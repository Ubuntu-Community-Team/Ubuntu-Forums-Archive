---
title: "Can my computer handle Ubuntu with Beryl ?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Cruvenium on 2008-03-23
Hey guys , here's my specs .

Intel Mobile Centrino Pentium M , 1.4GHz ,
512MB RAM ,
32-bit Intel 82852/82855 GM/GME Graphics Controller .

So , can that run Ubuntu with Beryl ?

---

### Post by quinnten83 on 2008-03-23
I think it should since it is intel.
but you can easily try with a live CD, since compiz is installed by default.
(compiz and beryl merged, so now it is compiz fusion).
If you use the Gutsy Gibbon (7.10) release, just start from CD, don't install yet.
select System>Preference>Appearance 
Select the tab "Visual Effects" and select extra.
If your windows now wobble and closing a window makes it fade away, then your golden.
If it works, you can go to "add/remove" and search for ccsm and install it, This will allow you to tweak compiz. 
Also open up a command line (accesories>console) and type

```
sudo apt-get install emerald
```

to get the compiz windows decorator. You can now change the theme.
Happy tweaking

---

### Post by Cruvenium on 2008-03-23
I'm running Ubuntu 7.10 Desktop version , so does it have Compiz Fusion ?

---

### Post by quinnten83 on 2008-03-23
yes it does...
if you go to systems>preferences>appearance and select the "visual effect" tab, select the second or third radio button, ubuntu will check if your computer can handle the effects. If it can't it will tell you that it could not be enabled. Otherwise it will just enable it.

---

### Post by Cruvenium on 2008-03-23
Alright , so I'm burning Ubuntu into a CD .

So it installs itself into my HDD , or it's just a Live CD ?

Or do I have options ?

---

### Post by oedha on 2008-03-23
> **Cruvenium said:**
> Alright , so I'm burning Ubuntu into a CD .

So it installs itself into my HDD , or it's just a Live CD ?

Or do I have options ?

.....previously you said that you're running 7.10....now you're burning a CD....
confusing.......
but.....yes...i have checked your VGA...you can run compiz well :)

Edit : after burning the ISO to cd....you have to boot from that cd to get live desktop
after that...click on install icon
but....the most important think is.......have you manage your partition ? and defrag your windows partition (if you have)

---

### Post by Cruvenium on 2008-03-23
Sorry sorry , mistake .

"I **AM** going to run Ubuntu 7.10" . :D .

A few questions , I'm a complete noob to Linux .

What format does my HDD have to be in , NTFS or FAT32 ?

And , when I run it , I have 2 options to boot , am I right ?

---

### Post by oedha on 2008-03-23
hehehe....nevermind.......
sorry .. i have to go...but you can take a look at :==> [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

all of your questions will be answered there..........from zero to.....you name it.......:)

edit : 
you can manage your partition with gparted livecd :==> [http://gparted.sourceforge.net](http://gparted.sourceforge.net)
linux partition = ext3 or reiserFs and swap
for your windows.....just let it be.......
time for you to read the link that i have given......

---

### Post by quinnten83 on 2008-03-23
I would suggest just running the live CD untill you get a feel for things.
After that, BACKUP YOUR DATA, defragment windows and install.
Ubuntu's installation is pretty much self explanatory, so don't worry about it.
Just make sure you BACKUP YOUR DATA!!! and I mean on an external medium.

---

### Post by jan quark on 2008-03-23
additionally to the psychocats site here is a good bunch of tutorials dealing with dual-booting if you wish to stay with windows for some reasons

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by Cruvenium on 2008-03-23
Now , weird thing .

I burn it using PowerISO 10x speed , when I boot it , I click Install or Boot from Live CD (or something like that) .

It loaded for quite a long time , and black screen came out . I thought it was loading , fine .

I left it and went out to play my PS2 .

When I came back , it was still the same old black screen . What's wrong ? Can someone tell me ?

---

### Post by jan quark on 2008-03-23
it is recommend to burn the ubuntu iso at the lowest possible speed to avoid errors

did you check the cd for errors, there is a option for this when you boot with the CD

also see:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Cruvenium on 2008-03-23
Alright , gonna try this baby once more with another CD-R disc @ 4x .

I hope this is the last CD Imma use .

---

### Post by Cruvenium on 2008-03-23
Still , doesn't work .

Same old black screen .

Any more ways than booting ? Like , run the .EXE and then install to another partition or something .

---

### Post by Spanky2k5 on 2008-03-24
I feel for you dude.
I only decided to give Ubuntu a go yesterday (my first time with Linux) and had the same problem
I booted the Live CD in VGA safe mode and installed from there and all worked since then

Thing is I installed Xubuntu to see what Compiz Fusion could do first hand but I'm having problems myself
I think its to do with the driver I'm using for the onboard Intel 845g graphics, but neither I810 and Intel seem to work, so I'm stuck with Vesa

If anyone has any ideas what I can do to get Compiz Fusion working I'm running Xubuntu 7.10 on an old iFriend NC202i4 notebook. I believe it a 2ghz Celeron, 512mb Ram and the Intel 845g Graphics.

If anyone wants me to post my xorg.conf file they'll need to tell me how to do it first (seriously, never used Linux before last night).

Also trying to get a Phillips SNU5600 Wireless USB installed but haven't really tried doing anything with that yet as VGA's my priority.

Cheers for any help

---

### Post by Tyke91 on 2008-03-24
no hijacking the thread please :)


Download the Alternate install CD, it is a text based installer (alot more like windows's install process instead of the nice graphical live CD)  

again, burn at lowest speed and for god's sake [COLOR=Red]BACK UP ALL YOUR DATA![/COLOR]

---

### Post by stchman on 2008-03-24
> **Cruvenium said:**
> Hey guys , here's my specs .

Intel Mobile Centrino Pentium M , 1.4GHz ,
512MB RAM ,
32-bit Intel 82852/82855 GM/GME Graphics Controller .

So , can that run Ubuntu with Beryl ?

I don't see any problem.  It won't be screaming fast but 512MB is a minimum for decent usability.

---

