---
title: "M'hecarregat el metacity, o algo per l'estil"
date: 2010-03-21
forum: Catalan Team
---

### Post by tanreb20 on 2010-03-21
Hola amics!

L'altre dia estava reordenant el Menú d'aplicacions, i en aquestes que vaig veure en un dels apartats molts enllaços a programes, que no es mostraven. Vaig decidir esborrar-los directament(els enllaços).

Ara resulta que em sembla que he trencat el metacity, o algun paquet semblant, ja que per exemple, abans tenia 3 enllaços directes al panell superior a diferents carpetes, ara quan hi faig clic, em diu el que posa a la imatge inferior.

També quan engego el pc abans em carregava el compiz bé, ara he de anar al temrinal, posar: compiz --replace i tancar el terminal, per tenir bores a les finestres, i per poder fer anar el docky correctament.

[IMG]http://img696.imageshack.us/img696/8/screenshot001oq.png[/IMG]

---

### Post by wgarcia on 2010-03-25
Sembla com si t'haguessis carregat l'associació del Nautilus per obrir carpetes des d'enllaços com els que tens al plafó de dalt. 

Potser anar al "Gestor de paquets" Synaptic i marcar "ubuntu-desktop" i "GDM" per reinstal·lar t'ho arregli.

---

### Post by tanreb20 on 2010-03-25
Ho he provat, i no, segueix exactament =

---

### Post by wgarcia on 2010-03-25
Ves-te a una terminal i entra la següent comanda:

cat /home/alorma/.local/share/applications/mimeapps.list

A veure què et surt...

---

### Post by tanreb20 on 2010-03-25
[Added Associations]
application/x-extension-part=vlc.desktop;
application/x-extension-crx=google-chrome.desktop;
image/jpeg=eog.desktop;f-spot-view.desktop;gpicview.desktop;firefox.desktop;gimp.desktop;
video/x-msvideo=totem.desktop;vlc.desktop;
audio/x-ms-wma=totem.desktop;vlc.desktop;soundconverter.desktop;
application/rdf+xml=gedit.desktop;
audio/x-riff=userapp-vlc-A4LK6U.desktop;


Pel que veig, falta l'asociació dels llançadors.. em podrieu passar el válid?

---

### Post by wgarcia on 2010-03-26
inode/directory=nautilus-folder-handler.desktop;

Aquesta és la línia que està en /etc/gnome/default.list. En realitat n'hi ha una altra relacionada:
        x-directory/normal=nautilus-folder-handler.desktop
        inode/directory=nautilus-folder-handler.desktop

però afegint la línia de dalt t'ho hauria d'arreglar.

En realitat a ".local/share/applicacions/mimetypes.list" no hauria d'haver-hi cap entrada d'aquest tipus, el meu és:
application/x-extension-dta=userapp-xstata-5NZVSU.desktop;userapp-xstata-0AB1GU.
desktop;
video/x-theora+ogg=Kino.desktop;
image/x-eps=evince.desktop;gimp.desktop;
text/calendar=gedit.desktop;emacsclient-emacs22.desktop;emacs22-gtk.desktop;texm
acs.desktop;ooo-writer.desktop;userapp-evolution-LK3PPU.desktop;
application/pdf=evince.desktop;AdobeReader.desktop;gimp.desktop;xpdf.desktop;use
rapp-pdfedit-KHWTRU.desktop;
application/vnd.openxmlformats-officedocument.wordprocessingml.document=openoffi
ce.org-writer.desktop;file-roller.desktop;mount-archive.desktop;openoffice.org-s
tartcenter.desktop;
application/x-trash=userapp-emacs-Y7VRWU.desktop;
text/plain=gedit.desktop;openoffice.org-writer.desktop;emacsclient-emacs22.deskt
op;emacs22-gtk.desktop;texmacs.desktop;openoffice.org-calc.desktop;
text/x-tex=emacsclient-emacs22.desktop;

i les associacions de les carpetes amb nautilus funcionen perfectament, tot i que no hi és la línia de dalt. 

Sembla un error. Escrivint la línia de dalt com deia a .local/share/applications/mimeapps.list
t'ho arreglarà.

Una possibilitat d'arreglar-lo és també canviar el nom de  .local a .local.old (així si alguna cosa va malament no perdre'l), sortir de l'usuari i tornar a entrar (s'hauria de recrear ".local"). Suposo que això restaurà les associacions a les associacions per defecte, i  farà perdre altres associacions que tu hagis creat clicant amb el botó dret sobre arxius i usant "Obrir amb...", però si no has creat cap associació així potser sigui una solució més neta que afegir la línia que comento a dalt. 

Aquest problema està documentat al següent error:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

Comença amb versions antigues d'ubuntu, però si et fixes l'última entrada descriu exactament el mateix problema que vas tindre tu.

---

### Post by tanreb20 on 2010-03-26
Moltes grácies! Ha funcionat!!!!

---

