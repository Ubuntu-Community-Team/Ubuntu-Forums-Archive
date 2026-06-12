---
title: "SATA Raid controller.......Big problems"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by *desk* on 2006-02-19
I did post this in an earlier thread but I think it is important to create a new thread on this subject. Not only does it effect  Ubuntu but many other Distros.

My problem was....and still is my SATA drive.
I have attempted to install five Distros and have had the same problem with all of them.......they have all froze durring installation. 
It's to do with the drivers for the SATA raid controller. I have two drives, the other is an IDE. If I disconnect the SATA drive then I have no trouble at all, on any of the Linux distros.
Incidentally XP has no problems with the SATA drive.
There are many people in the various forums having similar problems, but I have not yet found a solution.
Please, you experts out there, have you an answer?

Many Thanks

---

### Post by nickle on 2006-02-19
What is your setup?
Are the sata drives activated in your Bios?
Have you tried a Live CD for any of the distros to see if the sata drives are detected properly...

Without some more specific info, I'm afraid there is little else I can say. Incidently, I habe and IDE and 2 sata devies installed; they worked with suse and ubuntu. I would expect most of the nerwe distros to identiy this kind of configuration. It is a question of understanding what might be special about your system...

---

### Post by *desk* on 2006-02-19
On my IDE C drive I have installed XP.
The SATA controller is a seperate Silicon card and therefore it is not recognised until the driver is manually introduced after XP is installed.
At this point everything runs smoothly using both drives.
If  I attempt to install a distro it will freeze when attempting to recognise the devices. I have noticed that it disables IRQ #10....which is the IRQ of the SATA controller.
If I disconnect the SATA drive, the Distro installs and runs without any problems.
I have not tried a live disk.

---

### Post by nickle on 2006-02-19
It seems breezy doesn't recognize your controler. You might be able to get a linux driver for your specific controller by doing some searches and a way of installing it.
Previously I had a similar problem with a promise sata controler. I found a way of installing it with Suse. My experience on this front is very flakey and I cannot give you any specific advice

However, I gave up with breezy when I discovered that the alpha release of dapper recognised the controler immediately...
Although the dapper version is not final yet, it might be worth downloading the latest version and see if it recognizes your controler. This is a pereninal problem with linux; it is often somewhat behind is supporting new hardware.

Give it a try and hey good luck. Just keep it in mind if you get a linux distro working you will never look back...

---

### Post by *desk* on 2006-02-19
Thank you Nickle, I'll give that a try.
I am very happy with Linux otherwise.
Thanks again

---

### Post by *desk* on 2006-02-19
Can anyone advise me where to download Dapper from.
Thank you

---

### Post by nickle on 2006-02-19
For Kubuntu, i.e. Ubuntu with a kde gui
[http://kubuntu.org/](http://kubuntu.org/)

For Ubuntu, i.e. Ubuntu with a gnome gui (namimg convention is confusing I know, but..)
[http://cdimage.ubuntulinux.org/dvd/current/](http://cdimage.ubuntulinux.org/dvd/current/)

The final release of Dapper will be available in April. Release details will be on the  link..

---

### Post by Coelocanth on 2006-02-19
[QUOTE=*desk*]Can anyone advise me where to download Dapper from.
Thank you[/QUOTE]

[Try Here](http://cdimage.ubuntu.com/releases/dapper/flight-3/).

Just to be clear: Drake's still in testing, and it's not advised to use it as your main OS yet.

*edit* Here's a link to the [DapperFlight3](https://wiki.ubuntu.com/DapperFlight3) Wiki as well.

---

### Post by *desk* on 2006-02-20
Thank you for all your help.
I'm now downloading Dapper, I am aware that it will still have bugs but I will run it alongside my other OS.
If I can get my SATA drive sorted out I will be more than happy with Ubuntu.
Thinking about it I would even replace my drive if necessary, rather than move away from Ubuntu. 

Des Kinsman

---

