---
title: "El fan no funciona, s'escalfa la placa i es tanca."
date: 2010-05-21
forum: Catalan Team
---

### Post by JosepF on 2010-05-21
Fa dues setmanes vaig passar de la Xubuntu 8.04 a la Lubuntu 10.04 (m'agraden les LTS) amb una instal·lació neta. El meu ordinata es un Acer Aspire 5315, amb un 1Gb de RAM, Intel Celeron. 

El cas es que el processador es posa a unes temperatures extraordinàries per culpa de que no funciona el fan i el "seguro" del maquinari fa que es tanqui. Amb el 8.04 anava com la seda. He buscat per tot, [he provat de tot]("http://ubuntuforums.org/showthread.php?t=604158&page=12"), menys actualitzar la BIOS, hauria d'instal·lar el guindous i no vull. De moment puc anar tirant amb una sol·lucio "bruta": engego, login, escriptori, poso en suspens, el retorno i miraculosament el fan comença a funcionar. 

He instal·lat lm-sensors, però no aconsegueixo fer anar el pwmconfig, diu que no te sensors per a ell, cosa que no es veritat, el coretemp esta suportat.  He instal.lat l'scrip [aquest ]("http://royale.tiblog.fr/juin-2008/debian-gnu-linux-on-the-acer-aspire-5315.html")i tampoc. Algú te alguna idea?

---

### Post by PatrickVogeli on 2010-05-21
el fan? No vols pas dir el ventilador no?

el català correcte, passa'l..

---

### Post by JosepF on 2010-05-22
Puc fer dues coses, considerar-te un troll lingüístic,  vist que signes sota el teu avatar en anglès, o passar de tu i esperar que algú amb mes criteri pugui ajudar-me. Naturalment vaig per la segona. I si vols, ara pots corregit troll.

---

### Post by JosepF on 2010-06-06
Ja està. Ho he arreglat sense necessitat d'actualitzar la BIOS. En el fons era molt senzill i per culpa de no mirar be el que fas, he trigat una mica mes. 

sudo gedit /etc/default/grub
afegiu
GRUB_CMDLINE_LINUX="**acpi_enforce_resources=lax**"
guardeu
sudo 'update-grub' 
reinicia

I punt i final. Tot va com abans. Funcionen els fans i també els ventiladors :-)

---

