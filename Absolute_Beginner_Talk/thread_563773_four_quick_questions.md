---
title: "four quick questions"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by AnimateDeath on 2007-09-30
I have a few general questions (please remember that I am completely new to linux so some of these questions might be super simple but I have no idea about them).

First question: I have Ubuntu installed on a 120gb partition and the swap partition is on a 20gb. Is that way to big for a swap partition? If it is, about what size should the swap be, and is there a way to change that swap partition size down and add it to the main partition for Ubuntu?

Second question:  Everything in my Ubuntu 7.10 install is running perfectly. Looking through the Synaptics Package Manager, I see some things that I would like to install, but they want to install other compenents with them. Could installing these additional components hurt anything on my install? For instance, I want to use Amarok but it wants to install some packages that I can tell by the "K" in front of the names belong to the KDE desktop, but I use Gnome. Could there be problems there?

Third question (also package manager), :  Let's say that I just start going through SPM and selecting things that I want to install. Like A LOT of things, Things that I don't even know what do, but want to try them out anyway. Will things that I install from the package manager mess up any of the core files for my install making it non-functional? Like if I use a program that needs a package called Thingy1.2.2, and I want to install a package that needs KThingy1.2.2, will that mess anything up?

And finally (for now) :  Does Ubuntu have a backup and restore function like windows does? I would like to get everything installed and working perfectly, including the workaround that I have to do for my sound, and then back everything up, including installed progs, and pictures, and music. And then if I screw something up, I can just use that backup to restore everything to where it was?    I guess this last one is pretty important to me for now since I screw up my installs a lot  LOL

---

### Post by n3tfury on 2007-09-30
> **AnimateDeath said:**
> I have a few general questions (please remember that I am completely new to linux so some of these questions might be super simple but I have no idea about them).

First question: I have Ubuntu installed on a 120gb partition and the swap partition is on a 20gb. Is that way to big for a swap partition? If it is, about what size should the swap be, and is there a way to change that swap partition size down and add it to the main partition for Ubuntu?

[COLOR="Red"]that's way too big.  it used to be preferred to have 2x your RAM, but that was before 2GB was almost standard, so it kind of depends on how much RAM you have.  i have 2GB of RAM, but only have a 1GB partition that never gets used.  and burn the gparted iso and you can trim that swap partition down.[/COLOR]

Second question:  Everything in my Ubuntu 7.10 install is running perfectly. Looking through the Synaptics Package Manager, I see some things that I would like to install, but they want to install other compenents with them. Could installing these additional components hurt anything on my install? For instance, I want to use Amarok but it wants to install some packages that I can tell by the "K" in front of the names belong to the KDE desktop, but I use Gnome. Could there be problems there?

[COLOR="Red"]install everything it asks to install with it.  these are i believe what they call dependencies.  you shouldn't run into any conflicts.  this applies to the question below too.  install what you want and uninstall the same way if you don't want it anymore.  try stuff out for free, that's the beauty of it![/COLOR]

Third question (also package manager), :  Let's say that I just start going through SPM and selecting things that I want to install. Like A LOT of things, Things that I don't even know what do, but want to try them out anyway. Will things that I install from the package manager mess up any of the core files for my install making it non-functional? Like if I use a program that needs a package called Thingy1.2.2, and I want to install a package that needs KThingy1.2.2, will that mess anything up?

And finally (for now) :  Does Ubuntu have a backup and restore function like windows does? I would like to get everything installed and working perfectly, including the workaround that I have to do for my sound, and then back everything up, including installed progs, and pictures, and music. And then if I screw something up, I can just use that backup to restore everything to where it was?    I guess this last one is pretty important to me for now since I screw up my installs a lot  LOL

it doesn't by default, but i think people suggest making a seperate /home partition so when you upgrade or reinstall, /home doesn't get touched.

---

### Post by Sunforge on 2007-09-30
A 20 Gb partition for swap is a little on the large side. The general rule of thumb is that swap should be twice the size of your RAM but (in my observation), on systems with 2 Gb of RAM or more, it's unlikely you're ever going to use your swap space at all; unless you're hibernating or you want to get to your crash dump files. There is an official Ubuntu guide to swap here:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

You can install KDE apps in Gnome, although your mileage might vary from app to app. Here's a link to a very similar post on the subject:

[http://ubuntuforums.org/showthread.php?t=285717](http://ubuntuforums.org/showthread.php?t=285717)

Synaptic is pretty good at ensuring that you get no conflicts when installing. What may happen is that you select programme X and Y and Synaptic automatically selects programme or library Z for de-installation. When you hit the "Apply" button everything should happen automagically. 

Ubuntu doesn't come with a built in backup system, although the safest thing you can do is ensure that you copy your home folder to another partition/drive/server/planet just in case, or put your /home folder on a different drive so that you can re-install without upsetting your accumulated files.

---

### Post by AnimateDeath on 2007-09-30
> **n3tfury said:**
> it doesn't by default, but i think people suggest making a seperate /home partition so when you upgrade or reinstall, /home doesn't get touched.

So then what would I do to get the /home partition back to being the main partition so that it is used? Do I just rename it to something? Please explain, I am so new to linux it is pathetic.

and thanks for the answers to the other questions.

wait: I see, so I would then just copy the /home partition back in to the fresh install of ubuntu??  but will that make all the programs that I have installed still work?

Maybe I should change that question. Can I just copy my entire installed ubuntu partition in to another partition fo backup and then if something happens, change that backup partition to being the one used? If so how would I do that?

---

### Post by n3tfury on 2007-09-30
> **AnimateDeath said:**
> So then what would I do to get the /home partition back to being the main partition so that it is used? Do I just rename it to something? Please explain, I am so new to linux it is pathetic.

and thanks for the answers to the other questions.

wait: I see, so I would then just copy the /home partition back in to the fresh install of ubuntu??  but will that make all the programs that I have installed still work?

Maybe I should change that question. Can I just copy my entire installed ubuntu partition in to another partition fo backup and then if something happens, change that backup partition to being the one used? If so how would I do that?

you'll have to wait for someone more knowledgeable about that one, but a quick google should bring up the results you're looking for.  i don't do this myself :)  well, at least not yet.

---

### Post by AnimateDeath on 2007-09-30
Well, I did a little searching and came up with this thread about backing up the system and it works awesome.    [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I guess that answers that. :)

---

### Post by mlentink on 2007-09-30
You might want to have a look at sbackup, which I use and works like a charm. The method mentioned in the thread you listed has some drawbacks, as no doubt you will have read/discovered....

---

