---
title: "U3, Wireless and Fingerprint sensor"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by football-fan on 2007-04-02
Hi to everybody who reads this, and thanks for your time

I'm rather (ok, completely) new to Ubuntu, and Linux, in general, and I'm lost...!

I cannot get my wireless to work (I have a Belkin Wireless router, 54mbps, 2.4GHz), and I have absolutely NO idea on how to get started with the fingerprint sensor, and finally, I cannot access my Windows Partitions (because apparently I am supposed to have a 'Disk Manager' but I can't find it in System/Administration).

I also got a U3 Flash drive, and the U3 Launchpad doesn't seem to work...

Thanks in advance for all who thought about helping, and more thanks for those who've responded.

The computer is a Toshiba Satellite M110 notebook,
Specs: 1GB RAM, 60GB HDD, integrated fingerprint sensor.

---

### Post by xpod on 2007-04-02
Hi football-fan
                   You are just a wee bit "lost" in this section it seems:)I think if you were to post your questions in the "beginers talk section" you`d probably get quicker responses..
[http://www.ubuntuforums.org/forumdisplay.php?f=73](http://www.ubuntuforums.org/forumdisplay.php?f=73)

Mabey one of the moderators might like to move it over there for you:) 

I dont know jack about wireless i`m afarid(or much else) but you might like to have a scan through this place for a relatively easy way of mounting your Windows partitions.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
I think the "disks" utility your talking of is the one that used to be in 6.06(dapper) but is no longer available in 6.10(edgy) so that might explain that?

Many of the basics are covered in ayisu`s site but if you still get stuck then hopefully this will have been moved to the "beginers talk section" by then so you at least get some replies for your wireless & u3 flash thingy.

Good luck

EDIT: If your XP is on a ntfs partition then you might also have to read up on "ntfs-3g" for full read\write access to your Windows partition once you mount it btw

---

### Post by bapoumba on 2007-04-02
@ football-fan: moved your thread to "Absolute Beginner Talk" support forum.

---

### Post by jkeyes0 on 2007-04-03
I've got a U3 flash drive, and I ended up removing the U3 software from it (I had to use a windows workstation to do it, because they didn't develop the software to work with Linux). You might be able to do it using VMware and a full windows install on it, but I haven't tried that.

If you're actually wanting to make use of the U3 software in Linux, I don't believe it's doable so far, as the U3 people don't seem to be too Linux-friendly.

---

### Post by compmodder26 on 2007-04-03
To address the issue of the wireless card and fingerprint scanner, can you put these two commands into a terminal and post the output of each here:

```
lsusb
```

```
lspci
```

---

### Post by bodhi.zazen on 2007-04-03
U3 does not work with Linux. I do not but U3 because of this.

to Remove U3 :

[http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html](http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html)

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

[http://cse.msstate.edu/~rwm8/hackingU3/](http://cse.msstate.edu/~rwm8/hackingU3/)

---

### Post by thefoolisme on 2007-04-03
Is there a compatible password program that would work with both Linux and Windows?  I have two U3 drives (bought before I discovered Ubuntu), and I use them to cart around my schoolwork, resumes, etc.  from work to home and everywhere in between.  With all my personal info on there, I really don't want to take the password protection off, without a good alternative.

---

### Post by bodhi.zazen on 2007-04-03
Well, on the Linux side we have permissions ... That will limit access ...

You can remove U3, format the disk to ext3, and change the permissions 

chmod 700 <directory>
chmod 700 <file>

will restrict access to other users.

You can install [http://www.fs-driver.org/](http://www.fs-driver.org/) on Windows.

---

### Post by phr0ze on 2007-04-10
Also, Do a search for portable apps. There are huge collections out there, I'm sure an alternative solution exists. The only thing is you will have to open the drive and run the application yourself versus the U3 auto launch. I keep Open Office and Firefox on my thumbdrive.

---

### Post by phr0ze on 2007-04-10
Ok, I searched for you because I was a little curious. This seems to be the best choice: [http://www.truecrypt.org/](http://www.truecrypt.org/)

Free, Open source, Windows and Linux compatable.

Gathered from the portable apps entry on Wikipedia.
[http://en.wikipedia.org/wiki/List_of_portable_software](http://en.wikipedia.org/wiki/List_of_portable_software)

---

### Post by football-fan on 2007-04-20
Thanks for the help guys, and sorry for the late response... forgot about this thread... :( :( 

anyway, I found a driver for my fingerprint reader, but, i can't install it... here's the "readme" file:

-------------------------------------------------------------------------------------------------------------------------

TouchChip TFM/ESS FingerPrint BSP for Linux Localization HowTo



TouchChip TFM/ESS FingerPrint BSP for Linux comes with all messages in English language. 

This document describes how to change messages to any other language.



Please follow these steps to translate text messages displayed by TouchChip TFM/ESS FingerPrint BSP:



1. create new .po file:

$ msginit --locale=<your language id>



2. Translate lines in the .po file



3. Compile the file:

$ msgfmt <the .po file> -o tfmessbsp.mo

4. copy the output file to /usr/share/locale/<your language ID>/LC_MESSAGES



For example to create translation for Czech language do following:

$ msginit --locale=cs

add translated lines to cs.po

$ msgfmt cs.po -o tfmessbsp.mo

$ cp tfmessbsp.mo /usr/share/locale/cs/LC_MESSAGES



-----------------------------------------------------------------------------

Since I'm VERY lost, can anyone help? Thanks

---

