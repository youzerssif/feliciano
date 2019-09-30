# feliciano
exo de groupe 3
ce projet a 4 applications

## blog
  ```
  from django.db import models

# Create your models here.
class Article(models.Model):
    """Model definition for Article."""
    titre = models.CharField(max_length=255)
    image = models.ImageField(upload_to='post')
    contenu = HTMLField('Content')
    icon = models.CharField(max_length=255)
    auteur = models.CharField(max_length=255)
    article_populaire = models.BooleanField()
    statut = models.BooleanField(default = True)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)
   

    class Meta:
        """Meta definition for Article."""

        verbose_name = 'Article'
        verbose_name_plural = 'Articles'

    def __str__(self):
        """Unicode representation of Article."""
        return self.titre

class Commentaire(models.Model):
    """Model definition for Commentaire."""

    description = models.TextField()
    article_id = models.ForeingKey('Article', on_delete=models.CASCADE, related_name='article_comment')
    statut = models.BooleanField(default = True)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Commentaire."""

        verbose_name = 'Commentaire'
        verbose_name_plural = 'Commentaires'



  ```
## resto
  ```
  from django.db import models

# Create your models here.
class Category_plat(models.Model):
    """Model definition for Category_plat."""

    nom = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Category_plat."""

        verbose_name = 'Category_plat'
        verbose_name_plural = 'Category_plats'

    def __str__(self):
        """Unicode representation of Category_plat."""
        return self.nom


class Plat(models.Model):
    """Model definition for Plat."""

    ingredients = models.CharField(max_length=255)
    nom = models.CharField(max_length=50)
    prix = models.IntegerField()
    image = models.ImageField(upload_to='post')
    category_id = models.ForeignKey('Category_plat', on_delete=models.CASCADE, related_name='cat_plat')
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Plat."""

        verbose_name = 'Plat'
        verbose_name_plural = 'Plats'

    def __str__(self):
        """Unicode representation of Plat."""
        return self.nom

class Service(models.Model):
    """Model definition for Service."""

    logo = models.CharField(max_length=255)
    titre = models.CharField(max_length=255)
    description = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)


    class Meta:
        """Meta definition for Service."""

        verbose_name = 'Service'
        verbose_name_plural = 'Services'

    def __str__(self):
        """Unicode representation of Service."""
        return self.titre

class Chef(models.Model):
    """Model definition for Chef."""

    nom = models.CharField(max_length=255)
    fonction = models.CharField(max_length=255)
    image = models.ImageField(upload_to='post')
    facebook = models.URLField(max_length=200)
    google = models.URLField(max_length=200)
    twitter = models.URLField(max_length=200)
    instagram = models.URLField(max_length=200)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Chef."""

        verbose_name = 'Chef'
        verbose_name_plural = 'Chefs'

    def __str__(self):
        """Unicode representation of Chef."""
        return self.nom

class Temoignage(models.Model):
    """Model definition for Temoignage."""

    auteur = models.CharField(max_length=255)
    image = models.ImageField(upload_to='post')
    logo = models.CharField(max_length=255)
    citation = models.CharField(max_length=255)
    fonction = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)


    class Meta:
        """Meta definition for Temoignage."""

        verbose_name = 'Temoignage'
        verbose_name_plural = 'Temoignages'

    def __str__(self):
        """Unicode representation of Temoignage."""
        return self.auteur

class Reservation(models.Model):
    """Model definition for Reservation."""

    nom = models.CharField(max_length=255)
    email = models.EmailField(max_length=254)
    numero = models.CharField(max_length=255)
    heure_reserv = models.TimeField(auto_now=True, auto_now_add=True)
    date_reserv = models.DateField(auto_now=True, auto_now_add=True)
    nbr_personne = models.IntegerField()
    livraison = models.BooleanField(default=True)
    emporter = models.BooleanField(default=True)
    mode_paiement = models.CharField(max_length=255)
    panier_id = models.ForeignKey('Panier', on_delete=models.CASCADE, related_name='panier_reserv')
    nom_resto = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)




    class Meta:
        """Meta definition for Reservation."""

        verbose_name = 'Reservation'
        verbose_name_plural = 'Reservations'

    def __str__(self):
        """Unicode representation of Reservation."""
        return self.nom

class Newsletter(models.Model):
    """Model definition for Newsletter."""

    email = models.EmailField(max_length=254)
    titre = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Newsletter."""

        verbose_name = 'Newsletter'
        verbose_name_plural = 'Newsletters'

    def __str__(self):
        """Unicode representation of Newsletter."""
        return self.titre


class Programme(models.Model):
    """Model definition for Programme."""

    jours = models.CharField(max_length=255)
    heure = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Programme."""

        verbose_name = 'Programme'
        verbose_name_plural = 'Programmes'

    def __str__(self):
        """Unicode representation of Programme."""
        return self.jours

class Resto(models.Model):
    """Model definition for Resto."""

    nom = models.CharField(max_length=255)
    description = models.TextField()
    small_text = models.CharField(max_length=255)
    numero = models.IntegerField()
    annee_experience = models.IntegerField()
    nbr_menu = models.IntegerField()
    staff = models.IntegerField()
    client_satisfait = models.IntegerField()
    licence_resto = models.CharField(max_length=255)
    message_footer = models.CharField(max_length=255)
    email = models.EmailField(max_length=254)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)



    class Meta:
        """Meta definition for Resto."""

        verbose_name = 'Resto'
        verbose_name_plural = 'Restos'

    def __str__(self):
        """Unicode representation of Resto."""
        return self.nom

class ImageResto(models.Model):
    """Model definition for ImageResto."""

    image_accueil_un = models.ImageField(upload_to='post')
    image_accueil_deux = models.ImageField(upload_to='post')
    image_about_un = models.ImageField(upload_to='post')
    image_about_deux = models.ImageField(upload_to='post')
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for ImageResto."""

        verbose_name = 'ImageResto'
        verbose_name_plural = 'ImageRestos'

class ContactInfo(models.Model):
    """Model definition for ContactInfo."""

    titre = models.CharField(max_length=255)
    email = models.EmailField(max_length=254)
    adresse = models.CharField(max_length=255)
    numero = models.CharField(max_length=50)
    site_web = models.CharField(max_length=255)
    statut = models.BooleanField(default = False)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for ContactInfo."""

        verbose_name = 'ContactInfo'
        verbose_name_plural = 'ContactInfos'

    def __str__(self):
        """Unicode representation of ContactInfo."""
        return self.titre

class Panier(models.Model):
    """Model definition for Panier."""

    item_id = models.ForeignKey('Items_panier', on_delete=models.CASCADE, related_name='items_panier')

    class Meta:
        """Meta definition for Panier."""

        verbose_name = 'Panier'
        verbose_name_plural = 'Paniers'

class Items_panier(models.Model):
    """Model definition for Items_panier."""

    plat_id = models.ForeignKey('Plat', on_delete=models.CASCADE, related_name='plat_item')
    quantite = models.IntegerField()
    prix_unitaire = models.IntegerField()
    prix_total = models.IntegerField()

    class Meta:
        """Meta definition for Items_panier."""

        verbose_name = 'Items_panier'
        verbose_name_plural = 'Items_paniers'




  ```
## contact
  ```
  from django.db import models

# Create your models here.
class Contact(models.Model):
    """Model definition for Contact."""

    nom = models.CharField(max_length=255)
    email = models.EmailField(max_length=254)
    subject = models.CharField(max_length=255)
    message = models.CharField(max_length=255)
    statut = models.BooleanField(default = True)
    date_add = models.DateTimeField(auto_now_add= True)
    date_update = models.DateTimeField(auto_now= True)

    class Meta:
        """Meta definition for Contact."""

        verbose_name = 'Contact'
        verbose_name_plural = 'Contacts'

    def __str__(self):
        """Unicode representation of Contact."""
        return self.nom


  ```
## config
  
