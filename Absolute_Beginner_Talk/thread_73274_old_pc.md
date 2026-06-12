---
title: "old pc"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by pigmelt on 2005-10-08
i have an oler pc it is a 400 mhz celeron, im running ubuntu on my newer pc, i was wondering if a lighter version of linux is out there and what would be recomended of that pc. i tried ubuntu hoary 5.04 but had a lot of problems with it some pakages would not load or not be there it is always a different pkg each time i try to install it, one time it said the kernal was not present. i have burned 6 different install disks using nero,deepburner,and iso burner. i think i just need to find a lighter distro. or retire the older pc. thanks for any help.

---

### Post by Teroedni on 2005-10-08
Have you tried server install?

It is a little bit more difficult, but you can tune ubuntu to your machine too make it fast enough.

---

### Post by delltraveller on 2005-10-08
[QUOTE=Teroedni]Have you tried server install?

It is a little bit more difficult, but you can tune ubuntu to your machine too make it fast enough.[/QUOTE]

So, how does one go about attempting the server install?

---

### Post by skoal on 2005-10-08
[QUOTE=delltraveller]So, how does one go about attempting the server install?[/QUOTE]
At the very beginning of the install CD, when it boots up I think there's either a FN (function) key you press or, IIRC, you just type "server" at the initial prompt.

After you go through the install phase, you'll reboot.  You'll login at the command prompt, then do the following:

1. sudo apt-get update
2. sudo apt-get install x-window-system-core
3. Take your pick of desktops: [xfce](http://www.ubuntuforums.org/showthread.php?t=30896), openbox, or many others light WMs.
4. startxfce4, or startx (for the others)

\\//_

---

### Post by zerhacke on 2005-10-08
I used to have a P2-300Mhz desktop box that gave me fits while trying to install Ubuntu Hoary or any other version of Linux for that matter from the CDROM.  When I tried a network install of Mandy, it worked perfectly.  Turns out the CDROM had gone bad.

Food for thought.

I say I used to have the machine because recently, my beloved little old Dell Optiplex passed away.

---

### Post by patrick295767 on 2005-10-08
[http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)

if you wanna some kind of help for old pc ... let me know if u'd like more information

Pat'

---

### Post by pigmelt on 2005-10-09
tried server install with new burnt disk. no go
i think that there are some more problems than the install cd, i believe that this pc is ready for recycleing ( building with the left over parts). still i get different errors every time i try to install. each time i also reformat the hd. thanks for trying to help. but sometimes ya gota know when to give up gracefuly.

---

### Post by DJ_Max on 2005-10-09
[QUOTE=pigmelt]tried server install with new burnt disk. no go
i think that there are some more problems than the install cd, i believe that this pc is ready for recycleing ( building with the left over parts). still i get different errors every time i try to install. each time i also reformat the hd. thanks for trying to help. but sometimes ya gota know when to give up gracefuly.[/QUOTE]
What was wrong with the server install?

BTW, have you looked at [http://ubuntulite.org/](http://ubuntulite.org/)

---

### Post by delltraveller on 2005-10-09
[QUOTE=skoal]At the very beginning of the install CD, when it boots up I think there's either a FN (function) key you press or, IIRC, you just type "server" at the initial prompt.

After you go through the install phase, you'll reboot.  You'll login at the command prompt, then do the following:

1. sudo apt-get update
2. sudo apt-get install x-window-system-core
3. Take your pick of desktops: [xfce](http://www.ubuntuforums.org/showthread.php?t=30896), openbox, or many others light WMs.
4. startxfce4, or startx (for the others)

\\//_[/QUOTE]
An internet or network connection is required to use apt-get, isn't it?

I'm installing on an old Asus MEW-B motherboard with onboard video and sound, Celeron 600MHz, 256MB ram, two Toshiba cd-rom drives, Sony floppy drive, not modem, no network.  The live cd runs nicely, but the thing absolutely refuses to do the full download.  I've managed to get the server version downloaded, but I'm way too green to work without some sort of graphic interface.  Is there some way I can work from the live cd (I've got no problem leaving it in the machine since there are two cdrom) and be able to save the work I do with it?

---

### Post by darkmatter on 2005-10-09
I used to have both Ubuntu and SuSE installed on an old PII 450 Mhz without any problems, performance issues.

I'm not all to sure that the age is the problem. How much RAM do you have?

---

### Post by delltraveller on 2005-10-09
[QUOTE=darkmatter]I used to have both Ubuntu and SuSE installed on an old PII 450 Mhz without any problems, performance issues.

I'm not all to sure that the age is the problem. How much RAM do you have?[/QUOTE]
Mine has 256MB RAM.  I don't think pigmelt mentioned what his/her RAM was.

Pigmelt, when trying to do the full install on mine I had the same problems you mention.

---

### Post by darkmatter on 2005-10-09
[QUOTE=delltraveller]Mine has 256MB RAM.  I don't think pigmelt mentioned what his/her RAM was.

Pigmelt, when trying to do the full install on mine I had the same problems you mention.[/QUOTE]

That is enough RAM.

I looked at your previous post, and noticed that the PC is not network enabled. That could be a small problem. I've never managed to get the default install without network (it always required 4 packages to be dl'd from the repo's)

You say you have the base (server) system installed?

Have you tried using aptitude or apt-get to install GNOME and Xorg?

They are both on the CD, so they should install from there instead of being fetched from the net. An internet connection should not be necessary unless a desired package is not available on the install CD.

---

### Post by az on 2005-10-09
If I though a pc was defective (And I think so every other day) I would run memtest86 (from the breezy installer) as well as checking the haddrive for bad blocks

ex:
mkfs -c /dev/hda5

You can run that from the installer cd (either rescue mode or just boot and when is asks you about partitioning, hit CTRL-ALT-F2 and use that console)

---

### Post by delltraveller on 2005-10-09
[QUOTE=darkmatter]That is enough RAM.

I looked at your previous post, and noticed that the PC is not network enabled. That could be a small problem. I've never managed to get the default install without network (it always required 4 packages to be dl'd from the repo's)

You say you have the base (server) system installed?

Have you tried using aptitude or apt-get to install GNOME and Xorg?

They are both on the CD, so they should install from there instead of being fetched from the net. An internet connection should not be necessary unless a desired package is not available on the install CD.[/QUOTE]
Okay, let's see here.....apt-get is a no go.......aptitude...add gnome....make self root..and go....is.....doing stuff....selecting, loading......setting up.....updating.....rebuilding database.  Looks like we've got something good going here.

---

### Post by delltraveller on 2005-10-09
[QUOTE=azz]If I though a pc was defective (And I think so every other day) I would run memtest86 (from the breezy installer) as well as checking the haddrive for bad blocks

ex:
mkfs -c /dev/hda5

You can run that from the installer cd (either rescue mode or just boot and when is asks you about partitioning, hit CTRL-ALT-F2 and use that console)[/QUOTE]
hard drive checks out fine

---

### Post by delltraveller on 2005-10-09
Okay, upon restarting I end up at this message and it locks up:

I could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled.  Please restart gdm when
the problem is corrected.

---

### Post by buster on 2005-10-09
It's not Ubuntu, but you have that already : Damn Small Linux has a good reputation for older computers. That's if, of course, your old PC is sound. Certainly worth a try, and quite different in look and feel. (Both Ubuntu and DSL are Debian clones by the way.)

---

### Post by darkmatter on 2005-10-10
[QUOTE=delltraveller]Okay, upon restarting I end up at this message and it locks up:

I could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled.  Please restart gdm when
the problem is corrected.[/QUOTE]

Well, as you've already installed X, that error is most likely the result of X not being properly configured. (though I haven't seen that particular error message since my slackware days)

Boot up into recovery mode and after login, run 
```
sudo dpkg-reconfigure xserver-xorg
```

When you are finished try to startx and see if the GUI loads.

If you still don't get any results, post back any error messages that occur.

---

### Post by pigmelt on 2005-10-11
my old pc has 288 mb. an onboard 128 ati rage and on board sound balster, and a linksys 10/100 nic. it may be a hdd fault. ill check it out, i tried to install ubuntulite, and got all the way through it only to get fatal io error 104 (connection reset by peer) on x server ":0.0" after 0 requests (0 known processed) with 0 events remaining. also, no screens.
i went to the ubuntulite help site and did what was sugested there only thing is i dont realy understand it, something about the video card buss, when i did the pcilist it showed every thing, what can be done with the info from the listing?

---

