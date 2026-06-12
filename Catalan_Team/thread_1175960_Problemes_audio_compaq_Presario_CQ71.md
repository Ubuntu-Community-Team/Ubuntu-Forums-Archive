---
title: "Problemes audio compaq Presario CQ71"
date: 2009-06-01
forum: Catalan Team
---

### Post by pserra on 2009-06-01
Hola,
el portàtil en ubuntu ja de bones i primeres em va tot, unicament em queda la punyetera impresora Brother MFC-240c i el audio...
ANEM PER L'AUDIO:
No sento rés....

He estat mirant per fòrum respostes anteriors sobre mirar a Sistemes ->preferencies-> so i jo ho trobo tot activat... també  he trobat a 
diversos foros que ho  arreglan així:  a mi posant el gedit a davant 
em retorna un document en blanc amb el nom alsa-base...

#un altra cosa que he llegit per ahi es:
#edita l'arxiu /etc/modprobe.d/alsa-base
#i afegeix al final
#options snd-hda-intel model=3stack


**He vist que en algun fil volieu saber el harware:**
**lspci -vv**
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 306b
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step

He vist que en algun fil volieu saber la versió:
**uname -a**
Linux pere-portatil 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

ALGUNA SUGERÈNCIA?.. ES QUE PORTO ESTONES DONANT-LI VOLTES SENSE RESULTAT.... 
MERCI

---

### Post by pserra on 2009-06-11
Hola sembla que aquest fil s'ha quedat a l'oblit.... algú te alguna suggerencia??
què més puc mirar??
Merci

---

### Post by akyra on 2009-06-11
Pots posar que tens activar en les preferencies?
Un pantallazo d'aqueta pantalla aniria bé.

Tens posat el ALSA Mixer?
Quina versió d'unbuntu tens?

---

### Post by pserra on 2009-06-11
Aqui deixo la captura de pantalla del que em demanaves.... jo ho veig correcte.....
A VERUE SI HO PDEM SOLVENTAR...
Merci

---

### Post by akyra on 2009-06-12
Quan fas el "test" tampoc escoltes res?

Jo tinc seleccionat el PCM en el mesclador.

I les preferencies las has comprobat?

---

### Post by pserra on 2009-06-12
Merci akyra per ñla teva ràpida resposta,
no... quan faig els tests tampoc no escolto rés...he  canviat el PCM al mescaldor i tot va igual.... 
lo de preferències, a que et refereixes? jo ho trobo tot ok....
MERCI

---

### Post by quitus on 2009-06-12
Hi ha una aplicació per poder controlar millor l'àudio, s'anomena paman (pulseaudio manager) està en els repositoris.

Prova opcions diferents en les preferències de so, com ara alsa driver.

salut

---

### Post by PatrickVogeli on 2009-06-12
pots enganxar el resultat de fer cat /proc/asound/card0/codec#0 | grep Codec ?

---

### Post by pserra on 2009-06-12
Hola,
Merci  PatrickVogeli
aix+o es el que m'ha retornat sense la ? final....
adjunto pantalla finestra  de un programa que n'he instal·lat avui que es diu arranjament del sistema per si pot ser d'ajuda....
Hola quitus, he estat mirant el paman... però no he pogut sol·lucionar...
apart que la seva interfície no es massa clara...Merci de totes maneres


pere@pere-portatil:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: IDT 92HD75B2X5

---

### Post by pserra on 2009-06-12
m'ha fallat l'adjuncio...

---

### Post by PatrickVogeli on 2009-06-13
pots fer això?

cat /proc/asound/card*/codec* | grep Codec

---

### Post by pserra on 2009-06-13
Hola,
sembla que retorna el mateix que al missatge anterior...

pere@pere-portatil:~$ cat /proc/asound/card*/codec* | grep Codec
Codec: IDT 92HD75B2X5

---

### Post by PatrickVogeli on 2009-06-13
Doncs bé, tens feina: sembla que la solució esta en compilar i instal·lar ALSA 1.0.19..

Bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/)
Solució: [https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/63](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/63)

salut

---

### Post by akyra on 2009-06-15
pserra, has probat a posar en lloc de "detecta automaticament" el Pulse Audio.

En les preferencies em referia a una vegada seleccionat el PCM, des de l'icona que apareix en l'escriptori fer doble-click i allà mirar que no estigui el só molt baix, però suposo que això ja ho has fet.

---

### Post by pserra on 2009-06-16
Merci Akyra,
ahir abans de llegir el teu missatge, encara no se perquè, vaig tocar tema particions injustificadament i el sistema m'ha petat..
m'he quedat sense rés, quan engega s'em queda cercant el grup, error 22... ara no nse que fer....mirar per el google i si no m'aclaro aquesta nit escriure al fòrum....

MERCI  PER L'AJUDA...

---

### Post by pserra on 2009-06-27
Hola,
em sembla que el tema del problema d'audio he trobat el problema,he instal·lat el alsa versio 1.0.20 que deu ser la més recent,
la vaig instal·lar des de aquesta pàgina on esta molt ben explicat:
  [http://fausto23.wordpress.com/2009/](http://fausto23.wordpress.com/2009/)
i al compilar ja em va sortir un missatge que per defecte el alsa estava a mute... em sembla que ho he trobat però cliko a sobre el la icona del so de volume control i no trobo manera de deshabilitar-ho...
 alguna suggerència??
merci

---

