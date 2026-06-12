---
title: "about DEB packages and dependencies"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by mental_noise on 2006-01-17
hello all!  i am relatively new to linux and i would like to ask how to install DEB packages and also know more about so called "dependencies".

here's what i want to do:

i have an old PC (PII 400MHz) and i want to use it as my learning ground for linux. i just got my copy of ubuntu 5.10 and only did a [FONT="Courier New"]server[/FONT] install. i found links on how to setup an ubuntu box for minimal PCs (see [[here]]("https://wiki.ubuntu.com/Installation/LowMemorySystems") ). i am now very interested to use fluxbox as my window manager. the wiki explains that to do this, just issue the command

[FONT="Courier New"]sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic[/FONT]

and it will be installed. the problem is, my old PC doesn't have internet connection and AFAIK, [FONT="Courier New"]apt-get[/FONT] needs an internet connection.

so, i thought that if i just downloaded the DEB packages of [fluxbox]("http://logicvortex.net/debian/fluxbox/") (and others), i could install it manually. i went to [debian.org]("http://www.debian.org") and read how to install DEB packages and that is when i encountered the dependencies.

question: does the .deb package i downloaded for fluxbox contain all the dependencies or do i need to download all the dependencies it needs so that it will be installed properly?

---

### Post by aysiu on 2006-01-17
This may help:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by mental_noise on 2006-01-17
[QUOTE=aysiu]This may help:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)[/QUOTE]
interesting link! :smile: 

and thank you for the quick reply but unfortunately the other PC is use to download these .deb packages is in WinXP so i cannot get it that way. :(

---

### Post by Limulus on 2006-01-17
mental_noise: I'll work on a longer reply in a sec, but basically:

- without all its dependencies, a given package likely won't work
- the fluxbox link in your post doesn't work
- you should get those DEBs from Ubuntu, not other sources
- dependencies are just other packages; the fluxbox package does not contain them

---

### Post by Limulus on 2006-01-17
(another short reply)

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) has all the information on Ubuntu packages (e.g. [fluxbox](http://packages.ubuntu.com/breezy/x11/fluxbox)) and you can download them from there too.

What you'll need to do is download all the packages that aren't already installed, transfer them to the old computer and run *sudo dpkg -i *.deb* in the directory where you put them.

---

### Post by mental_noise on 2006-01-17
[QUOTE=Limulus]...
- the fluxbox link in your post doesn't work
- you should get those DEBs from Ubuntu, not other sources[/QUOTE]
sorry about the link but that is what appears when i click the download link at [fluxbox.org]("http://fluxbox.org/"). :smile: anyway, how do i download .deb packages manually from ubuntu?

[QUOTE=Limulus]- dependencies are just other packages; the fluxbox package does not contain them[/QUOTE]
just as i feared. :( so i need to [FONT="Courier New"]**dpkg -i**[/FONT] all those dependencies one-by-one then? which leaves me with another question, do i need to dpkg the main package (in this case, the fluxbox .deb) first or can i dpkg everything in any order? 

thanks!

---

### Post by Limulus on 2006-01-17
(yet another short reply)

You know, you could probably use an Ubuntu Live CD to download the packages on the XP computer

BTW, since fluxbox is in the Universe repository, you'll need to set up your sources list when using the Live CD; see [my site](http://members.shaw.ca/Limulus/ubuntu.html#SynTer) for more info on that...

>anyway, how do i download .deb packages manually from ubuntu?

if you want to do it that way (and it will take a long time, so you really might want to try the Live CD method), start with the fluxbox package link I gave you and scroll to the bottom to where it says "Download fluxbox" and click the platform your old computer runs on (most likely "i386"; Intel chips since 386) and you'll be given sites you can download the DEB from.  Then repeat that for each and every red dot package (pacakges on which it "depends") and continue the process for each of those packages, etc. until you have a complete set that requires no more packages.

>so i need to dpkg -i all those dependencies one-by-one then? which leaves me with another question, do i need to dpkg the main package (in this case, the fluxbox .deb) first or can i dpkg everything in any order?

You should really do them all at once actually.

---

### Post by mental_noise on 2006-01-17
> **Limulus]...

You know, you could probably use an Ubuntu Live CD to download the packages on the XP computer

BTW, since fluxbox is in the Universe repository, you'll need to set up your sources list when using the Live CD said:**
> my site[/url] for more info on that...

...

you really might want to try the Live CD method

...
this is great news indeed! thanks for your help. i will try this out ASAP and ask questions should the need arise.

thanks a lot! :D

---

### Post by Limulus on 2006-01-17
The thing with the Live CD though is that it presents its own challenges; off the top of my head, I don't know if its considered safe to write to NTFS partitions (that is to say, your Windows XP partition) with Breezy.  Also, unless you have both a CD-ROM and a CD-RW attached to your machine, you can't write to a CD from the same drive you're using the Live CD in ;)

Can you tell me more about your computer? (and note that I have to go to bed, so my apologies if I can't give much more tech support tonight)

---

### Post by Limulus on 2006-01-17
some pointers for when you run the Live CD:

It will behave just like a regular installation, but a bit slower.

apt (command line)/synaptic (Ubuntu) keeps its downloaded debs in /var/cache/apt/archives

*sudo apt-get clean* from Terminal (command line) will erase all debs from  there (e.g. if you want to start from scratch).

When you reboot, anything not saved from your Live CD session to a HD/CD, etc. will be lost.

I dunno exactly what packages are installed from the CD when doing a 'server' install; I should look into that to see if to install fluxbox maybe you only have to download a few...

---

### Post by mental_noise on 2006-01-17
@ Limulus:

i apologize for having replied just now and it's okay if you don't give tech support right away. you have helped me a lot and i won't deprive you of your sleep. hehe.

anyways, here are some info about my PC running on XP:
[INDENT]Processor: Pentium 4 - 1.80 GHz[/INDENT]
[INDENT]Memory(RAM): 256MB[/INDENT]
[INDENT]Video Card: GeForce MX 400 64 MB[/INDENT]
[INDENT]CD Drive: Enlight CD Writer - DVD rom combo[/INDENT]
[INDENT]Modem: D-Link DU-562M (USB)[/INDENT]

unfortunately, i only have one CD drive. but maybe i can use a Flash Disk instead of writing it to a CD? i sure hope so. :)

questions (yet again ... forgive my newbie-ness):
1) if i boot the live CD, will i be able to change the [FONT="Courier New"]**.../sources.list**[/FONT] and do an [FONT="Courier New"]**apt-get update**[/FONT] without the need of restarting?

2) if i successfully do an [FONT="Courier New"]**apt-get *<package name>***[/FONT], will i be able to get the packages and dependencies involved?

[QUOTE=Limulus]...

I dunno exactly what packages are installed from the CD when doing a 'server' install; I should look into that to see if to install fluxbox maybe you only have to download a few...[/QUOTE]
you read my mind here. i was supposed to ask you if (and how) i could check which packages are pre-installed during a [FONT="Courier New"]**server**[/FONT] install.

on a side note: will i be able to browse the net using the modem i specified above? i fear that it is a winmodem ... so i doubt that it will be detected by ubuntu.

thanks (once again) for teaching me and hopefully if i get it to work, i will blog about it and give you credits. ;)

---

### Post by Mustard on 2006-01-17
If you had a USB drive formatted with a FAT32 filesystem it would make life easier. :)  You could transfer to the USB drive and then mount it with your Ubuntu installation and transfer the files that way.

Any chance you could burn the packages to a CD from XP?  Then you could mount the CD via command line on ubuntu and transfer the packages over.

---

### Post by Limulus on 2006-01-17
[QUOTE=mental_noise]unfortunately, i only have one CD drive. but maybe i can use a Flash Disk instead of writing it to a CD? i sure hope so. :)[/QUOTE]

That would work, yes :) How big is it?

[QUOTE=mental_noise]1) if i boot the live CD, will i be able to change the [FONT="Courier New"]**.../sources.list**[/FONT] and do an [FONT="Courier New"]**apt-get update**[/FONT] without the need of restarting?[/QUOTE]

yes :)

[QUOTE=mental_noise]2) if i successfully do an [FONT="Courier New"]**apt-get *<package name>***[/FONT], will i be able to get the packages and dependencies involved?[/QUOTE]

you should be able to, though I don't know the exact command line instructions off the top of my head... (it wouldn't be hard to look up)

[QUOTE=mental_noise]on a side note: will i be able to browse the net using the modem i specified above? i fear that it is a winmodem ... so i doubt that it will be detected by ubuntu.[/QUOTE]

Are you in the UK? :) I didn't see it on the US site, but its on [http://www.dlink.co.uk](http://www.dlink.co.uk)

Hmm... That poses an interesting question; even if its fully supported by Ubuntu (because its USB external, I don't think its a winmodem; they usually don't have dedicated hardware), connecting with the server installation would be more tricky since its all command line...

Say, before we get too far down one track I want to try a little experiment with my Live CD... I'll put another comment here in a little bit...

---

### Post by mental_noise on 2006-01-17
[QUOTE=Limulus]That would work, yes :) How big is it?
...[/QUOTE]
the flash disk is 128MB in size. i hope this is enough. :)

---

### Post by Limulus on 2006-01-17
[QUOTE=mental_noise]the flash disk is 128MB in size. i hope this is enough. :)[/QUOTE]

Spiffy; the files (including every last recommended and suggested deb) are ~92 MB, but I have an easier suggestion for you since I don't know if you'll be able to get your modem working easily from the Live CD: if you'd like, go to my [contact page](http://members.shaw.ca/Limulus/contact.html) and send me an e-mail; I'll send you a gmail invite and once you get a gmail acct set up, I'll send the 92 MB of files there, from which you can easily d/l them into Windows and burn onto a CD or whatever :)

Now, if you'd prefer to do it the way I did it to get the files, here's how: I've devised a shell script (basically a batch file if you're used to DOS) that will run under a Breezy Live CD and put all the DEBs in a directory on the Live CD desktop :)  Here's the code:

```

wget http://members.shaw.ca/Limulus/files/basic_breezy_sources.list
sudo cp basic_breezy_sources.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wajig
sudo mkdir /mydebs
sudo mkdir /mydebs/archives
sudo mkdir /mydebs/archives/partial
sudo mkdir /mydebs/lists
sudo mkdir /mydebs/lists/partial
sudo touch /mydebs/status
sudo mv basic_breezy_sources.list /mydebs/sources.list
sudo apt-get update -o=Dir::Cache::archives=/mydebs/archives -o=Dir::State::status=/mydebs/status -o=Dir::State=/mydebs/ -o=Dir::Etc::sourcelist=/mydebs/sources.list
sudo wajig installrs -d -o=Dir::Cache::archives=/mydebs/archives -o=Dir::State::status=/mydebs/status -o=Dir::State=/mydebs/ -o=Dir::Etc::sourcelist=/mydebs/sources.list fluxbox x-window-system-core xdm dillo synaptic
mkdir ~/Desktop/DEBs
cp /mydebs/archives/*.deb ~/Desktop/DEBs

```

(based on [http://lists.debian.org/debian-isp/2003/11/msg00047.html](http://lists.debian.org/debian-isp/2003/11/msg00047.html) and [http://www.togaware.com/wajig/](http://www.togaware.com/wajig/))

What it does is it downloads a sources.list from my site, installs the wajig package (like apt-get, but can also grab recommended and suggested packages) and then gets all 330 packages needed for fluxbox, x-window-system-core, xdm, dillo and synaptic.  Now, you'll have some of those installed by default on a server setup, but I don't know which and since the Live CD doesn't emulate a server setup, so it will just be easier to grab them all.

To use it, you just save it to a file (e.g. "run.sh", say on the Live CD desktop), then run a Terminal window, *cd Desktop* then *sudo bash run.sh* and except for two yes/no questions (do you want to download wajig and then do you want to download the 330 files) its fully automatic.  From there, just save them onto your flash drive and take them back to windows for burning.

So your choice ^_^

---

### Post by Limulus on 2006-01-17
Regardless of what method you chose for getting the files, once you have them transferred to the old computer, a slightly modified version of the instructions on [this page](http://techpatterns.com/forums/about349.html) will let you use apt to install everything nicely :)

```
cd /home/username/downloads/debs
```(note: change to your deb directory path)

```
mkdir binary
mv *.deb binary
dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
sudo nano /etc/apt/sources.list
```

Add the line:
```
deb file:/home/username/downloads/debs/binary/ ./
```(note: change to correct path. Also, there is a space between /binary/ and ./)

```
sudo apt-get update
```

And then you'll be able to install the packages you want:

```
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic
```

Plus when you're in Fluxbox and running Synaptic, all the suggested and recommended packages will be available.

---

### Post by mental_noise on 2006-01-19
> **Limulus]Spiffy said:**
> 
exactly what i was trying to do ... i don't know how to dial-up using the live cd. :mrgreen: 

[QUOTE=Limulus]if you'd like, go to my [contact page](http://members.shaw.ca/Limulus/contact.html) and send me an e-mail; I'll send you a gmail invite and once you get a gmail acct set up, I'll send the 92 MB of files there, from which you can easily d/l them into Windows and burn onto a CD or whatever :)
...
cool! i already have a gmail account and its **mental.noise *at* gmail *dot* com**.

i can't thank you enough for the help you've been giving me and i am sorry that i replied just now since i was caught up with some deadlines at work. :) 

i would also like to try the other method using the shell script but i don't know how i could dial-up using the breezy live cd and i don't even know if my modem was detected. :)

---

### Post by mental_noise on 2006-01-24
[QUOTE=Limulus]...
```
mkdir binary
mv *.deb binary
dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
sudo nano /etc/apt/sources.list
```
...[/QUOTE]
hello Limulus. i managed to copy the deb packages you sent to me through mail (thank you for that!) to my old PC and as i was going about the quoted procedure above, but when i do

```
dpkg -scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
```

i get the error

```
dpkg: conflicting actions --contents and --status
```

i would really appreciate your help on this. thanks! :smile:

---

### Post by Limulus on 2006-01-24
[QUOTE=mental_noise]hello Limulus. i managed to copy the deb packages you sent to me through mail (thank you for that!) to my old PC and as i was going about the quoted procedure above, but when i do

```
dpkg -scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
```

i get the error

```
dpkg: conflicting actions --contents and --status
```

i would really appreciate your help on this. thanks! :smile:[/QUOTE]
Hmm... I have no idea ^^;  I just tried it again on my system and it worked. *shrug*  But fear not; in the "Ubuntu help is on the way! ^_^" e-mail I sent you, I had attached a copy of the Packages.gz file my computer produced.  It should work just as well for you.  Just drop it in the same directory as the DEBs and then continue to the next instruction on the list (sudo nano /etc/apt/sources.list)

---

### Post by mental_noise on 2006-01-24
oh yeah, one quick question. which one is correct?

A) [FONT="Courier New"][SIZE="2"]**dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz**[/SIZE][/FONT]
*(no space in between [FONT="Courier New"][SIZE="2"]**dpkg-scanpackages**[/SIZE][/FONT])*

or

B) [FONT="Courier New"][SIZE="2"]**dpkg -scanpackages binary /dev/null | gzip -9c > binary/Packages.gz**[/SIZE][/FONT]
*(with space in between [FONT="Courier New"][SIZE="2"]**dpkg -scanpackages**[/SIZE][/FONT])*

if it is A), i get a bash error: dpkg-scanpackages saying it doesn't exist or something like that. but if B), i get the error [FONT="Courier New"]**dpkg: conflicting actions --contents and --status**[/FONT]

thanks!

---

### Post by Limulus on 2006-01-24
[QUOTE=mental_noise]oh yeah, one quick question. which one is correct?

A) [FONT="Courier New"][SIZE="2"]**dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz**[/SIZE][/FONT]
*(no space in between [FONT="Courier New"][SIZE="2"]**dpkg-scanpackages**[/SIZE][/FONT])*

or

B) [FONT="Courier New"][SIZE="2"]**dpkg -scanpackages binary /dev/null | gzip -9c > binary/Packages.gz**[/SIZE][/FONT]
*(with space in between [FONT="Courier New"][SIZE="2"]**dpkg -scanpackages**[/SIZE][/FONT])*

if it is A), i get a bash error: dpkg-scanpackages saying it doesn't exist or something like that. but if B), i get the error [FONT="Courier New"]**dpkg: conflicting actions --contents and --status**[/FONT]
[/QUOTE]
Hey, I was able to reproduce your error message! :)

You're right, there's **no** space.  OK, so that means you need another package to make it work...  Just give me a few min to figure out what that is.

Edit: Its dpkg-dev; it has a whole bunch of dependencies though, so you'd probably do best using my copy of Packages.gz

---

### Post by mental_noise on 2006-01-25
ok, i was able to install the packages last night. there were a few corrections i made to /etc/apt/sources.list though. instead of:

```
deb file:/home/username/downloads/debs/binary/ ./
```

i changed it to

```
deb file:///home/username/downloads/debs binary/
```

because when i do the former, it will give me an error *"cannot install file:/home/username/downlaods/debs/binary/binary/<package>.deb. file not found"* or something like that.

thanks a bunch Limulus for your extended help on this matter. :)

i will be asking more questions later. right now, i must get to work. :D 

[QUOTE=Limulus]...
Edit: Its dpkg-dev; it has a whole bunch of dependencies though, so you'd probably do best using my copy of Packages.gz[/QUOTE]

for some reason, i was able to install dpkg-dev off of the ubuntu install CD. also with x-window-system-core since it won't install it using the downloaded deb packages. :rolleyes:

---

