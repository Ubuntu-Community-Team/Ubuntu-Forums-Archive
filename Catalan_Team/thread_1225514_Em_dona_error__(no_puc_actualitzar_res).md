---
title: "Em dona error  (no puc actualitzar res)"
date: 2009-07-28
forum: Catalan Team
---

### Post by kimms on 2009-07-28
Hola,

Miraré d'explicar-ho breument.
L'altra dia em volia actualitzar el firefox de la 3 a la 3.5.Em descarrego  el fitxer i el descomprimeixo, llavors l'afegeixo a la carpeta corresponent segueixo unes instruccions ( via cònsula) per actualitzar a la nova versió.(Ja ho vaig fer amb l'amule)..
Vet aquí que em va marxar la llum a mig escriure, ja us ho podeu imaginar...Conseqüències, no m'actualitza res ni amb el Synaptic ,ni amb el gestor.Em diu..
[FONT=Georgia][COLOR=Black]." s'ha produit un error irresoluble mentre s'iniaba la informació dels paquets
E:El tipus" * "no es conegut a la linea 56 de la llista de fonts/etc/apt/sources.list. 
E:No s'ha pogut llegir la llista de fonts"
[/COLOR][/FONT]
 No m'atreveixo a toca res...em podrieu dir si us plau que puc fer per deixar-ho correcte..

Gràcies

Kim

---

### Post by lluisanunez on 2009-07-28
D'entrada, jo miraria què hi ha a la línia 56 de la llista de fonts

```
gksudo gedit /etc/apt/sources.list
```

Si no ho saps arreglar a mà, entra al Synaptic > Configuració > Repositoris, marca els repos que hi hagi d'haver, desa, i torna-ho a provar

---

### Post by kimms on 2009-07-28
> **lluisanunez said:**
> D'entrada, jo miraria què hi ha a la línia 56 de la llista de fonts

```
gksudo gedit /etc/apt/sources.list
```Si no ho saps arreglar a mà, entra al Synaptic > Configuració > Repositoris, marca els repos que hi hagi d'haver, desa, i torna-ho a provar


Gràcies Lluisanunez, ja ho he solventat, com em dius he anat a la cònsola ,doncs no podia accedir a la configuració del Synaptic i a les" sources.list", he suprimit totes les linees a partir de la 56 (56-60), totes elles feien referència al firefox... i ja està !!

Gràcies pel teu temps:popcorn:

Kim

---

### Post by oriolsbd on 2009-07-29
Per cert, per instal·lar-te el Firefox 3.5 no necessites cap repositori especial. Està als repositoris "normals" d'Ubuntu (em sembla que a l'Universe). Pots instal·lar directament des de Synaptic el paquet "firefox-3.5". Per executar-lo, el tindràs al menú "Aplicacions>Internet>Shiretoko Web Browser".

Bé, això comptant que tinguis Jaunty.

Salut!

---

### Post by lluisanunez on 2009-07-29
Una pregunta, Oriol, el FF 3.5 s'insta&#320;la a part o matxaca al FF 3.1?

---

### Post by kimms on 2009-07-29
> **lluisanunez said:**
> Una pregunta, Oriol, el FF 3.5 s'insta&#320;la a part o matxaca al FF 3.1?
L'instala a part, com si fos un nou navegador però et clona el teu f.f 3.0 amb barres d'eines inclosa,perfectament.Menys un parell de complements( webmail,Dom inspector...) ,llàstima que l'idioma de moment és amb Anglès.

Salutacions.

---

### Post by oriolsbd on 2009-07-29
El paquet d'idioma en català per al Firefox 3.5 us el podeu baixar de Softcatalà:
[http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_per_al_Firefox](http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_per_al_Firefox)

Quant al tema del firefox-3.5, és com comenta en Kimms... més o menys. Em sembla que actualment els paquets firefox-3.1 i firefox-3.5 dels repositoris oficials d'Ubuntu són exactament el mateix. Si us fixeu pel Synaptic, en el firefox-3.1 indica que instal·la el firefox-3.5.

La cosa té sentit. El firefox 3.1 mai no va arribar a tenir una versió definitiva. Si no recordo malament, va arribar fins a la tercera versió Beta. Llavors, la gent de Mozilla va pensar que entre el Firefox 3.0 i el 3.1 hi havia moltes modificacions, però el canvi de numeració de 3.0 a 3.1 semblava que fos un canvi menor. I van decidir que canviar la numeració del Firefox 3.1 a Firefox 3.5. O sigui, que la quarta Beta del Firefox 3.1 ja es va dir Firefox 3.5 Beta 4.

O sigui, que Firefox 3.1 i Firefox 3.5 són el mateix, i pel que sembla pels comentaris del Synaptic que he indicat abans, si instal·les el Firefox 3.1 ja t'instal·la la versió definitiva del 3.5. Si des del Firefox 3.1 feu "Ajuda>Quant al Mozilla Firefox", quina versió us diu que teniu instal·lada?

Salut!

---

