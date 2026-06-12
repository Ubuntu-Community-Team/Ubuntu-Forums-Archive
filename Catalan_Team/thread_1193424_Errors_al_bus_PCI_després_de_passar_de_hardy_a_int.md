---
title: "Errors al bus PCI després de passar de hardy a intrepid"
date: 2009-06-21
forum: Catalan Team
---

### Post by lpargemi on 2009-06-21
Hola

Acabo de passar de Hary a Intrepid, i m'he trobat amb un problema. Amb hardy tot anava bé, i ara en canvi cada vegada que arrenco se'm munta una llista, a vegades és inacabable, amb l'error següent. (Extret del logger)

```

Jun 21 19:26:09 lluis kernel: [   33.836865] +------ PCI-Express Device Error ------+
Jun 21 19:26:09 lluis kernel: [   33.836870] Error Severity^I^I: Uncorrected (Non-Fatal)
Jun 21 19:26:09 lluis kernel: [   33.836872] PCIE Bus Error type^I: Transaction Layer
Jun 21 19:26:09 lluis kernel: [   33.836874] Flow Control Protocol ^I: Multiple
Jun 21 19:26:09 lluis kernel: [   33.836876] Receiver ID^I^I: 0010
Jun 21 19:26:09 lluis kernel: [   33.836878] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
Jun 21 19:26:09 lluis kernel: [   33.836882] pcieport-driver 0000:00:02.0: broadcast error_detected message
Jun 21 19:26:09 lluis kernel: [   33.836885] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
Jun 21 19:26:09 lluis kernel: [   33.836888] pcieport-driver 0000:00:02.0: broadcast resume message
Jun 21 19:26:09 lluis kernel: [   33.836896] pcieport-driver 0000:00:02.0: AER driver successfully recovered

```

A vegades tarda quatre  cinc minuts a engegar traient pel monitor aquest missatge intercalat amb altre sfucions que van bé, i a vegades arrenca depressa.

Us enganxo el què hi ha al bus PCI

```

lluis@lluis:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
04:04.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


```

El buss 00 Device 02 és la gràfica nVidia?

Faig servir el controlador NVIDIA accelerated graphic 173, després de provar amb el 180 i tampoc va.

La versió que tinc instal.lada és: 

```
lluis@lluis:~$ uname -a
Linux lluis 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux

```

En fi, algú sap què pot estar passant, o si stic pensant el video i és qualsevola altra cosa?

Agraït

Lluís

---

### Post by papapep on 2009-06-21
Prova què fa afegint-li el paràmetre

```
pci=nommconf
```

a la línia d'arrencada del menu.lst al kernel que fas servir.

---

### Post by lpargemi on 2009-06-22
Hola

Quan dius:

> **papapep said:**
> Prova què fa afegint-li el paràmetre

```
pci=nommconf
```

a la línia d'arrencada del menu.lst al kernel que fas servir.

vols dir fer això al fitxer menu.lst del directori /boot/grub ?


```
title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c036(...)aa5c0 ro quiet splash locale=ca_ES  pci=nommconf
initrd		/boot/initrd.img-2.6.27-14-generic
```

Així funciona sense sortir els errors aquests al logger.

Agraït

Lluís

---

### Post by lpargemi on 2009-06-24
Hola.

Després d'uns dies de prova puc confirmar que la solució que proposa en Papapep funciona. Molt agraït.

Ara bé: em podríeu fer cinc cèntims de què es suposa que li he manat? Que no envii al logger els avisos del PCI? 

Salut

Lluís

---

