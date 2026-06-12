---
title: "no desa la resolució de pantalla"
date: 2009-05-26
forum: Catalan Team
---

### Post by bratac on 2009-05-26
Bones,

m'acabo d'instal·lar xubuntu i, per defecte em va amb resolució de 640x480. En entrar la canvio a 1024 x 768, faig clic a aplica i tot funciona perfectament però quan reinicio l'ordinador em torna a sortir a 640x480. 

Em podeu dir com ho he de fer per a que quedi desada la configuració?

gràcies!

---

### Post by LitusMayol on 2009-05-26
Ep,

jo tinc el mateix problema i de fet aquí al fòrum ja hi ha diversos fils que parlen d'això. De moment no hem conseguit solucionar-ho.

Jo et proposo una solució: crea un usuari nou. Proba si a aquell li va, si li va elimines l'altre i fora.

Espero que et funcioni!

---

### Post by bratac on 2009-05-28
Bones,

i no hi ha alguna manera de forçar a la X a agafar la resolució de pantalla que ens vagi bé per defecte?

He provat de reconfigurar xserver.conf però només em deixa configurar el teclat.

gràcies.

---

### Post by LitusMayol on 2009-05-28
> **bratac said:**
> Bones,

i no hi ha alguna manera de forçar a la X a agafar la resolució de pantalla que ens vagi bé per defecte?

He provat de reconfigurar xserver.conf però només em deixa configurar el teclat.

gràcies.

Jo també ho he provat, I res, ni manualment ni re de re... :( No ho sé!

---

### Post by kimet on 2009-05-28
Heu provat a a editar el xorg.conf a mà?

Si cas podeu enganxar el contingut de /etc/X11/xorg.conf a veure si algú os pot ajudar.

Salut.

---

### Post by CarlesOriol on 2009-05-30
A mi tampoc em va funcionar fa temps... però hi ha una opcio que et permet desar els canvis a un altre arxiu. Jo ho vaig fer aixi' i després vaig reescriure les linies del xorg a maneta comparant els canvis.

---

### Post by vinga on 2009-06-03
si tens nvidia i fas servir els controladors propietaris, executa des del terminal ```
$ nvidia-settings
``` i probablement et dirà quin problema tens.
a mi em diu:
```
grr@casa:~$ nvidia-settings 
ERROR: Invalid display device DFP-0 specified on line 47 of configuration file
       '/home/grr/.nvidia-settings-rc' (the currently enabled display devices
       are CRT-0 on casa:0.0).

grr@casa:~$ 

```

entenc que el dispositiu o device és invàlid, però no sé corregir-ho.
si algú em pot ajudar...

```
grr@casa:~$ more /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

grr@casa:~$ 
```

sal1t.

---

### Post by kimet on 2009-06-04
Hi ha molt poca cosa en aquest Xorg.conf, donant per suposat que el teclat i ratolí funcionen correctament, jo provaria: (fer copies de seguretat abans)



Afegir a ho hi diu Section "Screen"

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "Default Device"
    Monitor        "Default Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth         24
        Modes        "1680x1050" "1280x1024" "1024x768"
    EndSubSection
EndSection
```
pots afegir  la secció monitor:

```
Section "Monitor"
    Identifier    "Default Monitor"
    HorizSync    30-83
    VertRefresh    55-75
EndSection
```

Tenint en compte de posar la vostra resulució tan a "Modes" com a "HorizSinc/VertRefresh" 
I també que identificadors han de coincidir entre les diferents seccions. Aqui [http://buzon.en.eresmas.com/xorg.conf/xorgconf.html](http://buzon.en.eresmas.com/xorg.conf/xorgconf.html) es veu el que vull dir.

Siau.

---

