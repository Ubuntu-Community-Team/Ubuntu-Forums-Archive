---
title: "Configuracions de l'escriptori per defecte"
date: 2013-04-19
forum: Catalan Team
---

### Post by tsanchez on 2013-04-19
Bon dia a tothom.

Estic interesat en modificar les configuracions per defecte del gnome, perque cada vegada que es crei un usuari, aquest tingui un wallpaper predefinit, el render de finestres sigui un establert, modificació de la posició dels botons (minimitzar, maximitzar, tancar) etc etc.

Per ara he modificat amb els esquemas ubicats a /usr/share/glib-2.0/schemas i /usr/share/gconf/defaults.

El cas es que funciona per m'agradaria modificar només el gconf i no acabo de trobar a cap lloc quines claus he de tocar. Seguint alguna manuals trobats per internet modificant /desktop/gnome/backgorund/picture_filename "URL_IMATGE" tindria que funcionar pero no es aixi. 

Algú s'ho ha barallat amb això?

Gràcies per avançat.

TSL

---

### Post by wgarcia on 2013-04-19
Quin escriptori estàs fas servint?

---

### Post by tsanchez on 2013-04-19
Estic configurant que per defecte agafi el gnome-classic.

---

### Post by wgarcia on 2013-04-20
Han canviat tantes coses amb gnome que no sé si això seguirà funcionant, però ja el que vaig fer fa uns anys va ser crear un usuari, configurar-lo com vull que es creessin els nous usuaris, i copiar els directoris del home d'aquest usuari anomenats .gconf i .config a /etc/skel . Em sembla que tot el que poses a /etc/skel s'utilitza per als nous usuaris, per exemple si crees un directori Desktop i li poses fitxers ".desktop" tindràs els accessos que vulguis a l'escriptori, o si copies el fitxer Desktop a del teu usuari model. Buscant /etc/skel a Internet també surten altres opcions, entre les quals les que menciones. Clar que això em sembla sols soluciona els elements estètics com el fons de pantalla o els accessos a l'escriptori, no la resta que dius com posició de botons, etc.

---

### Post by tsanchez on 2013-04-24
Hola a tothom! 

Per "requisits del guió" (o mes ben dit per requisits del projecte) no era convenient tocar /etc/skel així que la solució al final passa per modificar els fitxers de configuració de gconf i glib. Ja ho tenim solucionat i si algú l'interessa podriem comentar com modificar-ho.


slts

tsanchez

---

### Post by wgarcia on 2013-04-24
Si no porta massa temps, sí que seria útil deixar aquí quatre línies de com ho heu fet, i marcar el fil com "solved".

---

### Post by tsanchez on 2013-04-26
Hola a tots!

Per tal de modificar l'aspecte per defecte del nostre entorn d'escriptori podem modificar els schemas de glib (o crear-ne algun de nou personalitat) o crear un fixter que modifiqui les claus del gconf.

Si triem modificar el glib, el fitxer l'hem de crear al directori /usr/share/glib-2.0/schemas

Noteu que ja existeixen fitxers del tipus nom_schema.override, així que si nosaltres creem algún de nou tindrem que posar-li un prefix númeric perque sigui l'últim en executar.

Despres nomes recompilem el glib utilitzant la sentencia de shell:

glib-update-schemas /usr/share/glib-2.0/schemas

Si modifiquem el gconf, el fitxer l'hem d'ubicar a /usr/share/gconf/defaults i perque es agafi aquesta configuració hem de fer desde la shell:

update-gconf-defaults 

Espero que li serveixi a algú :D

---

