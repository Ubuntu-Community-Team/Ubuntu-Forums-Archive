---
title: "ISA Network card"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by paul6 on 2006-04-01
I need to install an ISA network card because Ubuntu did not detect it during installtion. The problem is I am new to linux and I do not know how to install stuff.. I ran Everest HOME edition under Windows and it listed the card as being "NE2000 Compatabile."  Does anyone know how to install this?

Edit: Yes it is ISA, not PCMCIA, sorry

---

### Post by Pragmatist on 2006-04-02
Is it an ISA or a PCMCIA card?  What is the brand and model of the card, if you have it (if not, is there any info on the card itself?)

---

### Post by Unicast on 2006-04-02
If it is an ISA card it won't be auto detected because ISA cards were never plug-and-play, unlike PCI cards. I know how to do this in windows, but I just don't know enough about linux to advise you.

Good luck anyway! :D

---

### Post by az on 2006-04-02
Open a terminal and type

sudo modprobe ne
then run the gnome networking tool and see if you have an ethernet connection there to configure.  If you do, configure it and make sure it works.

Once it works, make sure that module gets loaded every time you boot.  You do that by adding it to the list in the /etc/modules file

sudo gedit /etc/modules

save and reboot to make sure you did it right...

---

### Post by paul6 on 2006-04-06
Hello, I opened up my computer and I found it is: Linksys Ether16 LAN Card [Link to picture]("http://img.photobucket.com/albums/v157/paul6743/DSC01828b.jpg")

I typed in "sudo modprobe ne" as instructed, and it asked for my password but than nothing happened, so I guess it was not detected at all

Any further help is appreciated.

---

### Post by az on 2006-04-06
[QUOTE=paul6]
I typed in "sudo modprobe ne" as instructed, and it asked for my password but than nothing happened, so I guess it was not detected at all
[/QUOTE]

No.  It means it loaded the driver and the driver did not have anything to compain about.  Did you open the gnome networking tool after that?  I'll bet you find you have a network device to configure.

Once you reboot, the driver is not there anymore.  You need to load the driver and configure the ethernet connection to make sure it works.  Before you reboot, edit the
/etc/modules
file and add it to the end of the list on a line by itself (the name of the module)

sudo gedit /etc/modules

That way, it will get loaded on boot and everything wil work fine.

---

### Post by paul6 on 2006-04-06
I ran it again, and the Gnome network tool,  the only thing listed under devices was "loopback interface"

Is there anything else I can try? Thanks

---

### Post by paul6 on 2006-04-06
bump

---

### Post by Pragmatist on 2006-04-07
I know this doesn't accomplish what you wanted, but here is my advice anyway:

Go buy a cheap PCI ethernet card.  Here is some info on cards that work with Ubuntu:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28hardware%29](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28hardware%29)

I came to my conclusion based on reading a bunch of stuff like this:

[http://linuxgazette.net/issue50/tag/9.html](http://linuxgazette.net/issue50/tag/9.html)

The material is out of date....but so is the card! :)

---

### Post by paul6 on 2006-04-07
[QUOTE=Pragmatist]I know this doesn't accomplish what you wanted, but here is my advice anyway:

Go buy a cheap PCI ethernet card.  Here is some info on cards that work with Ubuntu:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28hardware%29](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28hardware%29)

I came to my conclusion based on reading a bunch of stuff like this:

[http://linuxgazette.net/issue50/tag/9.html](http://linuxgazette.net/issue50/tag/9.html)

The material is out of date....but so is the card! :)[/QUOTE]

Yeah, I figured this card was too old and stubborn to work, just needed someone to confirm it. Now I can safely get rid of it and seek a replacement. Thanks.

---

### Post by pmdubuc on 2006-12-25
Hope this helps someone who came across this discussion looking for answers like I did.

I got one of these cards to work by first booting to DOS and using the Linksys UTILITIES\SETUP program to disable PnP on the card and set the IO address and IRQ to something that doesn't conflict with other cards in the system.  The program warns you if you get a conflict.  

Then I rebooted and used a terminal window to explicitly set the io and irq:

sudo modprobe ne io=0x240 irq=3

Your values for the io and irq parameters may vary, of course.  Then I did

sudo gedit /etc/modules

and added the line

ne io=0x240 irq=3

to what was in the file.

That's it.  The old card works fine.  Hope this helps someone.

---

