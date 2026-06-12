---
title: "WINE instructions"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-06-04
hello all,

need a thorough instruction on how to install WINE

thanks

---

### Post by tdrusk on 2006-06-04
[QUOTE=KarmaKing]hello all,

need a thorough instruction on how to install WINE

thanks[/QUOTE]
Go to system>administration>Synaptic Package Manager

Search for WINE.
Right click the program called wine and click "mark for installation".
it will show other things that need to go with it. click ok.
Then go to the top of the synaptic package manager and click apply.

Now whenever you have an .exe, right click it and click, "Open with Wine.

---

### Post by KarmaKing on 2006-06-04
ok, it shows that it is installed through synaptic, what now??

> Now whenever you have an .exe, right click it and click, "Open with Wine.

It doesn't show anything when i right click

---

### Post by gotvols on 2006-06-04
Go to system>administration>Synaptic Package Manager


I did the above, but I didn't see wine in the list.  When I did the search nothing came up.

---

### Post by gotvols on 2006-06-04
ok I went to the wine website and it had step by step instructions for Ubuntu.:KS

---

### Post by KarmaKing on 2006-06-05
yep I went to that site too.  I have the repositories and it was showing in synaptic.  I installed through synaptic, but it still shows nothing when I right click on an exec file.

Now, there are two different wine on my synaptic list and from what I gather, one is the hq version the other debian.  I have the hq version installed...if that helps any.

I also checked the the terminal and it says the latest version installed.  I followed the instruxtion to the letter and.....

---

### Post by darkruler01 on 2006-06-05
OK now can i get help doing this on KDE?

---

### Post by Matthew Bartram on 2006-06-05
Did you run winecfg?

---

### Post by KarmaKing on 2006-06-05
just ran it but I am not sure what to do exactly with that... I tried adding an application to the cfg but these errors are what I got

> @karmaubuntu:~$ sudo winecfg
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory


---

### Post by KarmaKing on 2006-06-05
question?

do I just add the exec file to the winecfg menu?

or, can I use it already installed on my XP partition?

---

### Post by KarmaKing on 2006-06-05
Ok, I got the exec file to start installing, but it just hangs up.  I am trying to install MusicMatch 10 for my MP3 player which uses a special format file (.MPY) and only MusicMatch does this.

I started the exec file and left it go for about 25 minutes, but just froze

any suggestions??

---

### Post by highslime on 2006-06-05
Heh, my usage of WINE lasted for about an hour before I got fed up with it, lol.  I play a MUD, and the client I use is Zmud.  Well, I got WINE to see it and all, but then occasionally as I was going about my business, the Zmud window just poofs, like something killed it.  And then once I got an access violation, and I couldn't kill it, trying every command I could find in help files and on the web.  That was pretty much the last straw for me. I'm gonna look for TinyFugue or something, I heard it's ok, just not as good as Zmud.  Oh, then I accidently downloaded the win version of Yahoo, and WINE wanted to install it.  Well I cancelled that out, and got the .deb pkg.  And to my dismay and confusion, the Linux version of Yahoo DOESN'T HAVE WEBCAM SUPPORT. That just seems incredibly retarded to me, but I'm sure they have their reasons.  So I went back and tried to install the Windows Yahoo(at least that supports it), and got all the way up to a message that said I didn't have IE 6.  Well no duh.  Apparently Yahoo uses dll's or something that IE uses, and it wouldn't run at all.  After doing some Googling, I came across GAIM-vv, a fork of GAIM that SUPPOSEDLY lets you view, but not broadcast, webcams. Well, when I went to view a friend's, they showed up as a green parakeet(which was pretty funny actually).  Maybe I don't have all the req'd libs or something for it, I'm not sure.  But anyhow, yeah I can't justify using WINE just for Zmud if the prog flakes out on me at random times.

---

### Post by KarmaKing on 2006-06-05
thanks for the reply and great story, but doesn't get me any closer to what I need.
I am pretty close to saying goodbye to windows, but alot stems on a few applications that I use frequently.

need solutions.

I know from a previous thread that Codeweavers has something that will work, but can't afford that right now.

peace

---

### Post by localzuk on 2006-06-05
Take a look at [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine) for information on installing wine.

---

### Post by Matthew Bartram on 2006-06-05
I think just running winecfg is enough to set it up. You might need to go to drives and tell wine to use your windows C as C, instead of its own.

Presumably you've mounted your windows drives?

Then you should be able to run any windows program just by double-clicking it (or right-click, and choose 'Open with "Wine Windows Emulator"')

You don't need to use sudo for winecfg, I don't know if it makes any difference.

Try installing libjack.so from synaptic, since that's what your terminal said was missing. 
I haven't got it on synaptic on my computer, but libjack0.100.0-0 is installed. I don't know what it is, but if you haven't got it installed, particularly if libjack.so isn't there, you could try installing it.

---

### Post by Matthew Bartram on 2006-06-05
What sort of applications do you use frequently? There might be linux alternatives available.

---

### Post by Kilz on 2006-06-05
[QUOTE=KarmaKing]thanks for the reply and great story, but doesn't get me any closer to what I need.
I am pretty close to saying goodbye to windows, but alot stems on a few applications that I use frequently.

need solutions.

I know from a previous thread that Codeweavers has something that will work, but can't afford that right now.

peace[/QUOTE]

[You could use sidenet to setup wine]("http://sidenet.ddo.jp/winetips/config.html"). I wouldnt use the setup IE or Windows media player options as they only work with wine 9.11 and up. The wine in synaptic is only 9.9. But it will setup drives, and the windows .dll's. 
Also realize that wine is a kind of emulation (I know what wine stands for Wine Is Not an Emulator) It isnt perfect. It isnt going to run all windows programs. [You may be better off looking for Linux programs with the same fuctionality]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software"). Check the [Wine Application Batabase.]("http://appdb.winehq.org/") to see if the application is suported, and/or tricks to get it running.

---

### Post by Matthew Bartram on 2006-06-05
[QUOTE=Kilz]I wouldnt use the setup IE or Windows media player options as they only work with wine 9.11 and up. The wine in synaptic is only 9.9.[/QUOTE]

If you use [automatix]("http://ubuntuforums.org/showthread.php?t=177646") to get wine, it gets the latest (0.9.14)

---

### Post by Kilz on 2006-06-05
[QUOTE=Matthew Bartram]If you use [automatix]("http://ubuntuforums.org/showthread.php?t=177646") to get wine, it gets the latest (0.9.14)[/QUOTE]

Thanks for the info, but I cant use automatrix. I run 64 bit Dapper. But anyone running the 32 bit version that reads the thread can. :)

---

### Post by tdrusk on 2006-06-05
So you installed WINE but when you RIGHT click an .exe file there isn't an option to open with WINE. 

Okay if you haven't tried rebooting try it. First try Ctrl+Alt+backspace. If that doesn't work try a full reboot.

---

### Post by phend-one on 2006-06-05
Sorry to threadcrap, but do you have to install Windows after you've installed wine from the command prompt/synaptic? Does it matter which version you install if you do?

---

### Post by Matthew Bartram on 2006-06-06
phend-one: You shouldn't have to install windows at all to use wine, but if it's installed already (or if you install it afterwards) you can use it and the programs installed in it, and I think you can even get wine to use some of its DLLs (but I don't know how useful that is).

Kilz: can't you just get the .deb file(s) for wine off winehq (or perhaps google? - with their patches)?

---

### Post by Kilz on 2006-06-06
[QUOTE=Matthew Bartram]phend-one: You shouldn't have to install windows at all to use wine, but if it's installed already (or if you install it afterwards) you can use it and the programs installed in it, and I think you can even get wine to use some of its DLLs (but I don't know how useful that is).

Kilz: can't you just get the .deb file(s) for wine off winehq (or perhaps google? - with their patches)?[/QUOTE]

I could, and might end up doing that, but 9.9 runs everything I need it to. I used ies4linux to install IE for the 2 pages I need it for. I have learned that there is no need to get the latest packages if everything is working because sometimes it breaks things. :mrgreen:

---

