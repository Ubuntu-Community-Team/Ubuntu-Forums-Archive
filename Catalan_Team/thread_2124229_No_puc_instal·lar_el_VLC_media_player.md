---
title: "No puc instal·lar el VLC media player"
date: 2013-03-10
forum: Catalan Team
---

### Post by Joanmun on 2013-03-10
Hola,
Finalment he instal·lat l'Ubuntu 12.04 al disc dur, he instal·lat les actualitzacions i els "restricted extras", però quan intento instal·lar el reproductor VLC em dona aquest error:


    
[I]Package dependencies cannot be resolved 
[/I]
*This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.*
*Details:*
*The following packages have unmet dependencies: *
*vlc: Depends: vlc-nox (= 2.0.5-0ubuntu0.12.04.1) but 2.0.5-0ubuntu0.12.04.1 is to be installed *
*     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.5ubuntu0.12.04.1 is to be installed *
*     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.5ubuntu0.12.04.1 is to be installed *
*     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed *
*     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed *
*     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed *

*     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.4 is to be installed *
*     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.4 is to be installed *
*     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed *
*     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed *
*     Depends: libtar0 but it is not going to be installed *
*     Depends: libxcb-keysyms1 (>= 0.3.8) but it is not going to be installed *
*     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed *

  
Alguna idea del que  hauria de fer? he buscat pels fòrums i he intentat seguir les instruccions que donen a gent amb problemes similars, però segueixo sense poder instal·lar el VLC. Quan entro al terminal el què suggereixen aquí:  [http://askubuntu.com/questions/180635/vlc-package-dependencies-cannot-be-resolved](http://askubuntu.com/questions/180635/vlc-package-dependencies-cannot-be-resolved)   , no puc instal·lar les "dependencies" i em surt aquest text:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer0.10-ffmpeg' has no installation candidate[/I]


Gràcies per endavant.

Per cert, tampoc puc reproduir vídeos amb el "Movie Player" que ve amb l'Ubuntu 12.04, em dona l'error següent:

An error occurred
The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed.

---

### Post by ffp on 2013-03-10
Pot ser que no tinguis marcat els restricted i multiverse a Fonts de programari !
Em dona la sensació que no et permet instal·lar aquest tipus de paquets.

---

### Post by wgarcia on 2013-03-11
Tens algun paquet especial instal·lat, per exemple una PPA (això són paquets a part dels dipòsits de programari oficials d'Ubuntu, si no et sona el que és segurament no tindràs cap instal·lat)?

---

### Post by Joanmun on 2013-03-11
Gràcies per les respostes, al final he instal·lat de nou l'Ubuntu i ara em funciona tot.

---

