---
title: "Must be run as root? ERROR during instal...HELP please"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-03-28
OK. I'm trying to install Nvidia drivers. I exit the GDM, then when in the console I run...

sh ~/Desktop/NVIDIA-Linux-x86 yada yada, and the installer starts fine! but then I get an error "Must be run in root" or "as root". I tried doing CD ~/Desktop then the Nvidia script, and the same thing happened.

Any ideas? what I"m doing wrong? Thanks](*,)

---

### Post by Zeroangel on 2006-03-28
[quote=gordong11]OK. I'm trying to install Nvidia drivers. I exit the GDM, then when in the console I run...

sh ~/Desktop/NVIDIA-Linux-x86 yada yada, and the installer starts fine! but then I get an error "Must be run in root" or "as root". I tried doing CD ~/Desktop then the Nvidia script, and the same thing happened.

Any ideas? what I"m doing wrong? Thanks](*,)[/quote]
The command should look like this:

**sudo** ~/Desktop/Nvidia-Linux-x86 yada yada

---

### Post by dermotti on 2006-03-28
um, why don;t you install the nvidia driver ubuntu provides? 

**sudo apt-get nvidia-glx**

quite a bit easier.

---

### Post by gordong11 on 2006-03-28
Both DID NOT work!

I need latest Nvidia drivers because, I need to install the forceware as well. I am getting no sound out of my mobo...not even recognizing the onboard sound device. I was told I need both.

Sudo ~/Desktop/NVIDIA-Linux-x86-1.0-8178-pkg1.run...didnt work, invalid directory.

Except I am having terrible trouble running them. Both are saved to the desktop, bot get the error "Must be run as root". Sudo did not work.

for nvidia-glx ...I get invalid operation, in the Terminal anyway...nothing outside the gdm.

---

### Post by aysiu on 2006-03-28
[QUOTE=gordong11]Both DID NOT work!

Sudo did not work.[/QUOTE] Can you be more specific about what didn't work? What was the error message? Did you do an expert install? That's the only thing I can think of that would be preventing you from doing *sudo*.

---

### Post by gordong11 on 2006-03-28
OK.

I'm starting the terminal, and doing Sudo /etc/init.d/gdm stop

then

I'm in the console outside Gnome, admin is my username. I then type:
sh ~/Desktop/NVIDIA-Linux-x86-1.0-8178-pkg1.run

then the Nvidia installer begins.....the screens switches to an Nvidia install screen, then I get the error "must be run as root"...only choice is to press "OK" and it takes me back to the console. If I run the same script with Sudo, I get "invalid directory" or something.

Now if I log into the console as root, neither work....nor does CD ~/Desktop/

This is what is killing me. I have been following the instructions at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#HOWTO:_Latest_NVIDIA_drivers](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#HOWTO:_Latest_NVIDIA_drivers)

Way number 2. since I'm running breezy no need to patch. I have also tried and succeed at extraction (step 8 then type to Install the driver:

sudo ./nvidia-installer -n --x-prefix=/usr/lib/xorg/

That does not work either. That is where I am at in a nutshell. 

This seems like it should be easy, but it is killing me ](*,) 

Is it possible to make boot CD/DVD and install that way?

Thanks for the help

---

### Post by aysiu on 2006-03-28
This method has always worked for me--it appears to be a slightly different take on "method 1":

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by gordong11 on 2006-03-28
That may work......but my main issue, why I'm going through with this, is that I have no sound at all. I was told I need Nvidia Forceware for my Gigabyte GA-K8N51GMF mobo. Ubuntu is not recognizing my onboard sound. I get the same error for Forceware install (needs to be run as root).

Thanks...If all ealse fails I"ll install a PCI sound card, but dont have the $$ right now.

---

