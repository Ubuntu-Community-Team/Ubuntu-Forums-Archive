---
title: "is ubuntu right for me"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by ausomadam on 2007-08-15
i have an old computer that i would like to use just really for the internet,  an instant messaging client , and listening to music.
the computer used to run windows 98 but i am going to wipe the hard drive soon so it wont any more
it has a 
intel pentium 2 prossesor
384mb of ram
and a 12 gb hard drive
So if i do the disk installation will Ubuntu run correctly and everything or should i find a different version of Linux? f so does anyone have any suggestions?

thanks alot

---

### Post by Hobo Joe on 2007-08-15
Yes, Ubuntu is for you!

Welcome!

---

### Post by ausomadam on 2007-08-15
so you think it will work with those specs ?

---

### Post by ausomadam on 2007-08-15
which version should i get? the 7.04 or the 6.06?

---

### Post by Hobo Joe on 2007-08-15
> **ausomadam said:**
> so you think it will work with those specs ?

Yes indeedy!


Are you going dual boot or just go full Ubuntu?

EDIT:
> which version should i get? the 7.04 or the 6.06?

7.04, definitely.

---

### Post by ausomadam on 2007-08-15
no im not gonna dual boot, and so those specs can handle 7.04? which i assume is newer one

---

### Post by Hobo Joe on 2007-08-15
> **ausomadam said:**
> no im not gonna dual boot, and so those specs can handle 7.04? which i assume is newer one

Yes and yes.

---

### Post by ausomadam on 2007-08-15
thank you for your help im gonna download it tonight and ill install it tomorrow and ill post the results

---

### Post by Hobo Joe on 2007-08-15
> **ausomadam said:**
> thank you for your help im gonna download it tonight and ill install it tomorrow and ill post the results

Awesome!

Let us know if you run into any problems and we'll try and sort them out for you.

---

### Post by ausomadam on 2007-08-15
will do thanks alot

---

### Post by zeehat on 2007-08-15
It has a P2.  Wouldn't it be better for Xubuntu?

---

### Post by Hobo Joe on 2007-08-15
Well, that's a possibility, but I think it'll run Ubuntu ok, and I think if you can, you should get Ubuntu of Xubuntu. If he has trouble, I'll suggest Xubuntu.

---

### Post by zeehat on 2007-08-15
Yup, that seems like the most logical thing to do.

---

### Post by ausomadam on 2007-08-16
i need to know how to wipe the old hard drive anyone know?

---

### Post by ausomadam on 2007-08-16
> **zeehat said:**
> It has a P2.  Wouldn't it be better for Xubuntu?

ill try ubuntu first i guess since its already burned


and btw i think i figured out how to wipe the hard drive

---

### Post by Ozeuss on 2007-08-16
> **ausomadam said:**
> ill try ubuntu first i guess since its already burned


and btw i think i figured out how to wipe the hard drive

don't worry about wiping your hard drive. the install disk can do that for you.

---

### Post by RomeReactor on 2007-08-16
Hi. During the installation process you can wipe the HD or make a partition. Since you already mentioned this HD will only have Ubuntu, just boot into the Live CD, and when you get to the desktop double-click on the **Install** icon. Follow the instructions, and when you get to the point where it asks you how to partition your disk, select **Guided Partitioning** and then **Use Entire Hard Drive**.

---

### Post by darksidedude on 2007-08-16
when you boot the live cd and go thew the install process just tick the thing about taking over a hard disk, it will do all the hard work for you

you wont need a serperate disc for xubutu if you want

```
sudo apt-get install xubuntu-desktop
```

---

### Post by RomeReactor on 2007-08-16
> **darksidedude said:**
> when you boot the live cd and go thew the install process just tick the thing about taking over a hard disk, it will do all the hard work for you

you wont need a serperate disc for xubutu if you want

```
sudo apt-get install xubuntu-desktop
```

That's correct, you don't need to download the Xubuntu CD. However, if eventually you decide to install the Xubuntu desktop, I suggest you use **aptitude** instead of **apt-get**:
```
sudo aptitude install xubuntu-desktop
```
that way, if for any reason you decide to remove it later, you can use:
```
sudo aptitude remove xubuntu-desktop
```
which will remove all xubuntu-desktop related packages; uninstalling with apt-get or Synaptic will only remove the metapackage, leaving all its programs and libraries installed.

---

### Post by ausomadam on 2007-08-16
thanks i was just about to wipe my hard drive now but i guess ill just try the live cd thing, owell at least i learned how to go to the computers bios now, lol.

---

### Post by irish_flu on 2007-08-16
> **ausomadam said:**
> thanks i was just about to wipe my hard drive now but i guess ill just try the live cd thing, owell at least i learned how to go to the computers bios now, lol.

Keep in mind that it will run a *lot* faster installed on a hard drive than it will run for the CD.  Don't base any performance-type opinions on the CD.  :)

I had Ubuntu installed on a similar system, it ran fine.  As others have said, if it seems sluggish to you there's always the option to install Xubuntu (which uses a "lighter" desktop) later on, without downloading a new CD and without reinstalling. You'll be able to switch back and forth between the desktops.

---

### Post by ausomadam on 2007-08-16
with the cd it installs it right?



The only problem is when i put the cd in it brings up the blue fatal error screen? any one know why or how i get around that?

---

### Post by sailor2001 on 2007-08-16
1st. Are you booting into the ubuntu? 2nd. where did you get ubuntu? 3rd. ubuntu download should be i386 iso and then burnt at a slow speed.4th checksum the disk

---

### Post by Hobo Joe on 2007-08-16
> **ausomadam said:**
> with the cd it installs it right?



The only problem is when i put the cd in it brings up the blue fatal error screen? any one know why or how i get around that?

Did you get to the menu or did you just get a blue screen when you tried to boot from the cd? Or was it when you were shutting down the computer?(I'm assuming it has Windows on it currently)

---

### Post by sailor2001 on 2007-08-16
> **ausomadam said:**
> i have an old computer that i would like to use just really for the internet,  an instant messaging client , and listening to music.
the computer used to run windows 98 but i am going to wipe the hard drive soon so it wont any more
it has a 
intel pentium 2 prossesor
384mb of ram
and a 12 gb hard drive
So if i do the disk installation will Ubuntu run correctly and everything or should i find a different version of Linux? f so does anyone have any suggestions?

thanks alot

384mb ram? check again

---

### Post by RomeReactor on 2007-08-16
Try booting again, but this time, press **F6** at the starting menu and choose to boot like this:
```
linux noapic acpi=off
```
If that doesn't get you to the desktop, try [these other options]("http://ubuntuforums.org/showpost.php?p=2225548&postcount=4").

384 RAM is more than the recommended minimum; however, if that fails, maybe the Alternate CD would be appropriate.

---

### Post by ausomadam on 2007-08-16
yes its 384mb of ram

i got ubuntu from the main page i downloaded it and burned it.


just now i changed the bios so the cd boots first and ubuntu is installing now....

---

### Post by ausomadam on 2007-08-16
now it has loaded and there is an install in the top left so im going to do that now

---

### Post by RomeReactor on 2007-08-16
So it really *was* the BSOD!

---

### Post by ausomadam on 2007-08-16
the what?

and btw how come during instalation there are no places in texas to say were your from but the distrubution center i got the cd from last night was in dallas?

---

### Post by jgrabham on 2007-08-16
> **RomeReactor said:**
> So it really *was* the BSOD!

Windows' last stand :D

---

### Post by ausomadam on 2007-08-16
ooo blue screen of death yeah lol
its partioning the hard drive now

---

### Post by kazuya on 2007-08-16
I wondered about why you could not select houston, texas as well.. It is a good question, but that is the case for most of the linux distributions including Ubuntu. 

b/w you and me, I would have recommended Linux Mint for a beginner. It is essentially Ubuntu but with all the multimedia codecs, flash, etc already included. With default Ubuntu, you may have to go in Synaptic and install them yourself if for some reason media file does not play.

But Ubuntu should work great for you. It did for me.

---

### Post by ausomadam on 2007-08-16
so does it not play certain files? most of my music is mp3's and i was gonna download the vlc media player will it work?

---

### Post by Hobo Joe on 2007-08-16
> **ausomadam said:**
> so does it not play certain files? most of my music is mp3's and i was gonna download the vlc media player will it work?

You will have to install a couple of packages, but don't worry, it's very simple.

---

### Post by ausomadam on 2007-08-16
oh ok will it prompt me to and like tell me were to go or do will i have to use the magical powers of google to find it?

---

### Post by mysticmatrix on 2007-08-16
When you'll double click a MP3 file, it will ask you to install appropriate codecs. Just click Yes 3 times and you'll be able to play all your MP3's. Ditto for other files.

---

### Post by Hobo Joe on 2007-08-16
This is all you need to do:
```

sudo aptitude install libxine-extracodecs

```

---

### Post by ausomadam on 2007-08-16
> **Hobo Joe said:**
> This is all you need to do:
```

sudo aptitude install libxine-extracodecs

```

were do you type that?

---

### Post by Hobo Joe on 2007-08-16
> **ausomadam said:**
> were do you type that?

In the terminal, located under applications>accessories.

---

### Post by RomeReactor on 2007-08-16
Installing multimedia packages is not that hard; you just need to tell us what formats you want to play, and we'll help you get them installed. And with the right codecs, you can play virtually any audio/video format: mov, wmv, mkv, avi, mpeg, DVDs, mp3, mp4, flac, wav, etc. By default, Ubuntu provides codecs for ogg only, I think. That's due to some licensing and/or patent issues with some codecs, which don't allow redistribution, so you have to install them yourself. Think of it as installing windows and then getting the CCCP codec pack. Not the same, but somewhat similar.

---

### Post by ausomadam on 2007-08-16
oh ok thank you lots and lots

---

### Post by ausomadam on 2007-08-16
is there a place i can find these codes ?

---

### Post by Sbarton on 2007-08-16
In the Terminal, and sometimes it is better to copy/paste the instructions given. Hoping of course that the code your copying is correct.
regards

---

### Post by ausomadam on 2007-08-16
lol yeah i was gonna copy them that would be to hard to try and remember them

---

### Post by RomeReactor on 2007-08-16
I would suggest you wait until you see if everything works fine once Ubuntu finishes installing; check that everything that was working before (when you were running the Live CD) is still working correctly.

---

### Post by Hobo Joe on 2007-08-16
Well, there are a lot, but there are the few basic and highly useful ones.

First:
Sudo
Sudo mean root, in other words, it gives you administrative rights, pretty much anything can be prefixed by that.
Then:
Aptitude
Aptitude has to do with installing things, like I just showed you. For example, I could say 'sudo aptitude install picasa' sudo is making it admin, aptitude is telling it to use the installer, and install is telling it to find the program and download it, and of course picasa is the program name.
You can also do 'sudo aptitude search -----', it will look in the repositories for you and find the programs that fit what you typed in.
So if I typed 'sudo aptitude search firefox' I would get a whole bunch of names for firefox and it's children. Then you could take any of those programs in the list and install then with the install command.

There are others obviously, but those are the top ones.

---

### Post by stchman on 2007-08-16
> **ausomadam said:**
> i have an old computer that i would like to use just really for the internet,  an instant messaging client , and listening to music.
the computer used to run windows 98 but i am going to wipe the hard drive soon so it wont any more
it has a 
intel pentium 2 prossesor
384mb of ram
and a 12 gb hard drive
So if i do the disk installation will Ubuntu run correctly and everything or should i find a different version of Linux? f so does anyone have any suggestions?

thanks alot

I have Ubuntu running on a P3-450 with 256MB RAM.  The RAM is OK, the proc might be a little slow.  I would recommend getting a larger hdd.

---

### Post by Tomosaur on 2007-08-16
If you're brand new to Linux / Ubuntu - then you should probably familiarise yourself with the Add/Remove application first (It's in the Applications menu). The method of installing software is pretty different from on Windows - you just select the program you want, then click 'apply', and it's automatically downloaded and installed for you. 

As for multimedia - codecs and such - Ubuntu will try to recognise when you're trying to listen or watch something, and will do its best to tell you about codecs and stuff if you need them, but it can't always tell what you're up to (depending on the program you use, how you open files etc).

---

### Post by RomeReactor on 2007-08-16
Most people here--including us--will tell you to install this or that by entering commands in the terminal; we do this because it's much easier and faster than saying "go here, then here, press this button, enter your search terms here, press this other button, scroll until you find this package, double-click, search for this other package", etc. However, when you are searching for programs, you have a very user friendly graphical application called Add/Remove. Or a more powerful package manager called Synaptic. These two programs will solve your program-installing needs, when you want to search for programs on your own. You practically don't have to see the terminal on a functioning installation of Ubuntu; it's only when something breaks, or you want advise regarding which packages to install, or making certain configuration changes, that you'll come across it.

Having said that, in time you'll find the terminal to be a very powerful tool.

---

### Post by ausomadam on 2007-08-16
well i am on ubuntu now! it is very nice and i like it alot i have so far activated the gaim chat which is very cool and used firefox time to explore more now and thanks for everyones help!

---

### Post by amazingtaters on 2007-08-16
Good deal man. Remember to ask if you need more help.

---

### Post by ausomadam on 2007-08-16
oh i will this linux experience is much nicer than ive ever had with customer support yuckkkk

---

### Post by amazingtaters on 2007-08-16
Whaaaat?!?!?! You don't miss those precious hours on the phone with tech support? I know I pine for them sometimes. Keeps me up at night wondering what tech support is doing without my calls...

---

### Post by ausomadam on 2007-08-16
ahh im sure there helping some clueless person dont worry lol

---

