---
title: "Totally lost"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Supavillain on 2006-08-17
I have a old windows 98 that I dont use that I want to try using ubuntu on...I tried running the disk and going through the steps and I kept getting errors at lots of the windows..so I figured that I need to totally reformat..which is what I want to do anyway..I thought with ubuntu you could reformat and install using the install disk...does anyone know how to reformat a win98?

---

### Post by Kobussie on 2006-08-17
What exactly do you mean with > a win98 ?

---

### Post by Supavillain on 2006-08-17
A Windows 98

I want to fully reformat a Windows 98 and install ubuntu

---

### Post by bodhi.zazen on 2006-08-17
Run GParted as root. Delete your win 98 partition. Make a swap and linux partiton. Install.

---

### Post by Kobussie on 2006-08-17
I assume you mean a P.C. with Windows 98 installed on it?
Try to tell more about the computer (how old, what processor etc)

---

### Post by ubuntu27 on 2006-08-17
If you do a default install, then all data on your hard drive will be deleted and replaced by the Ubuntu Linux Operating System.

The disk that you got. Is that a CD that came with [Shipit]("https://shipit.ubuntu.com/") or did you burned yourself?

If you burned it yourself, did you check that it is burned properly? Make sure you burned as an IMAGE.

[Here]("http://psychocats.net/ubuntu/iso.html") is a comprensible guide to burn a iso image. 

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

---

### Post by Bakerconspiracy on 2006-08-17
First and formost im assuming when you say "a Windows 98" that you mean a hardrive that has windows98 installed on it. 

Yes you can format a hardrive with the ubuntu set up cd. What you want to do when you arrive to the Partitioning stage of the install is select the option of erasing your entire disk and use guided partitioning.

What particular windows is your machiene stalling at? (Do you have the i386 version of the distro?)

---

### Post by Markus Valkeapaa on 2006-08-17
> **Supavillain said:**
> A Windows 98

I want to fully reformat a Windows 98 and install ubuntu

During Ubuntu installation you'll be asked about the hard disk use. A new hard disk partition will be created according to your wishes. You can for example give all of the disk for Ubuntu, which means Windows98 will disappear. I take it you can run Ubuntu from the  liveCD?

-Markus

---

### Post by Supavillain on 2006-08-17
Ok I ran it all and got past the guided partioning..then it went into the base system and said 
"Cannot install base system"
THe installer cannot figure out how to install the base system, No installable cd rom was found and no valid mirror was configured"

The install disk is in though

---

### Post by Bakerconspiracy on 2006-08-17
Did you take the insallation step by step, it seems like some steps in the
install failed/were skipped or your disk integrity is bad.

---

### Post by Supavillain on 2006-08-17
Took it step for step..Ill go over it all over again and type all what I do in here..

step one : Language = English
step two : Location = Canada
step three : Keyboard = American English
step four : XXX

everything else automaticly sais "Base system doesnt work"

so I probably screwed up somewhere..

---

### Post by Supavillain on 2006-08-17
alright so I got a walkthrough and i got through a bit...I need to know either to pick 

erase entire disk : IDE1 master (hda) - 13.7 GB FUJITSU
erase entire disk and use LVM : etc etc

---

### Post by Supavillain on 2006-08-17
ok nevermind 
got through all that..its installing base system and I have a stinky feelings its not going to work

I followed the instructions word for word...what could be wrong?

---

### Post by syedn on 2006-08-17
If its now installin the base system what makes you afraid it isn't going to work?

---

### Post by Bloch on 2006-08-17
You say it's an old computer. Ubuntu won't be very fast on it if it has less than 256MB ram and maybe a 800MHz PIII

But it will be good enough to test it and you can install the xubuntu desktop which will be a little quicker. (the defaul;t is the gnome desktop)

Let us know how it installed

---

### Post by Supavillain on 2006-08-17
Ok I just tried restarting my computer normally without the disk in so I could try the other "live" disk ..and it wont start up..it just comes to a black screen

ugh..

---

### Post by Bloch on 2006-08-17
Give us the specs of your machine. 
The live disk might not work at all with less than 128MB ram.

Do you mean you were installing from the "alternate install" disk - the one that begins immediately with installing ubuntu?
What happened? You said it was installing the base system a few minutes ago.

---

### Post by Supavillain on 2006-08-17
yea It was installing then it said it failed and it gave me the same error message I posted before

Im redoing it again now

right now im at the network part, its not hooked up to the internet so im choosing "do not configure the network at this time"

chose host name

now its detecting disks

and now im given the choice to erase entire disk
or erase entire disk and use LVM
or do it manually (which I think I earlier did by mistake and F*ucked it up..)

---

### Post by Supavillain on 2006-08-17
ok I went to manual and this is what it sais right now


"#1 primary  13.5 GB (wierd crooked down symbol) (smiley face) ext 3 /media/hda1

#5 logical 180.9 MB (wierd looking guy) swap  swap

---

### Post by Bloch on 2006-08-17
Go for it.

As far as I remember ubuntu installs twice as much swap as you have ram.
This means you possibly have 90MB ram. Is that true?

You will need xubuntu, but the standard desktop should start - but slowly.

---

### Post by Supavillain on 2006-08-17
ugh im just gonna wing this..I screwed up the whole swap thing..I dont know what It should look like..Im just gonna erase it all and I dunno
lol

---

### Post by Supavillain on 2006-08-17
I know what the problem is now..its the whole swap and partition thing..can anyone walk me through how to do it manually?

---

### Post by Bloch on 2006-08-17
It's been a while since I installed I'm afraid. 

But why don't you choose the "erase entire disk" option and let the installer choose the partitions?
Your previous attempts to  install might have created partitions and now it will try to install into these paritions etc.
Better start from scratch

---

### Post by Supavillain on 2006-08-17
When I choose that, it still messes up..Ill try again..

---

### Post by Supavillain on 2006-08-17
Its back to the install base system

but I bet It wont work again..and I have no clue why

---

### Post by Bloch on 2006-08-17
I remember seeing a computer running windows 98 on only 32MB of ram. It is possible you have too little ram. Even 64MB is too little, though the installation at least should work.

I remember I got that error message about the base system. I had a corrupt disk - I burned it at too high a speed.

---

### Post by Supavillain on 2006-08-17
This is a legit version..

heres the error message I got


"kernel package: 'linux-386'
Check /target/var/log/bootstrap.log for the details

---

### Post by Bloch on 2006-08-17
You say you have a "legit" disk - ubuntu is free for anyone to copy. Do you mean you applied and got the ubuntu disk from "Shipit"?
Is it the "alternative-install" disk? It seems to be because it goes straight into attempting to install ubuntu.

The live-install disk boots into ubuntu from the cd so you can try it out, and then permanatly install it by clicking an icon on the desktop.

You say you are installing but the system seesm to already have linux on it if it is writing files to
/target/var/log/bootstrap.log

How far did the installation get? Did you ever boot the computer into ubuntu? Did you ever boot as far as a command line 
supavillain@mycomputer:~$

Anyone any ideas??

---

### Post by cjssmo on 2006-08-17
I understand this is an ubuntu forum but it sounds like you old computer dosn't have the spec's needed to run it soooo here is an alternative that should work.  Dawm Small Linux.  It is 50mb is size and is easy to install on older equipment.  It comes in a live cd format but you can install it to your hard drive and have a debian like system or you can run it from ram (to do this i think it requires 128mb ram) or you can run it from a pin drive.  Basically it is pretty versitile and the selling point for me is that it works well on older computers I currently have Ubuntu on my main computer but I have Dawm Small Linux on a pasario 450mhz processor, 64mb Ram and a 10gb HD, that my kids use.  Dawm Small Linux on the pasario is just about as fast as my main computer which is running a amd 2800.  Give it a try

---

