---
title: "Ajuda amb els drivers, sóc nou a gnu/linux :)"
date: 2020-01-25
forum: Catalan Team
---

### Post by ramonet21 on 2020-01-25
Bona vesprada ):P, 
Em diuen Ramonet i fa un parell de setmanes que estric trastejant amb gnu/linux, concretament amb kubuntu, anteriorment havia emprat ubuntu però ara estic provant la versió amb kubuntu kde plasma. (kubuntu 18.04 si no m'equivoque, la darrera LTS)
M'agradaria que m'ajudareu, si és possible, amb el tema dels drivers que és un tema que em costa moltíssim de sol·lucionar.
Els drivers que necessite són els de la gràfica, els altaveus i els auriculars.

La gràfica que empre és AMD Radeon RX 580, i seguint  aquest enllaç [https://www.amd.com/es/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-580](https://www.amd.com/es/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-580), descarregue el paquet i tinc 2 opcions, instalar la versió normal o la versió pro (no comprenc la diferència).
Els passos que faig són els indicats:
```
tar -xJvf amdgpu-pro _ *. tar.xz
cd amdgpu-pro-XX.XX (subsituint les X pel meu cas concret)
sudo apt update
./amdgpu-pro-install -y  (tinc 2 opcions, amdgpu -install o amdgpu-pro install)
```

Tot bé fins que a la darrera línia de la instal·lació em diu error amb el kernel actual no compatible ( mateix error amb la versió normal i la pro)
Línia d'error: 
```
WARNING:amdgpu dkms failed for running kernel
```

KERNEL ACTUAL: $ uname -r     -->    5.3.0-26-generic

El mateix exemple que em passa a mi li passa a aquest portuguès [https://www.youtube.com/watch?v=9f_hh0mfBiA](https://www.youtube.com/watch?v=9f_hh0mfBiA) (minut 6:18 podeu veure l'error). 
La cosa és que si que sembla que s'ha instal·lat (la versió normal, no la pro)

```
XXXX@XXXX:~$ glxinfo |grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Radeon RX 580 Series (POLARIS10, DRM 3.33.0, 5.3.0-26-generic, LLVM 9.0.1)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 19.2.2
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5 (Compatibility Profile) Mesa 19.2.2
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 19.2.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```


M'agradaria saber si el driver està ben instal·lat. Emprant el programa gputest, que llença un video i analitza els fps, el resultat és el següent:

```
GpuTest 0.7.0
Module: TessaMark x32      (no entenc molt bé lo de 32 imagine que el meu sistema serà de 64 bit, no se massa del tema)
FPS 727
Settings: 1920x1080
Renderer Radeon RX 580 Series
OpenGL 4.5 (core profile) Mesa 19.2
```

D'aquesta informació entenc que la gràfica funciona, no entenc el WARNING d'abans anunciant incompatibilitat amb el kernel.

M'agradaria saber si està tot correcte o si hauria de probar de configurar les coses de forma diferent. També m'agradaria saber si tenint en compte la meua gràfica em convé la versió normal o la pro (amb les dues apareixia el warning )

Això en quant a la gràfica.

Tincs uns altaveus logitech que no me'ls deteca, s'anomenen altaveus logitech Z213.

A l'apartat de dispositius de reproducció apareixen 2:
```
OUTPUTS
- linia de sortida : àudio intern estereo analogic (DEFAULT)
- linia de sortida: hdmi/display port 3: ellesmere (radeon rx580) digital stereo (hdmi 3)

INPUTS
Audio internet estereo analògic
```


I els meus auriculars s'anomenen Logitech G430 Gaming SOrround SOund 7.1, tampoc he aconseguit instal·lar els gràfics.

He fet molta recerca, i després de no haver aconseguit res (crec, doncs no se si la gràfica està bé) he acoduit al fòrum en busca d'ajuda de gent entesa. 
Moltes gràcies per la vostra atenció,
Salut.:D

---

### Post by ffp on 2020-01-27
Bon dia,
Pot ser que no sigui massa bo per ajudar-te, però el meu consell es que essent nouvingut a linux, no instal·lis drivers de fora de l'entorn linux, solen tenir molts problemes i el mes probable es que NO els tinguis instal·lats i segueixes utilitzant els drivers genèrics, però amb la configuració emmerdada. Això no es com el windows.
El millor sistema per instal·lar els drivers propietaris, es anant a "programari i actualitzacions" pestanya "Controladors addicionals" i esperar a que el sistema analitzi el teu hardware i proposi un driver privatiu "provat", sol funcionar correctament.
Jo no faig servir mai radeon, nvidia està millor suportat, crec jo. Ànims, aprendre sempre es divertit.

---

