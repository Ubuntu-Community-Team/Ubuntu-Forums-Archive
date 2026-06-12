---
title: "Crear shortcuts a l'escriptori a programes instal·lats manualment"
date: 2012-06-15
forum: Catalan Team
---

### Post by Jautenim on 2012-06-15
Hello world,

ja fa uns dies que m'he forçat a actualitzar de 10.04 a 12.04 per no quedar-me anclat en el temps, però aquest maleït Unity està plagat de detallets que em foten dels nervis ](*,)

L'últim que em porta de cap: m'he baixat manualment un programa (un build del navegador web Chromium) i l'he deixat a /usr/local. Fins aquí bé. Amb Ubuntu 10.04 i anteriors versions en aquest punt feia click dret sobre l'escriptori i al menú que apareix seleccionava "Create Launcher" i allà podia posar la ruta a l'executable, el nom i fins i tot la icona que volgués.

[IMG]http://cdn.shuffleos.com/wp-content/uploads/2011/10/create_launcher.jpg[/IMG]


Ara en canvi de l'única manera que he aconseguit crear shortcuts a l'escriptori ha estat buscant les aplicacions amb el buscador del Dash (ni tan sols es poden portar des de la barra lateral :mad:) i arrosegar-les a l'escriptori.

El problema es que si es tracta d'una aplicació instalada manualment sense fer servir l'apt-get o el software center no es pot trobar amb el Dash (o no sé fer que la trobi, es veu que escriure una ruta com ara "/usr/local/chrome-linux/chrome" no ho entén ](*,)](*,)](*,)](*,)).



Algú em podria orientar una mica sobre com crear aquest shortcut i sobre com treballar amb el Dash en general abans que em torni completament boig? \\:D/


(Per cert el mètode que surt a la foto d'instalar el gnome-panel i cridar aquesta comanda tan lletja ja l'he provat i a l'hora de la veritat no em crea el shortcut, desesperació++)

---

### Post by wgarcia on 2012-06-18
Em sembla que per crear una drecera a l'escriptori com demanes, un procediment que es pot utilitzar és obrir el "Dash", arrosegar qualsevol icona d'alguna aplicació a l'escriptori (per exemple la de firefox), desar-la a l'escriptori, clic amb el botó dret del ratolí -> propietats, i aquí canviar els paràmetres (ruta a l'aplicació, nom de la drecera, comentari, icona, permisos). No sé si hi ha d'altres procediments.

Per executar comandes personalitzades com la que dius em sembla que s'ha de fer "Alt-F2" i entrar el nom de la comanda, al "Dash" com tu dius sols apareixen les comandes instal·lades amb el sistema (el Centre de programari, la línia de comandes amb "sudo apt-get install" o el Synaptic).

---

### Post by akyra on 2012-06-20
Hola, aquí tens la solució de com crear els accesos directes.
Ja diràs si et va bé.

[http://ubuntu-cosillas.blogspot.com.es/2011/10/crear-lanzadores-de-escritorio-en.html]("http://ubuntu-cosillas.blogspot.com.es/2011/10/crear-lanzadores-de-escritorio-en.html")

Adeu

---

### Post by wgarcia on 2012-06-22
He trobat una manera senzilla de crear les dreceres a l'escriptori.

1) Obrir el "gedit"
2) Entrar les dues següents línies:

```
[Desktop Entry]
Type=Application

```

3) Desar el fitxer a l'escriptori amb el nom que vulgueu, per exemple "La meva aplicació.dektop", és important que acabi en .desktop

4) Fer clic amb el botó dret del ratolí sobre la icona a l'escriptori, un cop creat el fitxer

5) Omplir la informació del diàleg ("Descripció", "Ruta a l'aplicació", etc), entrant la ruta completa al nostre script o fitxer executable

6) Mireu a permisos que estigui marcat que es pot executar

Ja està...

---

