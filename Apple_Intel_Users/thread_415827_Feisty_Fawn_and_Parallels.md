---
title: "Feisty Fawn and Parallels"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by mwayne on 2007-04-20
I, too , am having problems installing both Ubuntu and Kubuntu in Parallels (Build 3188) with the Live CD - both CD and image file. It starts the boot process and then gets to a black screen and nothing more.

If someone solves this problem, I'd sure love to know how.

Thanks

--Mitch

PS - MacBook Pro Core 2 Duo w/ 2Gb RAM

---

### Post by ronocdh on 2007-04-20
> **mwayne said:**
> I, too , am having problems installing both Ubuntu and Kubuntu in Parallels (Build 3188) with the Live CD - both CD and image file. It starts the boot process and then gets to a black screen and nothing more.

If someone solves this problem, I'd sure love to know how.

Thanks

--Mitch

PS - MacBook Pro Core 2 Duo w/ 2Gb RAM
I have heard little but bad things about Parallels and Ubuntu. I have heard better things about VMWare Fusion beta 3. I would take that for a spin and see how it treats you. Site asks you to register for a beta serial number, but it's at no charge. [Site]("http://www.vmware.com/products/beta/fusion/").

---

### Post by mwayne on 2007-04-20
It's (Ubuntu) installing under VMWare without any problems. Thanks

---

### Post by Chrisj303 on 2007-04-21
As far as running ubuntu as a host OS via a VM, the Fusion Beta 3 is were it's at. Parallels have pretty much given up on anything other than 'windows on a Mac'. 

They have been promising the (much needed Tools) for over 18 months.

I don't think they see it as an important market, but i think the ability to test out a new distro vis a VM is brilliant, and definitly overlooked.


303

---

### Post by jdemesse on 2007-04-21
Could you try to set the maximum memory assigned to the VM to 588 MB and try again ?

There was a bug in Parallels a few weeks (months?) ago that prohibited some kernels from booting. The solution was to lower the memory settings.

---

### Post by tomos on 2007-04-21
Haven't tried Parallels.  I can say that Fusion works very well.  The only problem I see is the sound is low quality.

Take care
tomos

---

### Post by muchmusic on 2007-04-21
I hadn't had an issue with parallels... I set the RAM allotted to 512MB. Perhaps lowering the RAM allocated is the right thing?

---

### Post by bigred3373 on 2007-04-21
VMware is great to use i tried it last night however i wanted it installed on the drive. anyone help me with the screen resolution its highest is 1024x768 i know it wasn't part of this discussion thanks

---

### Post by hajk on 2007-04-21
Just installed Kubuntu Feisty in Parallels for Mac (build 3188) without problems, but I had to take the following actions:

1. Specify the guest OS as Solaris/Other Solaris (strange, but it works) -- can change this back to Other Linux 2.6 after the installation. This solves a problem with installation CD-ROM not being recognized, and has been well-discussed in this forum already.

2. Give the VM 512MB memory, can increase this after the installation.

3. Use the alternate install CD, and boot option "install acpi=off".

After removing the CD it reboots twice and then the login screen appears.

---

### Post by dstrawsb on 2007-04-22
I had the same problem, and I was googling like a madman, finally found a solution or a workaround.

Set the VM configuration to Solaris and Solaris Other, issue has something to do with the CDROM driver, both the way linux 2,6 kernel  handles it and the way Parallels expects it to be.  but I am currently loading 7.04.

Don

---

### Post by myfology on 2007-04-24
This seems to be working,, i'm about halfway installed.. I"m crossing my fingers! Thanks!  I knew there had to be some kinda hack.

m.

---

### Post by insyzygy on 2007-04-26
I just installed feisty fawn into parallels. I had the same experience with the black screen for the livecd, however the alternate install cd (text install) works fine. Oddly when it boots there is a black screen for like 10 second and then it goes to the login and works fine, in parallels the splash bootup is just black. 


So if your ok with the text installer, it works fine, even with only 256 mb allocated to the virtual machine.

---

### Post by Enderend on 2007-05-01
It's time consuming, but I have had success by first installing Dapper (Ubuntu 6.06) under Other Linux 2.6.  From there, I did a upgrade to 6.10 followed by an upgrade to Feisty.  There may be a way to go straight from Dapper to Feisty, which would save time.

---

### Post by Chrisj303 on 2007-05-02
I don't get it - why bother battling with parallels to get it to boot Feisty, as even when it does install, it isn't very well intergrated with your desk top due to the lack of tools.

Fusion Beta 3 is a MUCH better soloution - i had feisty installed with it with no trouble at all. It actually created and compiled the tools right in front of my eyes, as there were no feisty - specific tools built into fusion. Incredibly impressive.

Parallels are not really interested in Linux users any more - they are concentrating on making windows work in OSX, as that is where the money (apparently) is.
I used parallels from build 1970 all the way to 3188, and there was not a single improvement made to the Linux side. 

cheers,
chrisj303

---

### Post by Enderend on 2007-05-02
For all of you who are running VMware Fusion Beta:

Were you able to get VMware Tools installed?  If so, how?  

I've had no luck with installing them in Feisty.

---

### Post by Chrisj303 on 2007-05-02
> **Enderend said:**
> For all of you who are running VMware Fusion Beta:

Were you able to get VMware Tools installed?  If so, how?  

I've had no luck with installing them in Feisty.

Yeah, i got the tools working in feisty.

You need to burn the Fusion disc image that you downloaded to a CD. Then run Fusion and look at the help files (search for 'Tools'). It gives step by step instructions - dead easy. 

A lot of people don't realise that the .dmg needs to be burnt to a CD in order to access the tools - this is were a lot of the confusion comes from.

Unless VMware have changed the Beta release to include the tools for feisty, you will have to let fusion create them for you. I just pushed 'enter' at every prompt to choose default settings, and it worked perfectly.

303

---

### Post by Nasiom on 2007-05-02
FYI,

I just install it succesfully in VirtualBox Beta 1 (The new Open Source virtualization engine)  The nice thing is it has additions for Linux much like all others have for Windows.   So mouse synchro, copy/paste, shared folders etc.

Everything seems to be working fine so far.

-Nasiom

---

