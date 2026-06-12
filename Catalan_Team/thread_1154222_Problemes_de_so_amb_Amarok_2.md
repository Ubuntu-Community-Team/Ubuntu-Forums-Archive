---
title: "Problemes de so amb Amarok 2"
date: 2009-05-09
forum: Catalan Team
---

### Post by mcako on 2009-05-09
Hola,
Avui he instal·lat l'Amarok 2 i veig que no em funciona l'audio, és estrany perque amb altres aplicacions com Rythmbox em reprodueix la música perfectament.
A l'iniciar Amarok em dóna el següent error per pantalla:
```
**Phonon: KDE's Multimedia Library**
The audio playback device **Nvidia CK8S with ALC850 (Nvidia CK8S)** does not work. Falling back to **default**.

```

Al executar amarok des de la consola em surt el següent:
```
llimac@Llimac:~$ amarok(5940) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(5940) Plasma::Applet::save: saving to "1"
amarok(5940) Context::ContextView::setContainment: "" Line:  599
amarok(5940) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(5940) Plasma::Applet::save: saving to "2"
amarok(5940) Plasma::Applet::save: saving to "3"
amarok(5940) Plasma::Applet::save: saving to "4"
amarok(5940) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(5940) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(5940) MagnatuneConfig::load: load
amarok(5940) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(5940) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(5940) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QDir::exists: Empty or null file name
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
amarok(5940) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
```

Per altra banda no sé perquè aquest Amarok que he instal·lat és diferent en quan a interfície gràfica del que vaig instal·lar a un altre pc on NO he actualitzat a la versio 9.04.

Segons l'about de l'amarok tinc la versió:
> Amarok
Version 2.0.2
Using KDE 4.2.2 (KDE 4.2.2)

He provat de canviar els paràmetres de so a Sistema > Preferencies > So canviant els dispositius de reproducció de so que tenia assignats com a "detecta automàticament" a "Servidor de PulseAudio", que fent el test d'audio és el que m'anava bé.

Alguna suggerència?
Gràcies!

---

### Post by orestesmas on 2009-05-09
L'Amarok és una aplicació de l'escriptori KDE. Tot i que es pot executar perfectament sobre Gnome (o qualsevol altre escriptori de Linux), cal configurar l'àudio amb les eines de KDE. No et serviran les eines de Gnome i per tant és normal que anant a Sistema > Preferències > So no notis cap efecte.

A veure si l'encerto. Amb el Synaptic prova d'instal·lar el paquet "phonon-backend-xine" i a desinstal·lar el "phonon-backend-gstreamer". Es soluciona el problema?

D'altra banda, és normal que vegis un Amarok diferent. El KDE s'ha renovat totalment no fa gaire, passant de la versió 3 a la 4. L'amarok que venia amb la intrepid correspon a una versió antiga, i la que tens tu ara (Amarok 2.0.2) ja és la nova. Al principi potser et costa una mica d'acostumar-t'hi, però poc a poc veuràs que incorpora moltes novetats i millores respecte la versió antiga. I els programadors n'estan afegint de noves constantment!

Vinga, a reveure.

---

### Post by mcako on 2009-05-10
Gràcies per l'ajuda, tot i així he vist que ja tinc instal·lat el phonon-backend-gstreamer. 
Per altra banda, he provat d'executar la comanda gstreamer-properties per canviar els connectors i els dispositius que tenia configurats a veure si es solucionava però em continua donant el mateix error.

Edit:
La meva targeta de so és la que venia onboard a la placa:
```
llimac@Llimac:~$ lspci | grep audio
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
```
No sé quina informació donar més.

---

### Post by mcako on 2009-05-10
**Gràcies Orestes! m'ho has solucionat!**
Havia llegit malament el teu post, pel que veig tu m'estaves dient el phonon-backend-xine i pensava que ja el tenia instal·lat, però no, el que tenia instal·lat era el phonon-backend-gstreamer..#-o
De totes maneres no l'he desintal·lat el de gstreamer, i sembla que tot funciona bé.
Gràcies!

---

### Post by orestesmas on 2009-05-11
Bé, doncs me n'alegro. M'apunto que no cal desinstal·lar el phonon-backend-gstreamer per tal que funcioni.

---

