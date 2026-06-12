---
title: "Firefox 3.0 no reprodueix sons en Ubuntu 9.04"
date: 2009-06-20
forum: Catalan Team
---

### Post by xangai on 2009-06-20
El Firefox es nega a "sonar". Qualsevol pàgina que tingui algún tipus de so, no el reprodueix. Siguin arxius de video (les imatges del qual si que es veuen) o arxius purament de so, per exemple les ràdios que emeten per internet. En Preferències de So dins de l'Ubuntu tinc seleccionat l'únic dispositiu que passa el "test" (en el meu cas Yamaha DS-1S (YMF744) YMFPCI (OSS)) que hi ha en les pròpies Preferències de So. La resta de dispositius no fan el "piiiiiiiip" quan polso el botó "test".

El Rhythmbox i el Totem reprodueixen perfectament el so. 

Alguna idea al respecte? 

Gràcies.

---

### Post by xangai on 2009-06-21
Continuo amb el tema. De fet no és únicament el Firefox qui no reprodueix el so. Tinc d'altres reproductors de vídeo o de música, que tampoc reprodueixen el so, exceptuant, és clar, el Rhythmbox i el Totem que sí que reprodueixen el so. Sembla com si aquests dos reproductors tinguessin "reservat" alguna llibreria, arxiu, driver . . ., necessàris per reproduir so i que no permetessin que cap altre programa els pogués utilitzar.

Misteris del software. Alguna idea al respecte?

---

### Post by marteljorge on 2009-06-21
Activa tots els repositoris a 'fonts de programari', actualitza la llista de paquets, actualitza els paquets i prova ambg Alsa.

---

### Post by xangai on 2009-06-22
Marteljorge:

No entenc ben bé per a que vols que actualitzi els paquets. Ja ho estàn. És que hi ha algún repositori en concret que tingui alguna actualització especial de l'Alsa? Jo el tinc actualitzat des de Canonical. Gràcies.

Vicenç.

---

### Post by PatrickVogeli on 2009-06-22
has provat aixo?

[http://ubuntuforums.org/showthread.php?t=1189563](http://ubuntuforums.org/showthread.php?t=1189563)

---

### Post by xangai on 2009-06-24
Gràcies PatrickVogeli, però del que parla en el "thread" que tu menciones no és exactament el meu problema.

Exceptuant el RhtythmBox i el Totem cap altre programa que pugui emetre so, no ho fa (inclós el Firefox) Si el programa emeteix vídeo, aquest es veu perfectament, però no emet so. 

Ho seguirem intentant. Gràcies.

---

### Post by xangai on 2009-06-24
¡¡¡ Solucionat !!!!

El problema estava en que jo tinc dues targetes de so. Una que està integrada a la placa base i una altra que vaig instal.lar jo. He anat a la BIOS i he desactivat (la he posada en "disabled") la que està integrada a la placa base. I ara ja reprodueix el so el Firefox i els altres reproductors de video i/o de so. Hem d'exceptuar l'Amarok que encara es resisteix a reproduir so. Però bé continuaré intentant-ho.

Gràcies no obstant als que m'heu ajudat.

---

### Post by oriolsbd on 2009-06-24
Hola, Xangai.

Prova el que diuen en aquesta anotació:
[http://epkis.com/joomla/programari/linux/140-amarok-2-a-ubuntu-jaunty.html](http://epkis.com/joomla/programari/linux/140-amarok-2-a-ubuntu-jaunty.html)

Salut!

---

