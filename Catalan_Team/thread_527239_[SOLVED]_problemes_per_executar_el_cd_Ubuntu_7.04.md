---
title: "[SOLVED] problemes per executar el cd Ubuntu 7.04"
date: 2007-08-16
forum: Catalan Team
---

### Post by carlesbm on 2007-08-16
Hola

Us exposo el meu problema amb la distribucio de Ubuntu he intentat de executar el cd amb el meu ordinador però, es queda com penjat i tot seguit comença apareixer un seguit de errors, que us descric tot seguit:
-Placa base  ASUS mod. P5LD2 SE 
-Equipat amb 2Gb de RAM un HD 250 Gb SATA  un HD 120 IDE targeta gràfica ATI SAPHIRE 512 MB
-No disposo de Disketera de 3" 1/5

-Errors:
    [183.083215]ata1.00:failed to set xfermado (err-mask=0x40)
                          ata1.01:failed to set xfermado (err-mask=0x40)
 ..........

    [184.210097]bufer I/O error on device fd0,logical Block0

i així seguix fins apareixer el següent missatge:

BUSYBOX V1,13 (debian 1:1.1.3-eubuntu3) built m shell (ask)

Enter "help" for aust of built in commands

/bin/sm, can´t access TT4: doB control turned OFF

(initramfs)_

He probat el DVD en altres ordinadors mes antics i funciona perfectament. Saveu que pot passar?:(:(

---

### Post by papapep on 2007-08-16
Crec que abans de ficar-nos amb temes més complicats, potser seria bó que provessis a intentar instal·lar amb la versió alternate d'Ubuntu:

[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)

Molts cops només amb això ja s'aconsegueix instal·lar. 
Si no fos així, ja saps...torna a comentar-ho (i si funciona també, per saber-ho ;-))

---

### Post by carlesbm on 2007-08-16
Hola papapep

He intentat de fer la instal.lacio amb la versio alternate i sembla que h pogut fer algun pas més fins que m'ha sortit un missatge de que no podia  muntar la unitat de CDrom, i hem demanava que poses un disket amb els controladors, j no tinc disketera. He descarregat el firmware de la pagina oficial de LITEON i l'he actualitzat. Ha una altra cosa; avans de que comences amb la instal.lació ha aparegut els missatges següents:

usb 1-1:device not accepting address 2,error-71
irq21 : nobody card (try bootin with the "irgpoll" option
handlers:
Disabling IRQ#21
ata1.01:exception Emask 0x0 Sact 0x0 SErr 0x0 frozen
ata1.01 cmd a0/01:00: .........

No entenc que passa? Es posible que la grabdora de DVD no sigui compatible amb linux? Com ho puc solucionar demà probare de colocar el cdrom i intentarè de arrancar amb un cd LIVE aviam que passa; demà ja penjare els resultats.

Donar-vos les gracies per la vostra gran ajuda.

---

### Post by papapep on 2007-08-16
Doncs potser hauries de fer-li un cop d'ull a la bios a veure com té configurat el tema del floppy i demés.

Apart,

> irq21 : nobody card (try bootin with the "irgpoll" option

Aquí et diu que provis de passar-li al kernel, quan s'engega tot plegat, l'opció "irqpoll".
A vegades també funciona. Per provar, no hi perds res.

---

### Post by carlesbm on 2007-08-17
Hola:

    He revisat la Bios i no he vist res que pugui resultar estrany, en l'apartat del Floppy disk hi ha la opcio 1,44 MB.

   Com es pot entrar aquesta opció de "irqpoll" al Kernel? , cal dir que els meus coneixements de linux son molt escasos, unicament he utilitzat lleugerament el propi ubuntu 6.10 (en un altre PC) pero pel que fa a introduir ordres, no tinc la sificient experiencia.

:(:(

---

### Post by papapep on 2007-08-17
Doncs quan s'inicia el sistema i et surten les línies del grub, fica el cursor (amb les fletxes) damunt la primera línia i prem la tecla "e" per editar-la. Després ves fins la línia que comença per "kernel" i torna a prèmer la tecla "e". Ves fins el final de la línia i allà fica l'opció "irqpoll".

A veure què tal et va.

---

### Post by carlesbm on 2007-08-17
Holaaaa.

     Per fi ja puc disfrutar del meu sistema Linux Ubuntu, Moltisimes gracies a papapep per els seus savis i de una molt gran utilitat, gracies als quals he aconseguit que el meu ordinador pugui executar, aquest sistema.

    En un proper post us detallaré tot lo millor que pugui el problema i la seva solució, per tal de poder ajudar algun altre usuari amb un problema semblant.


    Moltes gracies i espero poder aportar alguna ajuda, tot i la meva poca experiència.
\\:D/\\:D/

---

