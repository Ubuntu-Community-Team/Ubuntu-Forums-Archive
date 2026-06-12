---
title: "I am an absolute ubuntu noob with a question.."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by poriggity on 2008-01-21
Ok, first off, I partitioned my hard drive, and run xp Pro on one partition, and Ubuntu on the other partition.  Internet works fine with my netgear WP111 USB adapter in XP pro, but not in Ubuntu.  I have gone to the synaptic package manger, searched for ndiswrapper and it doesn't exist, even though the cd I got with the "Ubuntu bible" I bought says it should be there.  Is there a way to put the ndiswrapper in the ubuntu OS?  I can't seem to find it.  Any help is appreciated.  I can't really download it.. unless of course there is somewhere to down load it which would let me burn it to CD then transfer to ubuntu.
Do I need to erase the OS and start over?

Thanks,
Scott

---

### Post by frup on 2008-01-21
This is the ndiswrapper project website
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

---

### Post by poriggity on 2008-01-21
Right.. I saw that... but is there a way to download it from the XP partition on my hard drive, and send it to the ubuntu partition section of the HD?

---

### Post by jleaker01z on 2008-01-21
> **poriggity said:**
> Ok, first off, I partitioned my hard drive, and run xp Pro on one partition, and Ubuntu on the other partition.  Internet works fine with my netgear WP111 USB adapter in XP pro, but not in Ubuntu.  I have gone to the synaptic package manger, searched for ndiswrapper and it doesn't exist, even though the cd I got with the "Ubuntu bible" I bought says it should be there.  Is there a way to put the ndiswrapper in the ubuntu OS?  I can't seem to find it.  Any help is appreciated.  I can't really download it.. unless of course there is somewhere to down load it which would let me burn it to CD then transfer to ubuntu.
Do I need to erase the OS and start over?

Thanks,
Scott

Ndiswrapper should be in Applications>Add/Remove.  Might need to add canonical repositories if it's not showing up.  Check /etc/apt/sources.list and see if there is a Canonical repository in there commented out (will have a #) in front of it.  It should look like this:

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

 Remove the # on the last 2 lines that start 'deb' and restart your Add/Remove.  The lists should update and you will find it listed then.

Edit:  To edit that file, open a terminal (Applications>Accessories>Terminal) then type in "gksudo gedit /etc/apt/sources.list".  If you open it up via the file manager with the text editor it won't let you save any changes.  You have to use the 'gksudo gedit' to give the text editor the proper permissions to alter that file.

---

### Post by poriggity on 2008-01-21
Great!  Thanks for the quick responses.. I am a total newb in the linux arena.  I have played around with Mac OS X and have been a windows user forever.. But I am really tempted to just scrap it all and go with ubuntu, as long as I can get a working internet connection :)
Scott

---

### Post by poriggity on 2008-01-21
Ok, so what's the solution if I don't see ndiswrapper in add/remove applications?

 I am confused.. supposedly this CD I have with the book I bought came with ndiswrapper, and its not there.

---

### Post by poriggity on 2008-01-23
anymore ideas on this?  Am I gonna have to hardwire the computer to my router, and download an ndiswrapper?
Scott

---

### Post by Mogurijin on 2008-01-23
The problem that people don't seem to be realizing is that you don't have an internet connection, so not much will automatically appear in the add/remove. Go to Admin -> Sources and look toward the bottom. There are options to add a cd repository. Play with those settings. Seeing as I'm in Windows with no Ubuntu installed, I can't actually see the screen. I hope this helps...

---

### Post by thelatinist on 2008-01-23
You can download the package from [http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9) and save it to a flash drive or a floppy, then install using gdebi.

---

### Post by poriggity on 2008-01-23
Ok, I now have the desktop hard wired to the router, but it can't stay this way.  It has to be wireless, unfortunately.  I downloaded ndiswrapper, and attempted to install the drivers for my wpn111, and this is what I get:
```
scott@scott-desktop:~$ ndiswrapper -iWPN111.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
scott@scott-desktop:~$ 

```

What am I missing?
Scott

---

### Post by stalkingwolf on 2008-01-23
Try this it has worked for me on several different systems with the adapter you are using.

Once you establish a connection you can download at will to fix if need be.
Go to-

System > Administration > Network tools > Devices > Highlight your adapter and check the configuration.

Then go back to,
System > Administration > Network settings> Network Connections > check for
your connection. > Hosts > ff02::ip6 all routers > highlight it and click add.

Again this has worked for ME several times.

---

### Post by poriggity on 2008-01-23
Thanks for all the help so far guys.  stalkingwolf, I am going to try it, but I did find a 50' ethernet cable laying around, and I can quite easily, run the cable from my router to the computer, so worst case scenario, I have to hard wire it.  No biggie.  Thanks!  I can't wait to explor all the ubuntu options!
Scott

---

### Post by thelatinist on 2008-01-23
> **poriggity said:**
> What am I missing?

You are missing the space between the option and the file.

You also will probably need to be in the folder that has the .inf file in it to execute this command, or perhaps you can specify the complete path.

---

### Post by oldos2er on 2008-01-23
> **poriggity said:**
> I can't wait to explor all the ubuntu options!
Scott

 You'll need to enable your repositories before you can install any new programs. Go to System, Administration, Software Sources, and check all the boxes on the first tab 'Ubuntu Software.'

---

### Post by poriggity on 2008-01-23
Ok, here is another question.  Can I easily upgrade from Edgy 6.10 to Gutsy 7.04 without downloading the ISO file and buring to disc?

---

### Post by thelatinist on 2008-01-23
> **poriggity said:**
> Ok, here is another question.  Can I easily upgrade from Edgy 6.10 to Gutsy 7.04 without downloading the ISO file and buring to disc?

I wouldn't.  I strongly suggest a clean install rather than a version upgrade, especially an upgrade through two versions.

---

### Post by poriggity on 2008-01-23
Ok, so if I do it, is there a secret to doing a format on the partioned section of the hard drive that holds ubuntu 6.10?  Can it be done through the OS?

FYI, I decided I didn't like the finicky nature of wireless on my desktop (had problems with it in XP too) and bought a 50' cat5 cable and tucked it under the carpet, from router to computer.  Internet problem solved :D
Scott

---

### Post by thelatinist on 2008-01-23
> **poriggity said:**
> Ok, so if I do it, is there a secret to doing a format on the partioned section of the hard drive that holds ubuntu 6.10?  Can it be done through the OS?

You can just run the Live CD and choose the "Manual" partition option, and choose the partition you want to use.  The Live CD will do everything for you.

---

