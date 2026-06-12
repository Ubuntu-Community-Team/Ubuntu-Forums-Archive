---
title: "D-Link DWL-510G Wireless Driver Install Problems"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by darth_vad3r on 2007-06-06
To start, My system is a little older than most (and a little more dumpster dived):

Dell Dimension 4100
Pentium 3 1ghz
192 MB ram
etc. etc.
Running Kubuntu 7.04

My problem is I'm trying to install a D-link DWL-510G Wireless Network Card.

I've found the windows drivers, and have downloaded ndiswrapper. My problem is when I attempt to use the command:

sudo ndiswrapper -i /location of file/filename.inf

it comes up with this:

couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete

The ndiswrapper -l command says that both the driver and the device are working, but after a sudo modprobe ndiswrapper, nothing comes up in iwconfig.

Any help would be greatly appreciated.

---

### Post by Seisen on 2007-06-07
where did you find the Windows Drivers at anyway? Here a link of a list of cards that work and the drivers they used.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/")

---

### Post by darth_vad3r on 2007-06-07
I got my drivers from the D-Link Website.

Those were the same ones that were linked to in the list you sent me; the link to the Asus website was dead.

I've also tried a few other things that didn't work:

Turning ACPI off didn't help things.
Installing the Windows 2000 drivers didn't work either.
Someone mentoned finding and removing a mrv8k.ko file in /lib/modules/<kernel>/kernel/drivers/net/wireless, but it wasn't there.

That's all I can remember that I did.

Thanks for any help. Again.

EDIT: This system has too many issues (lag with no programs open). I think due to the fact that it's a Dell, it doesn't like Kubuntu too much. Thanks for the help, but I'm just going to install win2k on it. I'm going to stay in the Ubuntu community though, as my laptop currently is dual-booting 7.04 and WinXP.

Thanks for all the help.

EDIT AGAIN: After installing Windows 2000 and having similar problems, it has been diagnosed as (probably) a PCI slot issue, at least in my case.

Seeing as I have Win2k set up, updated, and with all the appropriate drivers installed (at this point), I'm just going to stick with it. However, had I been able to diagnose the problem as that, I would have stayed with Kubuntu.

---

### Post by pherphenix on 2007-11-22
English (excuse my bad english)
I can do work the fuc... D-link 510G in ubuntu 7.04 AMD64bis, first download the driver at [http://www.publicstaticvoid.com/blog/d_link_dwl_g510_64_bit_drivers](http://www.publicstaticvoid.com/blog/d_link_dwl_g510_64_bit_drivers), and install using the folder WinXP_2K_x64 contained in the zip file, if you don't know how, read [http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper](http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper)
I hope it is useful to someone. A modest collaboration from Argentina
-------------------
Español
Pude hacer andar la put... D-link 510G en ubuntu 7.04 AMD64bit, primero bajamos el driver de [http://www.publicstaticvoid.com/blog/d_link_dwl_g510_64_bit_drivers](http://www.publicstaticvoid.com/blog/d_link_dwl_g510_64_bit_drivers), y lo instalamos usandoand lo que esta en la carpeta WinXP_2K_x64 que contiene el archivo zip, si no sabes como se usa ndiswrapper podes leer la guia [http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper](http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper)
espero que le sirva a alguien. una modesta colaboracion  desde Argentina

---

