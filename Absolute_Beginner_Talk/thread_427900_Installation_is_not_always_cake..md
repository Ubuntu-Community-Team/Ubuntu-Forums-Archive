---
title: "Installation is not always cake."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by bill602 on 2007-04-29
Talk about a newbie.  I can't believe I'm having trouble installing this.  I downloaded Ubuntu and copied it onto a CD.  I put a spare hard drive with no operating system into my desktop and set up the machine's bios to boot off the CD drive.  The problem is as the machine starts up, it tells me to remove all disks and hit any key to continue.  If I just hit a key, the same message keeps popping up.  It can't seem to find anything on the CD it can work with.  Did I download the wrong file?  I have heard that the .iso file gets things started, but it obviously hasn't run into my computer before.

I'm really anxious to get off of Microsoft.  Bill Gates is great with charities, but I don't like his way of running a company.

Bill602

---

### Post by LaurelLynn on 2007-04-29
Dear bill602,

A few ideas on what could be wrong:

1. For the bios, CDROM has to be the first entry in the boot sequence, not just enabled (you probably thought of that one).

2. There is usually a function key that flashes on the screen for the boot menu (usually F10 or F12) that you can use to manually select the CDROM

3. Cd burning software is not 100% reliable, try burning at a very slow speed and turn on the verification option if there is one.

4. The download might have been corrupted. Try it again, and if possible check the MD5 hash code to be sure it is correct.

Hope one of those helps.:)

---

### Post by apunc1 on 2007-04-29
exactly how did you copy it to cd? detailed instructions are here [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

if you give the specs of your computer we can decide which version you should download (i.e. 64 bit, alternate cd)

---

### Post by bill602 on 2007-04-30
OK.  My desktop is a Sony Vaio with an Intel Pentium 4 running Windows XP Version 5.1 with Service Pack 2.  I've had it for about 5 or 6 years.  

I used the Copy function in Windows Explorer to transfer the downloaded Ubuntu file from my hard drive to the CD.  The CD was not a boot disk.  I'll check out the instructions on the link you suggested.

When you mentioned the issue of version, I began to wonder if Ubuntu is the right system for me.  Maybe kubuntu would be better.

Thanks for the help,
bill602

---

### Post by zvacet on 2007-04-30
It is same thing Ubuntu or Kubuntu.Only difference ic graphic enviroment.Important thing is did you downloaded proper version for your procesor.if you have 32 bit you must download version for that.I think that version is called x386.If you have 64 bit procesor you can install both(32&64).here is one more page for download and burn iso
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

To not download all iso again(if is corrupted) you can do this:download iso with torrent and point download in folder whee your previous iso is.Torrent will just chek it and if it is some files with errors torrent will replace just them.Aftr that burn iso on lower possible speed.

---

### Post by Spike-X on 2007-04-30
> **bill602 said:**
> 
I used the Copy function in Windows Explorer to transfer the downloaded Ubuntu file from my hard drive to the CD.  The CD was not a boot disk.  

You need to use actual CD burning software with a "burn image to CD" function. Nero does this, and I'm sure there are freeware options also.

---

### Post by Nythain on 2007-04-30
yeah, your problem lies in the fact that you have a cd with a big iso file on it... not the contents of an iso file on a cd.
you need to find a piece of windows software that allows burning images from iso... such as nero... then burn the iso that way, not just copying the file over to the cd...

also there are more differences between ubuntu and kubuntu than just saying the graphical gui style... the main difference is the fact that kubuntu uses kde instead of gnome, but that effects much, like kdm instead of gdm... kate instead of gedit... most of the pakcaged software is different, kubuntu doesnt ship with firefox standard, it has konqueror... ktorrent instead of whatever ubuntu gets... Desktop Environments are more than just graphical gui styles... they encompas libraries and entire software packages associated with...

---

### Post by dichtbijzee on 2007-04-30
freeware for burning iso's on windows: InfraRecorder 0.42

[http://infrarecorder.sourceforge.net/]("http://infrarecorder.sourceforge.net/")

---

### Post by indytim on 2007-04-30
One other thing that I have found helpful : 
When booting to your new LiveCd, take the few minutes required to do the CD check  before instaliing.  This will help insure that the CD contents are correct for a complete installation.

IndyTim

---

### Post by Nythain on 2007-04-30
i guess now would also be a good time to throw out that whole BURN SLOWLY warning :) just to prevent any future potential installation problems

---

### Post by Cheese Sandwich on 2007-04-30
Wouldn't a direct (right click)->"Write to CD"  on the ISO file work if the CD is blank & unformatted?

I've successfully burned ubuntu onto CDs in Win98 by doing something similar.

( Hey **bill602** - it's me, John. :) )

---

### Post by bill602 on 2007-05-03
Thanks much for your info.  It did the trick.  I got thru the download, checking, burning, and loading processes and now have Ubuntu running.

---

### Post by bill602 on 2007-05-03
Hey John, good going.  What do you think about Kubuntu?

---

### Post by Cheese Sandwich on 2007-05-04
> **bill602 said:**
> Hey John, good going.  What do you think about Kubuntu?

Haven't tried it, but I did convert my (somewhat old) desktop machine from ubuntu to xubuntu (with the xcfe window manager) - it's right what they say, it's considerably "snappier" re speed of opening windows, etc, although it has a clunkier look to it.

I'm keeping regular ubuntu (with the gnome window manager) on my new, faster laptop. Kate uses the laptop quite a bit as well, and has no problems using ubuntu over windows.

---

### Post by bugginmiami on 2007-05-04
New here. Just installed last night. Ive played with Knoppix for recovery, and red hat a few years ago but with the way my mind works, its like starting over. I had very few problems.  It installed and recognized everything on my 8 year old laptop (that has been decommissioned from the windows world for a few years now!). Runs great. (was incredibly piggish running on live cd, but installed, very decent). It recognized all my hardware including my pmcia wired and wireless cards. (I could not get it to work with the WEP settings of my Cisco wireless router, only in wide open for now). Ive found one screensaver that will lock up the laptop, but otherwise its never locked up. My new round of problems is just based on my lack of knowlege (compiling programs, etherape, mrtg, other security tools). Ive just never done it and will have to learn or ask you guys, but as far as installing, Im a happy camper. Grear product and tool!
jasonw

---

### Post by bill602 on 2007-05-06
Hey Cheese Sandwich,
We now have Ubuntu on the desktop & Xubuntu on the laptop.  I think each it's place, but I will probably end up preferring the version I get used to first.  Right now, I'm trying to figure out how to wake up Ubuntu from Hybernation mode.  I tried that at the end of my last session and now it won't wake up.  Have you run into that yet??  In order to send this, I had to plug the laptop directly into the cable modem.
Bill602

---

### Post by Cheese Sandwich on 2007-05-06
> **bill602 said:**
>  Right now, I'm trying to figure out how to wake up Ubuntu from Hybernation mode.  I tried that at the end of my last session and now it won't wake up.  Have you run into that yet?? 


No, I keep both computers on all the time.

You could try a search here - type "wake hibernate", for example, in the search field in the upper right & hit enter or click "go". If that's not helpful, start a new thread on the issue.

> **bill602 said:**
> In order to send this, I had to plug the laptop directly into the cable modem.


Is that related to the hibernation issue, or is that something different? Have you gone into System->Network & set the wireless connection appropriately? If no luck, a reboot might help.

---

### Post by LucMeister on 2007-06-09
i had the same problem when my cd didn't want to install.

the problem is that your cd is corrupt because when i installed from another, it worked perfectly.

i now have kubuntu 7.04 and it looks very much like windows but it still acts as a linux OS.

the problem i face is installing applications such as matlab, mathematica and various add ons because i don't understand the commands and what they do.

i think i need a textbook on different commands and what they do.

i must admit, windows sucks, but linux is any better because it is not user friendly.

hope you come right with your problem.

regards,
LucMeister

---

### Post by Cheese Sandwich on 2007-06-09
Sadly, bill602 has given up on ubuntu due to technical problems, and has returned to Windows.

---

