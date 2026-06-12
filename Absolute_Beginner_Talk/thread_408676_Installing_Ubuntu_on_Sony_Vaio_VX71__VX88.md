---
title: "Installing Ubuntu on Sony Vaio VX71 / VX88"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by dominykast on 2007-04-13
I decided to write this short install guide to everyone who would consider installing Ubuntu on Sony Vaio VX71 / VX88. It took me some 3 hours to come up with this.

Information about this machine (this is taken from [[COLOR="Blue"]here[/COLOR]]("http://www.waymouth.org/john/pcg-vx88/"))

850-MHz Intel Mobile Pentium III-M CPU
256MB SDRAM
30GB hard drive
14.1-inch XGA TFT display
Graphics chip: Intel 815EM chip
Audio: Intel 815 sound chip
Intel 10/100mbps ethernet
Orinico (lucent) MiniPCI Wireless w/128bit WEP
External DVD/CD-RW drive (PCGA-CRWD1) / i.link (ieee1394) CDRW/DVD combo drive
Memory stick slot
Modem
PS/2 Touch-pad with "jogdial"
PCMCIA: 1 type I or II 
2 USB ports

First thing, which you will notice is that regular Ubuntu CD image does not boot. This is because of fancy external CD-ROM whose drivers won't get loaded. Therefore, forget the CD install easy way and do network install easy way. 

First you will need MinimalCD image, which can be downloaded here - [[COLOR="RoyalBlue"]get MinimalCD image[/COLOR].]("https://help.ubuntu.com/community/Installation/MinimalCD") Other methods of installation can be found [[COLOR="RoyalBlue"]here[/COLOR]]("https://help.ubuntu.com/community/Installation/")

Now, download the image and burn it on to CD. Connect CD drive to your laptop, if necessary change boot settings in BIOS by pressing F2 when computer starts so computer could load CD image. Once computer is started from CD and menu appears just press enter (or enter necessary settings) and read further notifications, choose install location which is closest to you and enjoy. 

Both networks cards gets recognised so you can do network install using wireless or ethernet, whichever is more convenient to you.

Consider that you will need some 1h 30 min to finish the install. 
Ubuntu works just fine, so no need for Xubuntu unless you really want it. There will be a moment when you will think that system hang up (6% or so), do not worry system is downloading packages to install. Check router or network lights to be sure.

After the install everything works out of box, including CD-ROM. Enjoy. 

The above is dedicated to my dad as he was original owner of this laptop (with windows) and to my pregnant wife who will be the new owner (with ubuntu). Long live all. 

D

---

### Post by phr0ze on 2007-04-13
Very nice,

Thanks for sharing. Network install could be a solution for other systems as well.

---

### Post by pipehappy on 2007-05-09
Hi, 

I will install ubuntu on vx88. My version is 7.04. Do you have your fan under
/proc/acpi/fan. I don't have nothing in the directory. And CPU runs under
about 40C. Is it a common value? I am worried if CPU will get toasted.

---

