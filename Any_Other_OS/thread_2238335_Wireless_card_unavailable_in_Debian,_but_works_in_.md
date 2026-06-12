---
title: "Wireless card unavailable in Debian, but works in Ubuntu"
date: 2014-08-07
forum: Any Other OS
---

### Post by S4mmael on 2014-08-07
Hello guys,

I have a liittle problem with a wireless card of a cheap HP laptop. It  works perfectly well out of the box in Ubuntu 14.04, but not in Debian  Jessie.

Here is what I managed to find.


In Ubuntu it looks like that:

root@ubuntu:~# dmesg | grep 02:00.0
[    0.986323] pci 0000:02:00.0: [10ec:8179] type 00 class 0x028000
[    0.986347] pci 0000:02:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.986383] pci 0000:02:00.0: reg 0x18: [mem 0x90700000-0x90703fff 64bit]
[    0.986486] pci 0000:02:00.0: supports D1 D2
[    0.986490] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.986542] pci 0000:02:00.0: System wakeup disabled by ACPI

root@ubuntu:~# lspci -s 02:00.0 -v
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 197d
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 2000 [size=256]
    Memory at 90700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-e0-4c-ff-fe-81-91-01
    Capabilities: [150] Latency Tolerance Reporting
    Kernel driver in use: rtl8188ee


Whereas in Jessie it looks like that:

root@debian:~# dmesg | grep 02:00.0
[    1.109622] pci 0000:02:00.0: [eaea:eaea] type 6a class 0xeaeaea
[    1.109628] pci 0000:02:00.0: unknown header type 6a, ignoring device

root@debian:~# lspci -s 02:00.0 -v -H1
02:00.0 Class eaea: Device eaea:eaea (rev ea) (prog-if ea)
    !!! Unknown header type 6a

It's only available in the output of lspci with -H1 option.


I'm aware that header type 6a is incorrect, but is there any workaround  or something? How do I make the card work in Debian? How does Ubuntu do that? 

Thank you in advance for any help, it's greatly appreciated.

---

### Post by mastablasta on 2014-08-07
> Kernel driver in use: rtl8188ee

Ubutnu most likely ships with some drivers that Debian does not use as a result of distro opensource only policy. I am guessing here but most likely there is a backport to install the necessary drivers in debian.

or just use Ubuntu. :P

---

### Post by S4mmael on 2014-08-07
Thanks for quick reply.
I've installed rtl8188ee.ko in debian, I can even modprobe  it. Unfortunately, it's useless since kernel does not "know" there is a  wireless card in the system.

---

### Post by ajgreeny on 2014-08-07
Is the debian machine still cable attached?  many Linux OSs will not detect the wireless if there is an ethernet cable still attached; that is true of Ubuntu, I think.

---

### Post by S4mmael on 2014-08-07
> **ajgreeny said:**
> Is the debian machine still cable attached?  many Linux OSs will not detect the wireless if there is an ethernet cable still attached; that is true of Ubuntu, I think.

I've just gave it a try. No luck.

---

### Post by Yellow Pasque on 2014-08-07
Have you installed firmware-realtek package? What Debian kernel are you using?

---

### Post by S4mmael on 2014-08-08
> **Temüjin said:**
> Have you installed firmware-realtek package? What Debian kernel are you using? Yes, I have. As I sad rtl8188ee.ko is available and can be modprobed. 3.14-2

---

### Post by QIII on 2014-08-08
As this appears to be specific to Debian (not an official flavor of Ubuntu ;) ) the thread has been moved to ***Other Operating Systems and Projects***.

You have a few crack commandos helping you already, so they will be able to follow the redirect.  Hopefully you won't get lost.

Cheers.

---

### Post by S4mmael on 2014-08-12
Any ideas please?

---

### Post by Yellow Pasque on 2014-08-12
Does dmesg say anything after you modprobe the module?

---

### Post by S4mmael on 2014-08-13
No, nothing    >  root@debian: # modprobe rtl8188ee[br]a[/br] root@debian: # lspci | grep -i wireless[br]a[/br] root@debian: # iwconfig[br]a[/br] eth0 no wireless extensions.[br]a[/br] [br]a[/br] lo no wireless extensions.[br]a[/br] root@debian: # lspci -knn -s 02:00.0 -v[br]a[/br] root@debian: # lspci -knn -H1 -s 02:00.0 -v 02:00.0[br]a[/br] Class [eaea]: Device [eaea:eaea] (rev ea) (prog-if ea)[br]a[/br] !!! Unknown header type 6a[br]a[/br] root@debian: # dmesg | grep -i "rtl8188ee\|wlan"[br]a[/br] root@debian: #[br]a[/br] 

---

### Post by Focker7117 on 2014-08-19
Im having the same issue .. 

uname -a 
Linux Red-Wolf 3.14-2-amd64 #1 SMP Debian 3.14.15-2 (2014-08-09) x86_64 GNU/Linux
Card = RTL8188EE

lspci:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)

dmseg:
[   10.087075] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   10.087142] rtl8188ee 0000:02:00.0: firmware: failed to load rtlwifi/rtl8188efw.bin (-2)
[   10.087246] rtl8188ee 0000:02:00.0: Direct firmware load failed with error -2
[   10.087250] rtl8188ee 0000:02:00.0: Falling back to user helper

Does anone have the repro that can be added that Ubuntu uses to pull the driver they use?

---

