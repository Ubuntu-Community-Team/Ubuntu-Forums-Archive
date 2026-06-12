---
title: "need help with wireless adaptor"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by dronug on 2005-11-02
i need help installing a linksys wireless b usb network adaptor 802.11b model no wusb11v4

im using ubuntu hoary hedgehog
any help is appreciated

---

### Post by matthewv on 2005-11-02
You'll need to use a tool called ndiswrapper, which allows you to use the windows driver files for your wireless adaptor. Run a search on the forums or the wiki for more info. I think it just involves installing ndiswrapper from synaptic and then telling it what drivers to use...

---

### Post by dronug on 2005-11-03
i have the ndiswrapper, do you know where i can get the drivers for the wireless adaptor.

tryed using drivers from the install cd that came with it, but it didnt seem to work.

---

### Post by Dr. Nick on 2005-11-03
[QUOTE=dronug]i have the ndiswrapper, do you know where i can get the drivers for the wireless adaptor.

tryed using drivers from the install cd that came with it, but it didnt seem to work.[/QUOTE]

You can try to get them from linksys web site, but they will be .exe which wont work until you extract it, Your best bet is to use the CD ones, but be aware their may be a few inf files and only one will work, What specific errors were you geting? Also do you happen to kow the chipset it uses? Their may be native linux drivers like my v3 but I am not sure

---

### Post by dronug on 2005-11-03
I have 3 inf files

 wusb11v4.inf
 netusb.inf
 lspmusb.inf

 ive tryed all of them with ndiswrapper. wusb11v4 and lspmusb show up invalid in ndiswrapper -l. netusb shows up present, but it doesnt show hardware present. in iwconfig it shows no wireless extension.

i think my chipset is prisum9x dont know how to find what kind of chipset it uses.

also how do u extract a exe file.

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=Dr. Nick]You can try to get them from linksys web site, but they will be .exe which wont work until you extract it, Your best bet is to use the CD ones, but be aware their may be a few inf files and only one will work, What specific errors were you geting? Also do you happen to kow the chipset it uses? Their may be native linux drivers like my v3 but I am not sure[/QUOTE]

There are native Linux drivers, but the only distro I know has them is kanotix because they are so new (hint hint).

---

### Post by Dr. Nick on 2005-11-03
[QUOTE=dronug]I have 3 inf files

 wusb11v4.inf
 netusb.inf
 lspmusb.inf

 ive tryed all of them with ndiswrapper. wusb11v4 and lspmusb show up invalid in ndiswrapper -l. netusb shows up present, but it doesnt show hardware present. in iwconfig it shows no wireless extension.

i think my chipset is prisum9x dont know how to find what kind of chipset it uses.

also how do u extract a exe file.[/QUOTE]

To unzip the exe just open a terminal in the directory you downloaded it into and type *unzip **filename.exe*** you can install a package called ndisgtk from synaptic (probably universe) which may make it a bit easier to install the inf after extraction

---

### Post by fuscia on 2005-11-03
[https://wiki.ubuntu.com/Linksys_WUSB11](https://wiki.ubuntu.com/Linksys_WUSB11)

my version 2.6 worked out of the box on breezy.

---

### Post by dronug on 2005-11-04
when using the wusb11 tutorial iran into a few problems.  first when i type in the command sudo apt-get install build-essential linux-headers-uname -r  i get command line option [from -r] is not known

so i just skipped this in went on.  everything goes fine until i get to  the make and sudo make install.
everything works fine but i get a few errors.  module error 1cannot stat. and /lib/modules/2.6.10-5-386/build/tmp-versions/*.mod no such file or directory.

i previously installed ndiswrapper 1.1 and tryed installing windows drivers but with no success.

i really like ubuntu and would love to get my usb wireless adaptor to work.  it does show up in device manager

---

### Post by janne5011 on 2005-11-04
hi you have one of this files ok?
"wusb11v4.inf
netusb.inf
lspmusb.inf"

what you need for ndiswrapper is 1 inf-file AND 1 .sys file.
maybe you already found that out?

here is a grapichal way use ndiswrapper maybe good:
[http://www.ubuntuforums.org/showthread.php?t=85378](http://www.ubuntuforums.org/showthread.php?t=85378)

---

### Post by dronug on 2005-11-04
yes i have those 3 exact files netusb is the only one that shows up valid in ndiswrapper -l,  but it shows no hardware present.

maybe my chipset doesnt work with ndiswrapper.
can anyone tell me how i can find out what chipset my wusb11v4 has.
i have the ndisgtk and ndiswrapper 1.5. the graphic interface is alot easier than typing in the terminal.

im really starting to think my wusb11v4  usb adaptor just doesnt work with ndiswrapper  :(

---

### Post by Lambert on 2005-11-04
It will work as the developers have this piece which they use to test.

[http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281](http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281)

> when using the wusb11 tutorial iran into a few problems. first when i type in the command sudo apt-get install build-essential linux-headers-uname -r i get command line option [from -r] is not known

don't type in uname -r in the command. 

from a terminal type in

```
uname -r
```

This will give you the kernel version you're running. replace uname -r in the above syntax with the out put. should be something like 2.6.12-9-386

When you type ndiswrapper -l and it doesn't show hardware present then first step is to get the device present. There maybe a hotplug problem where it's not recognizing the device being present. Do a search for "hotplug usb" or something of that nature.

---

### Post by janne5011 on 2005-11-04
hm .one way make sure is look in ndiswrapper directory and see is there one .inf-file and one .sys-file?
or is the directory simply empty.
?

---

### Post by dronug on 2005-11-04
success!  after many hours ive got it to work.
the sad part is im really not sure how i did it. i reinstalled the wusb11v4.inf file with ndiswrapper and the hardware showed up, but i tryed that file many times before and it came up invalid in ndiswrapper -l.
but that doesnt matter now because im writing this post from my ubuntu pc.

man i really appreciate all the help from everyone who posted on this thread and i hope it helps someone else with similar problems.

thanks again:razz:

---

### Post by newbie2 on 2005-11-04
here is also some ndiswrapper information
[http://nextgen.no-ip.org/~andrew/linux/ndiswrapper/ndiswrapperinfo.php](http://nextgen.no-ip.org/~andrew/linux/ndiswrapper/ndiswrapperinfo.php)

---

