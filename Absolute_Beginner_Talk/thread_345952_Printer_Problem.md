---
title: "Printer Problem"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by wickstopher on 2007-01-25
Hello!  I am a thrilled new Ubuntu convert, running Edgy Eft on my 2.0ghz pentium IV with 1gb of ram.  

One problem that I have run into is getting my printer to work.  I have an HP Deskjet 3845 that is connected to my computer via USB.  Ubuntu easily recognized the printer, and appears to have the correct drivers at work.  It is sending commands to the printer (i.e. it makes noise and the paper feeds through), but nothing is printed.  I currently only have 1 print cartridge installed, the black cartridge.  No color cartridge installed.  Windows XP gave me error messages with this configuration ("printing in ink backup mode"), but still enabled me to print in grayscale/b&w.  I seem to have everything configured correctly, i.e. paper size and print mode (grayscale/black cartridge only), but the issue persists.  No error messages, but no results.  Any help out there?

---

### Post by DSn0wMan on 2007-01-25
My HP 3845 works pretty well. I just selected 3840 from the list of printers. It has been a while since I installed it, but if I remember right I had to install hpijs. I think it's in the repo's. I also found a link that might be helpfull.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3845](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3845)

---

### Post by wickstopher on 2007-01-25
Hmm, still no dice.  From what I can tell, everything got installed okay.  Although, I did get this strange screen when installing, and I had to reboot to get rid of it (it wouldn't close through normal means).

[image (screenshot) here]("http://www.christopherwicks.com/bucket/hpinstallprob.png")

strange.  but, when I look at what drivers are available for my printer, it appears to be the one in use.

[image (screenshot) here]("http://www.christopherwicks.com/bucket/driverinq.png")

I'm assuming this means that it is installed, because when i click on the Install Driver button it takes me to a file menu.

Not sure what I'm doing wrong here.  Is it possible that not having a color cartridge here would make a difference?

---

### Post by DSn0wMan on 2007-01-25
It seems like the screenshot you provided is the postfix config.

---

### Post by wickstopher on 2007-01-26
Sorry, I'm not sure what that means!  Do you mean that everything should be working properly in theory?

---

### Post by DSn0wMan on 2007-01-26
I mean that the screenshot you posted is a shot of the postfix (email server) configuration. This has nothing to do with printer installation.

---

### Post by wickstopher on 2007-01-26
Okay, I think I was going about this the wrong way.  

I am now going through the process of manually instaling hplip (and in the process, installing a seemingy endless number of libraries and packages) following the instructions at [http://hplip.sourceforge.net]("http://hplip.sourceforge.net").

I have managed to make my way to one of the last steps:

```
sudo hp-setup
```

when I run hp-setup, this is what i get:

"error: Unable to connect to hpiod"
"error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again."

[IMG]http://www.christopherwicks.com/bucket/hpsetuperror.png[/IMG]

also perhaps of note, when i run the following command:

```
sudo /etc/init.d/hplip restart
```

i get this message that starting hpiod failed:

[IMG]http://www.christopherwicks.com/bucket/hpiodfailed.png[/IMG]


I haven't found out a way yet to resolve this issue.  Thanks again for your patience and support!

As an added note, I mentioned earlier that my printer was picking up commands sent from the computer, feeding paper through, etc., just not actually printing.  Since going through all of these steps, my printer has ceased to recognize commands, and when I try to print, nothing happens at all (except that the print job gets held in the printer queue indefinitely, which also wasn't happening before).  Tearing my hair out!

---

### Post by wickstopher on 2007-01-28
Just to let those who may have been concerned/curious/as frustrated as I was know, I resolved my printer issue.

First of all, I did a total reinstall of Edgy Eft, as I don't really know what I was doing, and with all of the manual configuring and stuff I was doing without really knowing what I was doing, I think I had hplip installed or partially installed about 4 or 5 times on my machine.

As it turns out, at least in Edgy Eft, hpijs/hplip comes pre-installed, right out of the box.

Initially, I still had the same problem (i.e. my printer was feeding paper but not printing anything)

Very frustrated and on the verge of giving up ever being able to print in Ubuntu, as a last resort, I searched the Add/Remove programs list (via the Applications menu) for anything to do with printers.  and came up with "Printers" (foomatic-gui 0.7.6).  I installed this little application, and configured my printer through its' interface, and all of a sudden, I'm printing beautifully.

So, esentially, the lesson that I learned is this:  don't mess around with root functions you have no idea about unless you absolutely have to.  If you are new to linux and ubuntu, take advantage of their very easy to use Synaptic Package Manager, and only use the shell/manual configurations as a last resort.  I guess.  Hopefully as time goes on I'll learn more about how this all works, but for now, I can print, and the one piece missing out of making this my complete operating system solution is finally in place.  Goodbye Windows!

---

### Post by stueyboy on 2007-02-17
Thanks for the foomatic hint. I had setup my photosmart 2700 with the hp-setup tool but it wouldn't print, so I tried this and it all works now. Sweet

Ta

---

### Post by joaodelvalle on 2007-03-08
Cool. To solve the same problem with the same printer, I uninstalled the hplib package completely, downloaded the newest version, built and then hpsetup worked fine.

João.

---

