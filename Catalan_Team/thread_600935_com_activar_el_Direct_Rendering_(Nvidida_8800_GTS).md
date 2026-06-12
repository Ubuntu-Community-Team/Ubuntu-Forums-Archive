---
title: "com activar el Direct Rendering (Nvidida 8800 GTS)?"
date: 2007-11-02
forum: Catalan Team
---

### Post by Roig on 2007-11-02
Hola

Quan faig:

glxinfo | grep rendering

em retorna:

dani@dani-habitacio:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

Que haig de fer per activar el direct rendering? A veure he instal.lat els drivers restringits sense problemes, amb l'aplicació que ve per defecte a l'ubuntu i els he activat també des d'allà. 

El compiz em funciona perfectament també, vull dir que no entenc perque em posa que no. Això si quan he provat de jugar al Unreal Tournament 2004, algunes textures se'm veuen de color negre, va rapid i tal pero les textures fallen, suposo que té a veure amb això. Vull saber que puc fer per arreglar-ho abans de posar-me amb el Wine+World of warcraft alguna idea? 

Gràcies!

---

### Post by papapep on 2007-11-02
Si vols que et funcioni l'XGL no podràs tenir DRI, no són compatibles.

---

### Post by patrickfromspain on 2007-11-03
Con et diu en papapep, si tens XGL no et funcionara el DRI. De totes formes, amb la teva tarja y els drivers d'nvidia NO necessites XGL, aixi que mira que no tinguis el paquet xserver-xgl insta&#322;lat.

---

### Post by jerec on 2007-11-03
No se quina versio fas servir, pero jo al actualitzar a Gutsy vaig tenir molts i molts de problemes per activar el "Direct Rendering" del driver de la nvidia.

Com ho vaig solucionar:

(com a root)
1º Ens carregem sense miraments les X
# apt-get remove --purge xserver-xorg

2º Em carregem per si cas el kdm (o el gdm depen del que facis servir)
# apt-get remove --purge kdm o # apt-get remove --purge gdm

3º Edita el xorg.conf i posa el driver "vesa"
# joe /etc/X11/xorg.conf
i la secció "Device"
canvia el driver "nvidia" per "vesa"

4º Reinstala les X i el kdm
# apt-get install xserver-xorg
# apt-get install kdm o # apt-get install gdm

5º Amb l'aplicacio "envy" desinstal·la el driver de "nvidia" i reinicia les X (o la maquina si vols), no has de tenir cap problema per tornar a entrar a les X, ja que encara tens posat el driver "vesa"
Per el envy_0.9.8-0ubuntu10_all.deb passa per la pagina del autor:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

6º Amb el mateix "envy" instala de nou el driver "nvidia", la mateixa aplicacio et demanara per modificar el xorg.conf i et canviara el driver "vesa" per "nvidia", reinicies les X i la maquina per comprovar que s'et carregen be tots els moduls.

7º Comproves que tens els moduls carregats i et funciona l'acceleracio 3D
# lsmod | grep nvidia
nvidia               6221776  36 
agpgart                35016  1 nvidia
i2c_core               26112  4 stv0299,nvidia,b2c2_flexcop,dvb_pll

# glxinfo | grep direct
direct rendering: Yes

I ja tens les X anant a 3D a tota castanya
# glxgears             
4504 frames in 5.0 seconds = 900.754 FPS
4447 frames in 5.0 seconds = 889.340 FPS
4508 frames in 5.0 seconds = 901.274 FPS

---

### Post by patrickfromspain on 2007-11-03
caram quanta cosa que no calia fer! T'agrada treballar i patir eh? ;)

---

### Post by jerec on 2007-11-03
Si home!!.
A tu et sembla que no m'ho vaig mirar tot i no vaig llegir 40mil pagines a veure que podia esser?¿.

Abans vaig provar el driver del Ubuntu, el de nvidia instalant-lo a ma, desde el Gnome amb el hadware propietari d'activar-lo, carregant el modul a ma, etc etc,
Em sortia el logo de nvidia, el driver funcionava, les X anaven impecables i el Xorg.0.log estava net com una patena d'errors.
Pero no tenia acceleracio 3D.

L'unica manera va esser reinstalant les X
10 minuts es feina?¿

Ahh, m'en descuidava, comprovar el xserver-xgl es el primer que em vaig mirar.

---

