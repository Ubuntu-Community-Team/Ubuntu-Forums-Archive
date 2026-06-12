---
title: "Canon MP160?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by JReagan1990 on 2006-11-17
I have just installed ubuntu on my laptop, and have found that my canon mp160 does not work, or rather, there is no driver for it.  Does anyone know how I could make this work?  Thanks in advance!;) 


P.S. - I am using dapper.

---

### Post by pelo8280 on 2007-04-07
Download this: [gutenprint package]("ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm")  to your desktop.  Install "Alien" through the Synaptics Package Manager (it may already be installed).  Open a terminal window and type:
     sudo alien --scripts [*path to rpm file*]
This will create a deb package in your home folder (or the folder that you cd'd to).  Run and install that.  Then, attach your printer, turn it on, Go to System, Administration, Printing, add, etc. and install the printer with the "MULTIPASS MP150" driver.

Your Canon Pixma MP160 should work.

---

### Post by celticbhoy on 2007-04-10
forget mp150 follow this link

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

follow instructions

works great and even gets the scanner to go

only prob I had was to search google for canon asia and download manually

and forget last instruction

go to add printer 
select mp160
select install printer
and navigate to /usr/share/cups/model and install mp160 driver then apply

works a treat

---

### Post by Norrad on 2007-04-29
I'm using Ubuntu 6.10 and I followed all the instructions in the above link, but I get an error at this line:

sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usblp0 -E

It says:

lpadmin: No such file or directory

Any ideas on how to fix that?

---

### Post by girlfreddy on 2007-05-05
> **pelo8280 said:**
> Download this: [gutenprint package]("ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm")  to your desktop.  Install "Alien" through the Synaptics Package Manager (it may already be installed).  Open a terminal window and type:
     sudo alien --scripts [*path to rpm file*]
This will create a deb package in your home folder (or the folder that you cd'd to).  Run and install that.  Then, attach your printer, turn it on, Go to System, Administration, Printing, add, etc. and install the printer with the "MULTIPASS MP150" driver.

Your Canon Pixma MP160 should work.

Sorry to say that I'm dense enough not to be able to understand (path to rpm file). I've downloaded the package to my desktop but can't get this to work the way it should. If anyone could give me step-by-step newbie instructions, it would help alot.

---

### Post by Rupart on 2007-05-07
> **Norrad said:**
> I'm using Ubuntu 6.10 and I followed all the instructions in the above link, but I get an error at this line:

sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usblp0 -E

It says:

lpadmin: No such file or directory

Any ideas on how to fix that?

I've exactly the same problem. I did a "locate" for that file and found 2 ones in:
/usr/share/cups/model/canonmp160.ppd
/usr/share/ppd/custom/canonmp160.ppd

Then set the specific directory inside the command:
sudo lpadmin -p MP160 -P /usr/share/cups/model/canonmp160.ppd -v cnij_usb:/dev/usblp0 -E

Got it...

---

### Post by thefoolisme on 2007-05-07
Different canon printer here.  While you're at it, can you guys find drivers for the Canon MF4150? :-)   I can't find any help anywhere other than to be told I'm screwed and will never be able to use my printer.  That would be the main reason I can't switch over permanently.

---

### Post by dragonwings on 2007-07-14
[http://ubuntuforums.org/showthread.php?p=3017140#post3017140](http://ubuntuforums.org/showthread.php?p=3017140#post3017140)

---

