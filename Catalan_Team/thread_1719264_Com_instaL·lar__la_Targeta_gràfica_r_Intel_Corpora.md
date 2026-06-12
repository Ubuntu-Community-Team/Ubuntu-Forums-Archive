---
title: "Com instaL·lar  la Targeta gràfica r: Intel Corporation Mobile 4 Series C"
date: 2011-04-01
forum: Catalan Team
---

### Post by dariusill on 2011-04-01
HOla a tots,

Per a saber quina targeta gràfic tinc he fet això :

  	 	 	 	 	 	  spci | grep -i vga
 

 **La que tinc**:  
 

 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 

Com instal·lo el driver? 


Gràcies

---

### Post by kimet on 2011-04-01
Les driver de intel venen ja instalats amb el xorg, no has d'instalar-los. Si de cas revisa si tens instal.lat xserver-xorg-video-intel.
Si de cas, com ja t'he dit abans, configurar el fitxer /etc/X11/xorg.conf
especificant el driver "intel" a la secció device.
```
Section "Device"

Driver      "intel"
        
EndSection
```

Si no existeix el xorg.conf generar-ne un buscant instruccions a google p.ex.:

[http://ubuntu-guia.blogspot.com/2010/07/crear-xorgconf-ubuntu-1004.html](http://ubuntu-guia.blogspot.com/2010/07/crear-xorgconf-ubuntu-1004.html)

Per comprovar si tens acceleració era la comanda que t'he dit abans
glxinfo | grep direct ha de respondre "yes"

---

### Post by wgarcia on 2011-04-03
Com diu el kimet, aquesta targeta gràfica està suportada plenament sens cap mòdul extern o privatiu. I fins i tot diria que no necessita remenar els fitxers de configuració de l'Xorg.

Quins problemes tens amb la gràfica? En un fil anterior deies que no podies veure els vídeos a pantalla completa. Tots els vídeos o sols els de format Flash? Hi ha algun altre problema?

Altres suggeriments per anar descartant coses:

1) Si a la pantalla d'entrada al sistema (grub) tens altres nuclis de versions inferiors, provar amb aquests a veure si els problemes de vídeo també hi són.

2) A l'últim nucli, el que estàs usant, crear un altre usuari (Administració -> usuaris i grups), entrar amb aquest altre usuari i provar si els problemes es poden replicar.

---

### Post by dariusill on 2011-04-04
No puc veure els videos de flash en streaming. Les pelis que veig en el VCL els puc veure sense problemes.

---

### Post by dariusill on 2011-04-04
He creat un altre usuari i **no sé com entrar amb aquest altre usuari al sistema** per tal de comprovar si entrar d'aquesta manera em funciona l'acceleració gràfica i les eines de Compiz. 

Merci

---

### Post by wgarcia on 2011-04-05
Per entrar amb l'altre usuari simplement quan inicies el sistema t'hauria d'obrir una finestra on pots entrar el nom d'usuari i la clau, tant de l'usuari original com del nou que has creat.

---

### Post by kukat on 2011-04-05
Entra amb l'usuari normal, i fes un "Surt" enlloc d'un "Apaga" o un "Reinicia". 

Si poses "Surt" et sortirà la pàgina per a escollir l'usuari. 

;) 



També es pot fer d'una forma més violenta amb: 

**Alt Gr + PetSIS  + K**


Açò reinicia l'entorn gràfic i et porta a la pantalla d'escollir l'usuari. 


(El PetSis és la que hi ha també al "Impr pant". Al meu teclat al costat de F12)

---

### Post by dariusill on 2011-04-07
Aquest comendament el poso a la terminal ?

[B]Alt Gr + PetSIS  + K

[/B]O bé són tecles que he de pitjar alhora? Quina és la tecla PetSIS ? Quan li dono a ATURA, l'opció SURT no m'apareix...

---

### Post by kukat on 2011-04-07
> **kukat said:**
> 

(El PetSis és la que hi ha també al "Impr pant". Al meu teclat al costat de F12)

Si, son tecles que tens que pitjar al mateix temps, com el CTRL + ALT + SUPR
;)

---

### Post by dariusill on 2011-04-08
Merci KUKAT !!

hi ha oberts dos fils de conversa per al que ha resultat ( crec) ser el mateix problema. Per tant tancaré aquest. Gràcies per això de reiniciar l'equip amb un alter nom d'usuari.** Ja ho he fet i no ha canviat res respecte el problema de la targeta gràfica i els efectes. **

Salut!

---

