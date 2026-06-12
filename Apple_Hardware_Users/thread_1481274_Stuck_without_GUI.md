---
title: "Stuck without GUI"
date: 2010-05-12
forum: Apple Hardware Users
---

### Post by 1984dc on 2010-05-12
Dear all

As a struggling nubie (i have only been using Ubuntu on my laptop for a year and loving it!) i tried to install ubuntu onto my other PC (Powermac G5 dual core 2.5ghz sata hdd PPC). I Originaly wanted to install to a seperate harddrive but with the open firmware on the ppc it seemed a little complicated and i went for a normal instalation.

I was told that the alternate CD would be the only one that would install to my type of pc correctly. The instalation seemed to go okay, though at the end of the software install it flashed up with an error message saying that i had not finnished this task corrrectly. seeing as the error message was only after all packages had been retrived i carried on regardless.

I then rebooted after instalation and i can only access Ubuntu through the command line (no GUI) i tried sudo apt- getupdate and sudo apt-get install ubuntu-desktop I then get the message;
"Media change: please insert disc labelled 'Ubuntu 10.04 LTS _Lucid Lynx_- Release powerpc 20100428' in the drive '/cdrom/' and press enter"
I tried it with the live "desktop" CD and the alternate CD but neither of them seem to work giving me the Error "Unable to fetch some archives..." 

I searched for a release that corresponded "Ubuntu 10.04 LTS _Lucid Lynx_- Realease powerpc (20100428" but i couldn't find a release on google apart from a page of server releases with the same release number.

any help on this would be greatly appreciated

Many thanks in advance


DC

System: Powermac G5 dual core 2.5ghz PPC sata hdd Running (at the moment) with an ethernet connection

---

### Post by 1984dc on 2010-10-25
this is how i Fixed it in the end.

I made a bootable pen drive of os x like this

[]("http://www.ehow.co.uk/how_6116410_make-usb-drive-os-x.html")

I then booted into it using these commands 

[]("http://www.macosxhints.com/article.php?story=20060301112336384")

and then i recovered the files using 

[]("http://www.cgsecurity.org/wiki/PhotoRec")

and then repartitioned and reinstalled OS X and then later ydl 6.2 (which was in the end the onlu linux distro which worked "out of the box").

---

