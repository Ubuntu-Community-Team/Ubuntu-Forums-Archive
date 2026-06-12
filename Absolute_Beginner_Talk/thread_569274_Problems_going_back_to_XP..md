---
title: "Problems going back to XP."
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by nameneeded on 2007-10-06
So in light of the problems I'm having with Ubuntu I decided to unistale it and go back to XP on my Gateway Tablet. Thinking of puting Ubuntu back on as a dual boot to use when I need a reason to get stressed.

S I go to install XP using my recovery discs.... no dice. Says Recovery failed and won't give options for a clean reinstal.

"Strange" I thought. but OK maybe they aren't meant for that. So I pull out my XP Pro disc I have. Figure I can call MS after to gewt the proiper codes and such.

It looks like its going to install then I get a screen saying that it can't find any installed Hard Drives!

Now I know what you're thinking... Its cause the drive is formated for linux right? 

Wrong. I too thought of that and have tried after reformating it to bot Fat32 and NTFS to no avail. 

I even bought a new HD and got the same results! 

And whats even weirder is that I can install any linux distro no problem!

Any ideas? I am not a computer geek. More computer friendly. I was told it could be my CMOS settings but have no clue what to do about that.

---

### Post by harbdog on 2007-10-06
XP is telling you that you're better off not installing it :popcorn:



if all else fails, grab VMWare Server and create a new XP image for you windows needs

---

### Post by n3tfury on 2007-10-06
> **nameneeded said:**
> So in light of the problems I'm having with Ubuntu I decided to unistale it and go back to XP on my Gateway Tablet. Thinking of puting Ubuntu back on as a dual boot to use when I need a reason to get stressed.

S I go to install XP using my recovery discs.... no dice. Says Recovery failed and won't give options for a clean reinstal.

"Strange" I thought. but OK maybe they aren't meant for that. So I pull out my XP Pro disc I have. Figure I can call MS after to gewt the proiper codes and such.

It looks like its going to install then I get a screen saying that it can't find any installed Hard Drives!

Now I know what you're thinking... Its cause the drive is formated for linux right? 

Wrong. I too thought of that and have tried after reformating it to bot Fat32 and NTFS to no avail. 

I even bought a new HD and got the same results! 

And whats even weirder is that I can install any linux distro no problem!

Any ideas? I am not a computer geek. More computer friendly. I was told it could be my CMOS settings but have no clue what to do about that.

maybe it's not showing up in the bios?  depending on manufacturer, during startup hit F2 (possiblly something else) to get into the bios and make sure it sees it and sees it as a bootable device.

---

### Post by n3tfury on 2007-10-06
> **harbdog said:**
> XP is telling you that you're better off not installing it :popcorn:



if all else fails, grab VMWare Server and create a new XP image for you windows needs

i don't even know what to say to that..

---

### Post by zerobinary on 2007-10-06
Try using the a live cd and c if window xp and ubuntu is even installed the hdd
and post the image of it here

---

### Post by kirios on 2007-10-06
> **nameneeded said:**
> It looks like its going to install then I get a screen saying that it can't find any installed Hard Drives!

Now I know what you're thinking... Its cause the drive is formated for linux right? 

Wrong. I too thought of that and have tried after reformating it to bot Fat32 and NTFS to no avail.
[COLOR="DarkRed"]Did you reformat from the Ubuntu install or from Windows Setup?[/COLOR]

---

### Post by bubbalouie on 2007-10-06
See if you can get a newer OEM CD (sadly I find even OEM CD's don't always accept the code that comes with a computer :( , but it will help diagnose the issue, then you can contact Gateway for a CD that will accept your XP license code), it may be that your CD has no SATA support.

---

### Post by 22bsti on 2007-10-07
what laptop is it?  many newer laptops have chipsets with sata controllers that were developed/released after xp came out and thus the drivers required to detect/use them are not on the original install media.  I had this same issue with my MSI PR-200 it has a newfangled intel 965GM (aka santa rosa) chipset and the required sata drivers were not present on the install media, i ended up having to "slipstream" the required drivers into the disc.  This has the added benefit of allowing you to remove much unnecessary crap that ms thinks that everyone needs, but thats another rant.  If you provide more info mysellf or others here may be able to help, or direct you to where you could recieve help.

---

### Post by bodhi.zazen on 2007-10-07
Ouch ....

Unfortunately Windows is not always so easy to install.  See if your restore CD/Software has any drivers, you may need to install them first. 

If all else fails, contact Gateway

---

### Post by justinmiller87 on 2007-10-07
> **bodhi.zazen said:**
> If all else fails, contact Gateway

Probably no dice there. If I remember right from a Slashdot article a month or two back, they consider putting anything but what was on there originally a void of the warranty. I think the article said they wouldn't replace the hinge on a laptop because it had Linux installed on it.

---

### Post by bodhi.zazen on 2007-10-07
> **justinmiller87 said:**
> Probably no dice there. If I remember right from a Slashdot article a month or two back, they consider putting anything but what was on there originally a void of the warranty. I think the article said they wouldn't replace the hinge on a laptop because it had Linux installed on it.

Well, don't tell them that you installed Linux then, tell 'em you need to re-install because of a virus ...

---

### Post by mivo on 2007-10-07
> **justinmiller87 said:**
> Probably no dice there. If I remember right from a Slashdot article a month or two back, they consider putting anything but what was on there originally a void of the warranty. I think the article said they wouldn't replace the hinge on a laptop because it had Linux installed on it.

I don't see how that would hold up legally, though. But as bodhi said, they don't have to know that Linux was on the machine (that is not the reason for the trouble anyway). Just had a virus and had to reformat the disk.

---

### Post by misfitpierce on 2007-10-07
> **harbdog said:**
> XP is telling you that you're better off not installing it :popcorn:



if all else fails, grab VMWare Server and create a new XP image for you windows needs

Exactly :)

---

### Post by leg on 2007-10-07
And yet all you hear from Windows fans is how easy it is to install Windows. Usually from people that have never actually had to do it. Could this be anything to do with the mbr record I have had a problem with that once or twice.

---

### Post by nameneeded on 2007-10-07
WOW!

So many responses in so little time! Well here's whats been done thus far.

1) Tried instal with Ubuntu still on drive. Result... "No hard drive detected."

1a) for a couple of tries it said MBR error but that went away after reformat.

2) Reformated drive with partion magic to NTTS. Result...No Hard Drive detected.

3) Reformatted to Fat32. Result...Same as above.

4) Did kill and fill of hard drive. Result... same as above.

5) Purchased brand new un opened Hard drive. Tried to install XP. Result...Same as above.

6) Put old Hard Drive back in. Reset MBR to 0. Tried to install XP. Result... Same as above.

In all senarios I could install any linux distro with no problems.

If this is a driver issue for my Hard Drive how can I fix that? I have my doubts on that being the issue as my recovery CDs came with my puter always fail.

My computer is a Gateway Tablet/Convertable CX2724

---

### Post by irish_flu on 2007-10-07
Is this a "PATA" (IDE) hard drive, or a newer SATA drive?

---

### Post by bodhi.zazen on 2007-10-07
> **nameneeded said:**
> WOW!

So many responses in so little time! Well here's whats been done thus far.

1) Tried instal with Ubuntu still on drive. Result... "No hard drive detected."

1a) for a couple of tries it said MBR error but that went away after reformat.

2) Reformated drive with partion magic to NTTS. Result...No Hard Drive detected.

3) Reformatted to Fat32. Result...Same as above.

4) Did kill and fill of hard drive. Result... same as above.

5) Purchased brand new un opened Hard drive. Tried to install XP. Result...Same as above.

6) Put old Hard Drive back in. Reset MBR to 0. Tried to install XP. Result... Same as above.

In all senarios I could install any linux distro with no problems.

If this is a driver issue for my Hard Drive how can I fix that? I have my doubts on that being the issue as my recovery CDs came with my puter always fail.

My computer is a Gateway Tablet/Convertable CX2724

Well, it the hard drive works with Ubuntu ,but not windows, you are missing a windows driver. I have no idea which one, try looking at your restore CD for drivers or contact Gateway (you can search their web site for drivers). Hopefully there are instructions on to to use them.

You can also try to contact Microsoft or a Windows forum ...

---

### Post by specs10 on 2007-10-07
I don't think he's missing any drivers.  I think I had the same issue once.  If it's the same thing that happened to me, Windows just can't read your MBR.

there's a command you need to run from the recovery console when you boot from the windows disk.  I think it's "fixmbr" : [here's]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true") a link to MS's help thing about it.  it'll effectively wipe your disk since it'll totally rewrite your MBR.  give that a shot.

Oh, yeah.  and I think I used "fixboot" at the same time.  just FYI.

---

### Post by nameneeded on 2007-10-07
> **irish_flu said:**
> Is this a "PATA" (IDE) hard drive, or a newer SATA drive?

Its a SATA drive.




> **specs10 said:**
> I don't think he's missing any drivers.  I think I had the same issue once.  If it's the same thing that happened to me, Windows just can't read your MBR.

there's a command you need to run from the recovery console when you boot from the windows disk.  I think it's "fixmbr" : [here's]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true") a link to MS's help thing about it.  it'll effectively wipe your disk since it'll totally rewrite your MBR.  give that a shot.

Oh, yeah.  and I think I used "fixboot" at the same time.  just FYI.


I have no options with my recovery CD's. It asks me to hit 'R' to start recovery then it goes through the motions then fails.

I'm gonna check out the link you posted. But I have already reet the MBR to 0 with no effect.

---

### Post by Cannaregio on 2007-10-07
> So in light of the problems I'm having with Ubuntu I decided to unistale it and go back to XP on my Gateway Tablet. Thinking of puting Ubuntu back on as a dual boot to use when I need a reason to get stressed.

I would say that in light of the problem you are having with XP right now, you should reconsider your move.


> **nameneeded said:**
> Well here's whats been done thus far.

1) Tried instal with Ubuntu still on drive. Result... "No hard drive detected."

1a) for a couple of tries it said MBR error but that went away after reformat.

2) Reformated drive with partion magic to NTTS. Result...No Hard Drive detected.

3) Reformatted to Fat32. Result...Same as above.

4) Did kill and fill of hard drive. Result... same as above.

5) Purchased brand new un opened Hard drive. Tried to install XP. Result...Same as above.

6) Put old Hard Drive back in. Reset MBR to 0. Tried to install XP. Result... Same as above.

In all senarios I could install any linux distro with no problems.

If this is a driver issue for my Hard Drive how can I fix that? I have my doubts on that being the issue as my recovery CDs came with my puter always fail.

My computer is a Gateway Tablet/Convertable CX2724


It indeed looks like your windows is telling you "no, no,no".

This said, I have a 'desperate' suggestion for you, though:
[supergrub disk + AIO (small AIO)]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by kirios on 2007-10-07
> **nameneeded said:**
> I have no options with my recovery CD's. It asks me to hit 'R' to start recovery then it goes through the motions then fails. 
[COLOR="DarkRed"]A lot of Windows sytems come with a hidden partition containing drivers. Could you have deleted this partition by mistake?[/COLOR]

---

### Post by Malibu Illusion on 2007-10-07
Sorry, but this sounds to me like it is entirely a driver issue.

Windows XP does not have support for some SATA/SCSI and RAID setups.  They require third party drivers to install.  In order to install these third party drivers, you will see an option to press one of the function keys during the installation process in order to load drivers from a floppy disk drive.  From the information that you have provided to us, it seems to me like that is the case. 

You will need to acquire the necessary drivers for your drive and load them from a floppy during the XP installation process.  After doing so, the XP installer will be able to see your drive and you should be able to continue as normal.

I suggest you look into this and seek further information, and the drivers themselves, by searching for your make of drive in Google and looking at the manufacturer's website.

Take care.

---

### Post by Ub1476 on 2007-10-07
[Install Windows XP on SATA without a Floppy (F6)]("http://www.community.probz.com/index.php?showtopic=1346")

---

### Post by pat888 on 2007-10-07
I think I have had the same problem in the past and got round it by deleting all partitions on the drive using a live cd. This was with an IDE drive.

---

### Post by trippinnik on 2007-10-07
I bet if you told us the model of computer we can find out if it's SATA or IDE.  That'd help a lot as far as narrowing doown the problem.

---

### Post by justinmiller87 on 2007-10-07
> **trippinnik said:**
> I bet if you told us the model of computer we can find out if it's SATA or IDE.  That'd help a lot as far as narrowing doown the problem.
It was already stated that it was a SATA.

---

### Post by nameneeded on 2007-10-08
K, 

Here's an update. One of the guys at memoryexpress (great store I buy my hardware from... check em out @ .com) figured its a driver issue or that my system had a hidden partion that the recovery discs needed to work properly.

Same as what the boards (you guys) were saying when I got home.

So I called gateway. I wasn't counting on much help from them as my puter is not only a year old but also was a refurbished unit.

Man was I surprised. The guy (Mike) was on the phone with me for over n hour. They figure its a driver issue. The problem was that there was a partion on the drive that directs the recovery CDs what to do. Since tats gone I'm a bit hosed. 

We figured out my systems exact specs (serial number worn away) and got the the driver page from gateway. So I need to figure out how to install drivers on a harddrive with no OS.

Thats the plan now.

Back up plan. I bought an OEM copy of Vista Premium. ($129) So I can try that if this fails. My fear is that it won't have the drivers needed just like my XP disc. Mike even suspected that same thing. So once its opened I cn't return it.

I really don't want to do that.

So Driver installing it is.

I'll post how I made out. If anyone knows an easy way to do this on a laptop withour a floppy pleae let me know.

Things I have available. 2 XP puters, 4 external HD's, 1GB USB Key and a couple hundred discs. 

PS Thanks for all the help and insights people! It was a real help not only for ideas but also to know I am doing the right things to solve this problem.

---

### Post by winsur8 on 2007-10-10
You might check in to the master boot record.  I believe i've had that problem before.  I think the command is  with in fdisk. maybe fdisk /mbr  

Good Luck

---

### Post by nameneeded on 2007-10-10
Update.

I borrowed a usb floppy. I downloaded the driver for the HDD. I ran my recovery disc. Hit F6 to let it know I had a driver. It let me use said driver...... and...... and .....

FAILED.

So I ran my XP disc. Hit F6 to let it know I had a driver. It to let me use my new driver........ and.......and.....

FAILED.

Same response "unable to locate HDD"

I don't know what to do now cept bring it in to get "fixed" at the place I bought it. 

I am unsure how the MBR could be the problem as I have reset it to 0.

I'm at a loss.

---

### Post by stchman on 2007-10-10
> **nameneeded said:**
> So in light of the problems I'm having with Ubuntu I decided to unistale it and go back to XP on my Gateway Tablet. Thinking of puting Ubuntu back on as a dual boot to use when I need a reason to get stressed.

S I go to install XP using my recovery discs.... no dice. Says Recovery failed and won't give options for a clean reinstal.

"Strange" I thought. but OK maybe they aren't meant for that. So I pull out my XP Pro disc I have. Figure I can call MS after to gewt the proiper codes and such.

It looks like its going to install then I get a screen saying that it can't find any installed Hard Drives!

Now I know what you're thinking... Its cause the drive is formated for linux right? 

Wrong. I too thought of that and have tried after reformating it to bot Fat32 and NTFS to no avail. 

I even bought a new HD and got the same results! 

And whats even weirder is that I can install any linux distro no problem!

Any ideas? I am not a computer geek. More computer friendly. I was told it could be my CMOS settings but have no clue what to do about that.

Your problem is most likely that you have a SATA hdd and XP install needs the drivers.  XP has big issues with SATA drives.  Remember the F6 when you are installing, you need that.

Stick with Ubuntu.

See Windows is not easier that Linux.  You said "I can install any Linux distro".

---

### Post by nameneeded on 2007-10-11
Ok update.

Got XP to use the drivers I had... then it asked me for another  driver (intel matrix controller) which I had... BUT  it wouldn't access the usb floppy to grab it.

So now I have Vista Prem. Loaded with no probs.

Next set up dual boot then I can continue the headache that is Ubuntu on a Tablet while haveing a usable tablet.

:guitar:


PS thanks for the assissts people... I hope your all there with my next one!

PEACE!

---

### Post by justinmiller87 on 2007-10-11
I'm sorry you have to use Vista, but I'm glad you were at least able to get it to work. I don't even remember if I offered you any advice in this thread, but if I did, I hope it helped. I have wicked terrible ADD sometimes. :)

---

