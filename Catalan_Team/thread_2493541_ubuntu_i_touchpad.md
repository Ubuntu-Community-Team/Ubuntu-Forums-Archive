---
title: "ubuntu i touchpad"
date: 2023-12-18
forum: Catalan Team
---

### Post by guillemtusell on 2023-12-18
Hola, espero saber-me explicar. 

Tinc un petit problema amb el Touchpad (Slimbook amb ubuntu 22.04LTS). M'han dit que és qüestió de software. Amb dos dits al touchpad puc moure les pàgines amunt i avall (scroll), i amb un dit moc el cursor. Bé, continuament se m'activa una funció que, amb un sol dit es mou la pàgina fent scroll (com si fossin dos dits) i no hi ha manera de moure el cursor fins que clico fort i es "desactiva" el que he dit (he de clicar fort, amb un copet al touchpad no es desactiva). He mirat la configuració, però no trobo res al respecte, tampoc a la web. Treballo bastant amb text i és desesperant.

S'agraeix algun consell. Gràcies.

---

### Post by wgarcia on 2023-12-19
Estás a l'escriptori per defecte (el Gnome)? Saps quin compositor gràfic estàs fent servir (Wayland que és el predeterminat ara, o X11 que és l'altra possibilitat)?

---

### Post by guillemtusell on 2023-12-19
Gnome 42.9 / Wayland.
Merci!

---

### Post by wgarcia on 2023-12-19
Has mirat si ho pots arreglar amb el "Gnome Tweaks", traduït com "Gnome Retocs"?

Ho pots instal·lar des del centre de programari, o a una terminal amb:

```

sudo apt install gnome-tweak-tool

```

Té un parell de opcions addicionals  per configurar el ratolí tàctil (touchpad). En particular, permet desactivar el toc al ratolí tàctic, a mi això em torna boig quan estic fent servir un editor o un processador de text.

---

### Post by guillemtusell on 2023-12-19
Sí, però només havia provat desactivar el botó central, per si creava una incompatibilitat. Ara provaré desactivar més coses. Gràcies

---

### Post by guillemtusell on 2023-12-19
Res, no és això. "Desactiva en escriure" no afecta, tampoc "inhabilitar emulació del clic". Ara bé: m'he adonat que aquesta "funció" s'activa en deixar reposar dos dits una estona sobre el touchpad, però no sempre (potser només si estan en un lloc específic) i es desactiva si faig un doble clic molt ràpid. Per tant, suposo que és qüestió de software, oi?
Alguna idea? Gràcies

---

### Post by wgarcia on 2023-12-20
Quan dius "qüestió de software" suposo que vols dis que no és un malfuncionament del dispositiu, oi? Jo crec que no ho és.

Per repassar totes les configuracions del Gnome sobre el ratolí tàctil, potser la sortida de

```
gsettings list-recursively | grep -i touchpad
```

pot ser útil. Tot i que és molt probable que si hi ha alguna cosa que està causant això, no sigui culpa del Gnome sinó d'alguna altra cosa.

---

### Post by guillemtusell on 2023-12-20
Hola,gràcies, veus alguna cosa estranya, aquí?:

org.gnome.desktop.peripherals.touchpad click-method 'none'
org.gnome.desktop.peripherals.touchpad disable-while-typing false
org.gnome.desktop.peripherals.touchpad edge-scrolling-enabled false
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad middle-click-emulation false
org.gnome.desktop.peripherals.touchpad natural-scroll true
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad speed 0.47058823529411775
org.gnome.desktop.peripherals.touchpad tap-and-drag true
org.gnome.desktop.peripherals.touchpad tap-and-drag-lock false
org.gnome.desktop.peripherals.touchpad tap-button-map 'default'
org.gnome.desktop.peripherals.touchpad tap-to-click true
org.gnome.desktop.peripherals.touchpad two-finger-scrolling-enabled true
org.gnome.settings-daemon.plugins.media-keys touchpad-off ['']
org.gnome.settings-daemon.plugins.media-keys touchpad-off-static ['XF86TouchpadOff']
org.gnome.settings-daemon.plugins.media-keys touchpad-on ['']
org.gnome.settings-daemon.plugins.media-keys touchpad-on-static ['XF86TouchpadOn']
org.gnome.settings-daemon.plugins.media-keys touchpad-toggle ['']
org.gnome.settings-daemon.plugins.media-keys touchpad-toggle-static ['XF86TouchpadToggle', '<Ctrl><Super>XF86TouchpadToggle']

(process:5390): GLib-GIO-WARNING **: 11:34:49.420: Failed to parse translated string '«[https://ca.wikipedia.org/wiki/Programari_de_propietat»](https://ca.wikipedia.org/wiki/Programari_de_propietat»)' for key 'nonfree-software-uri' in schema 'org.gnome.software': 0:expected value

(process:5390): GLib-GIO-WARNING **: 11:34:49.420: Using untranslated default instead.

---

### Post by wgarcia on 2023-12-20
La veritat que no. L'únic que se m'acut és habilitar "edge-scolling-enabled", cosa que no sé com es mostra als paràmetres o el gnome retocs. Això em sembla que fa que sols es pugui simular la rodeta de desplaçament a les vores del ratolí tàctic. Potser impedeixi que pugui saltar això de desplaçament amb un sol dit al mig del ratolí tàctic.

---

### Post by guillemtusell on 2023-12-20
Sí, això ha funcionat. La llàstima és que perdo el desplaçament amb dos dits, que m'havia acostumat, i pel lateral del pad, és més incòmode.
El que no entenc és que tinc un portàtil (antic) secundari amb la mateixa versió d'ubuntu, i això no em passa.
Bé, moltes gràcies per tot, encara que si se t'acut on pot estar l'arrel del problema per a tenir desplaçament amb dos dits sense que se m'activi aquest desplaçament amb un dit de tant en tant...
Bon Nadal ;)

---

### Post by wgarcia on 2023-12-21
Potser pel model de ratolí tàctil, no tots tenen el mateix suport als nuclis de Linux. 

Si vols marca com a "Solved", ho pots fer clicant sobre "Thread tools" a dalt.

---

