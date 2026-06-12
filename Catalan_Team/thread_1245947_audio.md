---
title: "audio"
date: 2009-08-21
forum: Catalan Team
---

### Post by neo_76 on 2009-08-21
no sé que em passa exactament, però no puc sentir la música. Sera problemes amb la tarja? com ppuc arreglar-ho??

---

### Post by SiscoGarcia on 2009-08-23
Sisplau, mira't [això]("http://ubuntuforums.org/showthread.php?t=599965") abans de continuar, sobretot els apartats 6, 7 i 8.

---

### Post by neo_76 on 2009-08-24
AMD 1800. 1Gb RAM. Crec recorda que la tarja és un NVIDI Geforce64.
SO:Kubuntu 8.10

Després d'instal·lar el Kubuntu 8.10 no s'escolta res pels altaveus. Com si no els reconegués. No sé donar més detalls.

---

### Post by guillemsola on 2009-08-25
crec que hauries d'aportar més informació al problema, prova a fer un **lspci** des d'una consola per veure la tarja/es que tens. Que no soni pot ser tan un problema del SO, dels altaveus, no has seleccionat la tarja adequada a Sistema->Preferències->So.

També hauries de provar de fer **alsamixer** per veure que els volums estiguin pujats.

A la web de alsa hi tenen un script que si l'executes a la teva màquina dona molta informació sobre l'estat del so al teu sistema.

[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

Genera un arxiu txt a /tmp que podries adjuntar.

---

### Post by neo_76 on 2009-08-27
neo@neo-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller(rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

### Post by guillemsola on 2009-08-27
OK, del lspci que adjuntes si t'hi fixes al sistema tens dues targes de so

Una creative i una integrada en placa.

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller(rev a0)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

Em mullo i dic que possiblement el teu sistema envia el so a una tarja diferent de la que tens els altaveus. Has provat connectar el so a la sortida de la integrada a l'ordinador? (o viceversa)

A Sistemes->preferencies->So tens on se suposa que va direccionat el so del sistema. Revisa que apunti a la sortida que tu vols.

salut!

---

### Post by quitus on 2009-08-27
Jo en un cas semblant només vaig poder aconseguir-ho desactivant una de les dues targes des de la bios.


salut

---

### Post by neo_76 on 2009-08-31
de conya! Tenia les targes invertides a "preferències".

---

