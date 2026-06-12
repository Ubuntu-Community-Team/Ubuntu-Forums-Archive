---
title: "Can I use a Printer connected to a Windoze PC?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-04-30
I know this maybe a silly question, but i'll ask anyway.

Can I use my wife's printer thats connected on her Windoze XP pc over our network??

Its just mine has run out of ink and I need to print something out and haven't got the money to buy new cartridges or to have these ones re-filled :( 

Thanks
Ian

---

### Post by Seisen on 2007-04-30
You can do that as long as you can find a linux driver for your printer. What kind of printer is it?

---

### Post by ianb72 on 2007-04-30
Hi
Its a Lexmark X1150 all in one printer/scanner thingy

---

### Post by Seisen on 2007-04-30
The first link is to setup your lexmark and second one is how to setup Samba so you can print to your Windows box. 
[http://ubuntuforums.org/showthread.php?t=49714]("http://ubuntuforums.org/showthread.php?t=49714")
[http://doc.gwos.org/index.php/Print_Windows_XP_machine]("http://doc.gwos.org/index.php/Print_Windows_XP_machine")

---

### Post by Calash on 2007-04-30
You will need to have the server service enabled on the Windows system (Computer management, Services, Server Service - Set to automatic and then start it)

Then you will have to share the printer (Right click on printer, Sharing, defaults will probably work ok)

Once you get that set you should be able to browse to it on the Ubuntu PC, and load the drivers, and you will be all set.



Edit:  The above assumes the printer is on the XP box.  Based on a reply this may not be the case, so disregard if I am wrong :)

---

### Post by ianb72 on 2007-04-30
Thanks Guys

I'll give that a go in a bit and let you know how it went.

I love this forum, don't matter how dumb you are, you can still find the answer and believe me I've asked some silly/dumb questions :lolflag:

---

### Post by ianb72 on 2007-04-30
Right am I really being dumb now????

I followed the HOW-TO as of [HOWTO Lexmark Printers]("http://ubuntuforums.org/showthread.php?t=49714")

It was going fine till the alien command.

Here is how far I got

[HTML] ian-m3gxx@ian-m3gxx-desktop:~/Desktop/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
ian-m3gxx@ian-m3gxx-desktop:~/Desktop/lexmark$ tar -xvzf install.tar.gz
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
ian-m3gxx@ian-m3gxx-desktop:~/Desktop/lexmark$ alien -t z600cups-1.0-1.i386.rpm
bash: alien: command not found
ian-m3gxx@ian-m3gxx-desktop:~/Desktop/lexmark$
[/HTML]

Have I done something really dumb as no one else seems to be haviing the same problem.

I am trying to do this on my 6.06 PC at the moment.

Cheers
Ian

---

### Post by Extreme Coder on 2007-04-30
Hi ianb72,
I don't know much about printers or sharing ( going to get one soon), but regarding the alien command, Open Synaptic, and install alien ,  or you can always open up a terminal and do a
```
 sudo aptitude install alien 
```
Hope it helped.

Extreme Coder

---

### Post by Seisen on 2007-04-30
I didn't realize that the howto didn't tell you to do that, my fault.

---

### Post by ianb72 on 2007-04-30
Cheers

That worked a treat :)

---

