---
title: "Some problems with sound and wifi"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by mezerik on 2008-05-28
I can't get a sound out of my 4th generation mbp in ubuntu.
I followed all the steps in this wiki - [https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro")

Seems a bit odd.  Any ideas.

Also i can't seem to get my mbp to connect to my wireless network, i use a netgear router and i have installed and configured madwifi as described in the above wiki.

Still can't get the 2nd click to work either after editing /etc/X11/xorg.conf and inputting this code to the Synaptics Touchpad section..


```
	Option		"MultiFingerButton"	"2"
```

Any help much appreciated. :)

---

### Post by cyberdork33 on 2008-05-28
the multi-finger clicking requires a patched synaptics driver.
[http://ubuntuforums.org/showthread.php?t=790589](http://ubuntuforums.org/showthread.php?t=790589)

---

### Post by mezerik on 2008-05-29
Right, i'll give that a try.

Any ideas why i can't get madwifi to work or any sound from my mac book pro in ubuntu?

---

### Post by theghostbelow on 2008-05-29
I think and hopefully someone will correct me if I am wrong that the madwifi doesn't work with the penryn macbook pro's they in stead require a ndiswrapper work around which at least for me hasn't actually worked yet, as for sound I don't know sorry.  but to make wifi work you can try to use the broadcom driver off of the bootcamp cd with ndiswrapper

---

### Post by stueng on 2008-05-29
I cover both the wireless and sound issues here [http://www.lostpeg.co.uk/content/view/32/73/]("http://www.lostpeg.co.uk/content/view/32/73/")

yes you need to use ndiswrapper on the latest generation macbooks as they dont use an atheros card they use a broadcom one

---

### Post by cyberdork33 on 2008-05-29
For MacBookPro4,1, the proper guide is here:
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)


You are following the guide for 1st and 2nd gerneration MacBook Pros

---

### Post by mezerik on 2008-05-29
when i try to enter the code in terminal

```
sudo ndiswrapper -i bcmw15.inf
```

i get this error

```
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
``` :confused:

---

### Post by cyberdork33 on 2008-05-29
> **mezerik said:**
> when i try to enter the code in terminal

```
sudo ndiswrapper -i bcmw15.inf
```i get this error

```
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
``` :confused:
that should be an l (lowercase L), not a 1.

Time for a cool linux tip: Tab Completion!

When you are typing out a file or folder name on the commndline, you can just type the beginning part of the name, and hit [TAB] then it will give the rest of the file for you. It will even make suggestions if there is more than one possible file.

so for your command, I might do, 'sudo ndiswrapper -i bcm[TAB]' and the system will complete the filename.

---

### Post by mezerik on 2008-05-29
Hmmmm tried a few combinations including the one you said. No luck...

[IMG]http://i25.tinypic.com/24awwn9.png[/IMG]

i am trying to excecute the commands in section 4.  Install the wireless driver on this page.

[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

I even tried copying and pasting the original commands from the page. :confused:

---

### Post by cyberdork33 on 2008-05-29
> **mezerik said:**
> Hmmmm tried a few combinations including the one you said. No luck...
I even tried copying and pasting the original commands from the page. :confused:The problem is that there is really a step missing in the wiki... you need to navigate in the terminal to where the inf file is, or use the complete path in place of bcmwl5.inf

---

### Post by mezerik on 2008-05-29
You little ripper!  Sorted it now.  Finally i can use ubuntu anywhere in the house. :)

Still i have the problem of no sound though.  Did i follow the wrong wiki for that.  I used the one here - [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Only thing i couldn't find though is mux and mux 1

I thought this may be a typo and also looked for mix and mix 1

No luck.  Any ideas?

Thanks for all your help up to now mate, all i need is some sound and the rest is just a bonus, pretty happy to use osx but i need ubuntu for sop as it's not available for osx.

---

### Post by cyberdork33 on 2008-05-29
[https://wiki.ubuntu.com/MacBookPro/SantaRosa#head-8532ccdc8bded528740751c13f4cfff271436c1d](https://wiki.ubuntu.com/MacBookPro/SantaRosa#head-8532ccdc8bded528740751c13f4cfff271436c1d)

---

### Post by mezerik on 2008-05-29
Thanks again mate, everything is working perfectly now :)

---

