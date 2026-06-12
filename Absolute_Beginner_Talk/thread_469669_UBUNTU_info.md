---
title: "UBUNTU? info"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by SUIHARA on 2007-06-10
ok iam thinking about making the change to ubuntu since vista well... sucks

and i have a few things to ask...


what is diff from  kubuntu,ubuntu,dapper ect

iam getting a cd sent from the sendit or sumthing but i have a version 5 or sumthing from my friend if i install the disk i have can i just run the new one when it gets here and it will update .. or to i have to format all?

ok so i know about wine or what ever its called and well i want to know abotu programs i use will wine run.
adobe premiere pro 7 & photoshop cs2
msn msg/windows live msg
nero
VDUB Mod

also will ubuntu work with my modem .. the box says it does work with linux but iam not 100% sure

and the sudu stuff i dont fully understand

---

### Post by AAM on 2007-06-10
Basically:
1. name set #1 deals with desktop used - Ubuntu [GNOME], Kubuntu [KDE], Xubuntu [Xfce], Edubuntu [GNOME with education apps]
2. name set #2 deals with version, follows a two word alliteration name - Dapper Drake  6.06 [released 06/2006], Edgy Eft 6.10 [released 10/2006], Feisty Fawn 7.04 [released 04/2007]
3. WINE runs programs - check with winehq for what will run. MSN is not needed as the Linux natives Kopete and GAIM achieve the same things. Nero also is a pale comparison to K3B. I am fairly sure that some versions of Photoshop run but if you wish there is a very good alternative in GIMP (but most Photoshoprers don't seem to like it as an alternative). Don't know what VDUB Mod unless its a 'modified Volkswagen', but that's unlikely on a computer site!

As for the question about Ubuntu version 5 (Breezy Badger?), it will give you some idea but there have been quite a few advances since then. If your hardware is very new, that version may not actually recognise the hardware. Certainly use the LiveCD to get a view of what its like.

Issue of modem depends on what type it is. If it is a winmodem - it's tough! Linuxant.com have commercial drivers available that do work and are cheap. If you have a proper modem then I understand that they work very easily - plug and go kind of thing. I am speaking from reputation here as I got broadband about the same time as I also got a proper modem! I did manage a winmodem with Linuxant drivers reasonably easily though.

And finally **sudo**! Well, that has got to do with fiddling with the operating system. basically, normal users are locked out from manipulating the OS. Any activity that modifies the OS requires you to prove that you are the administrator by giving the correct password. Linux plays 'dumb' in this respect, that is, if you try to do something like alter an OS file, it will just tell you that you can't do it. You have to tell it that the "*super-user*" (**su-**) wishes to do (**-do**) something followed by the appropriate command. So to alter a file like **/etc/X11/xorg.conf**, you don't say **gedit /etc/X11/xorg.conf** which will just let you look at a copy of the file and save it elsewhere, you need to say **sudo gedit /etc/X11/xorg.conf** which will let you alter and save it back into its original place (just as a warning for later, whenever you start altering these OS files, save a backup as the first thing you do! Lot of experience talking here!). Whenever you undertake a GUI activity that deals with the OS (like installing a new program or updating), you will be asked for the sudo password. Its the password of the first user entered into the system at install by default. So for your desktop, its the same as your log in paassword.

---

### Post by apunc1 on 2007-06-10
the difference between kubuntu, ubuntu, and xubuntu is the desktop interface.
kubuntu=kde
ununtu=gnome
xubuntu=xfce 

the kubuntu menu is designed to look similar to windows. xubuntu is generally for lower end machines as xcfe is a lighter desktop environment. i personally prefer gnome because it is less clunkier than kubuntu and there is more support here on the forum for it.

dapper is version 6.06 of the *buntus (kubuntu, ubuntu, xubuntu)
the most recent version is feisty 7.04. i assume this is the version you will receive from shipit.

if you have version 5.04 or 5.10 on cd and install it you would have to upgrade chronologically from 5.10->6-06->6.10->7.04 via online updates so it makes sense to wait and d a fresh install of feisty

sudo=super user do. you will use it to run any administrative tasks, for example when you install a program or update your operating system.

---

### Post by koenya on 2007-06-10
hi there,


Ubuntu is more clean, mac like, while kubuntu has more detailed config options

You can use wine to run your photoshop and your premiere. But I doubt that you will get the dual core functionality out of your wine.

But I advise you to find alteratives for premiere and photoshop. Linux programs are written to work well with the linux kernel and with the interface. For photopshop there are two alternatives: the gimp and cinepaint (the latter has cmyk support if you install the icc profiles ofcourse).

As for premiere: cinelerra

If you want to use photoshop and premiere I would advise windows xp; it´s a very good program if you don´t use internet, e-mail and stick to a limited number of programs.

---

### Post by SUIHARA on 2007-06-10
> **AAM said:**
> Basically:
1. name set #1 deals with desktop used - Ubuntu [GNOME], Kubuntu [KDE], Xubuntu [Xfce], Edubuntu [GNOME with education apps]
2. name set #2 deals with version, follows a two word alliteration name - Dapper Drake  6.06 [released 06/2006], Edgy Eft 6.10 [released 10/2006], Feisty Fawn 7.04 [released 04/2007]
3. WINE runs programs - check with winehq for what will run. MSN is not needed as the Linux natives Kopete and GAIM achieve the same things. Nero also is a pale comparison to K3B. I am fairly sure that some versions of Photoshop run but if you wish there is a very good alternative in GIMP (but most Photoshoprers don't seem to like it as an alternative). Don't know what VDUB Mod unless its a 'modified Volkswagen', but that's unlikely on a computer site!

As for the question about Ubuntu version 5 (Breezy Badger?), it will give you some idea but there have been quite a few advances since then. If your hardware is very new, that version may not actually recognise the hardware. Certainly use the LiveCD to get a view of what its like.

Issue of modem depends on what type it is. If it is a winmodem - it's tough! Linuxant.com have commercial drivers available that do work and are cheap. If you have a proper modem then I understand that they work very easily - plug and go kind of thing. I am speaking from reputation here as I got broadband about the same time as I also got a proper modem! I did manage a winmodem with Linuxant drivers reasonably easily though.

> **apunc1 said:**
> the difference between kubuntu, ubuntu, and xubuntu is the desktop interface.
kubuntu=kde
ununtu=gnome
xubuntu=xcfe 

the kubuntu menu is designed to look similar to windows. xubuntu is generally for lower end machines as xcfe is a lighter desktop environment. i personally prefer gnome because it is less clunkier than kubuntu and there is more support here on the forum for it.

dapper is version 6.06 of the *buntus (kubuntu, ubuntu, xubuntu)
the most recent version is feisty 7.04. i assume this is the version you will receive from shipit.

if you have version 5.04 or 5.10 on cd and install it you would have to upgrade chronologically from 5.10->6-06->6.10->7.04 via online updates so it makes sense to wait and d a fresh install of feisty

sudo=super user do. you will use it to run any administrative tasks, for example when you install a program or update your operating system.


ok

the disk i have doesnt have a live cd when i boot it
it just says
instal txt
instal cmd line
and instal oem 
i think
then its got a few things like help and mem test

vdub mod = VirtualDubMod
the program i use to record from my capture card ohh i forgot lol will my capture card work?

thanks for ur reply 

also i have used my friends pc alil and i was saying the sudu thing i dont really under stand
is every thing run of sudu? 
so theres like no auto runs off cds or click a exe and enter info and install?

> **koenya said:**
> hi there,


Ubuntu is more clean, mac like, while kubuntu has more detailed config options

You can use wine to run your photoshop and your premiere. But I doubt that you will get the dual core functionality out of your wine.

But I advise you to find alteratives for premiere and photoshop. Linux programs are written to work well with the linux kernel and with the interface. For photopshop there are two alternatives: the gimp and cinepaint (the latter has cmyk support if you install the icc profiles ofcourse).

As for premiere: cinelerra

If you want to use photoshop and premiere I would advise windows xp; it´s a very good program if you don´t use internet, e-mail and stick to a limited number of programs.

thats ok coz i dont have a dual core

---

### Post by koenya on 2007-06-10
yes there is. 

but try the feisty live cd, once you´re in you´ll see the install options
simple install; just use applications/install
advanced; synaptics

---

### Post by AAM on 2007-06-10
sorry, I added some more and so the quote is not complete!

I will defer on the capture card, although I would be very very surprised if there is not a similar program. As I have written, **sudo** is necessary in one context only. There is an autorun option for CDs, and you use a much more comprehensive system for program install and updates. Incidentally I should point out that Linux is really a child of the Internet, and having a broadband connection is not far off necessary if you wish to stay out of "Dependency Hell" (you'll recognise the place if you ever go there). If you only have dial-up then you should look at some alternatives to help you (you can get advice on this later from me if you need to - or others too).

---

### Post by apunc1 on 2007-06-10
> **SUIHARA said:**
> ok

the disk i have doesnt have a live cd when i boot it
it just says
instal txt
instal cmd line
and instal oem 
i think
then its got a few things like help and mem test


you have the alternate cd. are you able to download a live cd? go here [http://us.releases.ubuntu.com/feisty/](http://us.releases.ubuntu.com/feisty/)
the live cd is also called the desktop cd


> **SUIHARA said:**
> 
also i have used my friends pc alil and i was saying the sudu thing i dont really under stand
is every thing run of sudu? 
so theres like no auto runs off cds or click a exe and enter info and install?

you use sudo to install programs from synaptic via the gui or terminal. it is for safety reasons, since you just wouldn't want anyone to come up and install things on your computer. this may answer some of your questions about sudo [http://www.newlinuxuser.com/explain-what-is-sudo/](http://www.newlinuxuser.com/explain-what-is-sudo/)

it's really that complicated and not much of a hassle.

---

### Post by SUIHARA on 2007-06-10
> **koenya said:**
> hi there,


Ubuntu is more clean, mac like, while kubuntu has more detailed config options

You can use wine to run your photoshop and your premiere. But I doubt that you will get the dual core functionality out of your wine.

But I advise you to find alteratives for premiere and photoshop. Linux programs are written to work well with the linux kernel and with the interface. For photopshop there are two alternatives: the gimp and cinepaint (the latter has cmyk support if you install the icc profiles ofcourse).

As for premiere: cinelerra

If you want to use photoshop and premiere I would advise windows xp; it´s a very good program if you don´t use internet, e-mail and stick to a limited number of programs.

> **koenya said:**
> yes there is. 

but try the feisty live cd, once you´re in you´ll see the install options
simple install; just use applications/install
advanced; synaptics


no the disk i have doesnt have live cd
it might not be version 5 my friend said it is but i dunno


and to every one else thanks
and do you all think ubuntu is for me i think so but i dont really know much about it

also about the hell of deps

most of the programs i use have a linux version
not sure about nero,adobe,vdub,msn ect 
but it dont really matter if i cant use adobe or nero 
but i would prefer adobe over gimp or sumthing
but if wost comes to wost i will use gimp

---

### Post by eldepeche on 2007-06-10
Sudo actually stands for "switch user do," as you can execute a command as an arbitrary user, provided the system is set up to allow it.

The way everyone except the most hardcore of geeks uses sudo is to perform administrator tasks. Under Windows 2000/XP, certain actions (installing software, modifying hardware settings) require authentication with an administrator account and password. In Ubuntu, this role is identical. If you choose an administrator program from the menu, such as the network settings, you will be asked for your password (the default account is an administrator user). 

In order to perform administrative tasks from the command line, like editing system-wide configuration files, you need to prefix the command with "sudo." When running regular programs, sudo is unnecessary, since executing programs doesn't require administrator access.

Software lives in repositories on remote servers; instead of downloading an .exe installer for Firefox and executing it, issuing the command "sudo apt-get install mozilla-firefox" tells the system to download the necessary files for Firefox, install them, and put a shortcut in the Applications menu. (This is only an example, since Firefox is installed by default in Ubuntu.)

---

### Post by Outrunner on 2007-06-10
> **eldepeche said:**
> Sudo actually stands for "switch user do," as you can execute a command as an arbitrary user, provided the system is set up to allow it.

I think that would be super user do, not switch user do.

---

### Post by SUIHARA on 2007-06-10
> **eldepeche said:**
> Sudo actually stands for "switch user do," as you can execute a command as an arbitrary user, provided the system is set up to allow it.

The way everyone except the most hardcore of geeks uses sudo is to perform administrator tasks. Under Windows 2000/XP, certain actions (installing software, modifying hardware settings) require authentication with an administrator account and password. In Ubuntu, this role is identical. If you choose an administrator program from the menu, such as the network settings, you will be asked for your password (the default account is an administrator user). 

In order to perform administrative tasks from the command line, like editing system-wide configuration files, you need to prefix the command with "sudo." When running regular programs, sudo is unnecessary, since executing programs doesn't require administrator access.

Software lives in repositories on remote servers; instead of downloading an .exe installer for Firefox and executing it, issuing the command "sudo apt-get install mozilla-firefox" tells the system to download the necessary files for Firefox, install them, and put a shortcut in the Applications menu. (This is only an example, since Firefox is installed by default in Ubuntu.)

so in other words? i cant download this and run it to install? even tho its the linux version
[http://teamxlink.co.uk/binary/kaid-7.0.0.7-linux-x86.tar.gz](http://teamxlink.co.uk/binary/kaid-7.0.0.7-linux-x86.tar.gz)

---

### Post by Outrunner on 2007-06-10
> **SUIHARA said:**
> so in other words? i cant download this and run it to install? even tho its the linux version
[http://teamxlink.co.uk/binary/kaid-7.0.0.7-linux-x86.tar.gz](http://teamxlink.co.uk/binary/kaid-7.0.0.7-linux-x86.tar.gz)

Why wouldn't you be able to? Of course you can.

---

### Post by SUIHARA on 2007-06-10
> **Outrunner said:**
> Why wouldn't you be able to? Of course you can.

but what about the sudo apt-get install mozilla-firefox thing wouldnt i have to download it like so.
sudo apt-get install xlink-(version)linux
?
and if so what if the server its downloading from doesnt have that file

---

### Post by eldepeche on 2007-06-10
Wikipedia says "su" stands for "substitute user," but I'd always heard "switch user." Since "sudo" is like "su" but will only "do" one command, so it seems logical that "sudo" would mean "su+do."

I'm by no means an authority, but it seems like since "sudo -u <username or uid#> <command>" will execute a command as an arbitrary user, it's not only for performing actions as root.

Not an important point, and I don't know for sure.

---

### Post by Outrunner on 2007-06-10
> **SUIHARA said:**
> but what about the sudo apt-get install mozilla-firefox thing wouldnt i have to download it like so.
sudo apt-get install xlink-(version)linux
?
and if so what if the server its downloading from doesnt have that file

That's not how it works. Using apt-get(or aptitude or Synaptic or Add/Remove... ) is just one way to do it. Usually if you download a .tar.gz , you'll have to extract the file and then compile the program, which is harder

EDIT: > **eldepeche said:**
> Wikipedia says "su" stands for "substitute user," but I'd always heard "switch user." Since "sudo" is like "su" but will only "do" one command, so it seems logical that "sudo" would mean "su+do."

I'm by no means an authority, but it seems like since "sudo -u <username or uid#> <command>" will execute a command as an arbitrary user, it's not only for performing actions as root.

Not an important point, and I don't know for sure.

That's good logic. Now I'm not sure myself. It's just that I read that it means super user do in my early GNU/Linux days, so I stuck to that.

---

### Post by SUIHARA on 2007-06-10
> **Outrunner said:**
> That's not how it works. Using apt-get(or aptitude or Synaptic or Add/Remove... ) is just one way to do it. Usually if you download a .tar.gz , you'll have to extract the file and then compile the program, which is harder

EDIT: 

That's good logic. Now I'm not sure myself. It's just that I read that it means super user do in my early GNU/Linux days, so I stuck to that.

oh :( i hate compiling lol i fort that .tar.gz was like zip
since the windows version of the download is .zip

---

### Post by Outrunner on 2007-06-10
> **SUIHARA said:**
> oh :( i hate compiling lol i fort that .tar.gz was like zip
since the windows version of the download is .zip

It's not that hard you know... You can extract the file with

```
tar xzvf <filename.tar.gz>
```

```
cd <extracteddir>
./configure
make
sudo make install
```

That's how it's usually done

---

### Post by SUIHARA on 2007-06-12
yeah i put it on my 2nd hd and its 6.10 eft or sumthin
i coulnt understan how to get drivers for my modem i found a network/dialup part
i put my info in it and theres no dial button and when i save it and close the reopen the info is gone

---

