---
title: "Duel Booting and Wine"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-07
I have a very simple question that I'm sure you guys will know the answer to.
Does Wine require Windows / Duel Boot machine or can you somehow
install the programs files to Linux.

Also what are the requirement for a program to be ran in Wine.
Does it have to be on the list or is it just hit and miss?

I have read several times that it's not an emulator,
does it run natively?

Thanks

---

### Post by celticbhoy on 2007-11-07
No need for Windows on your machine, that's kind of the point.

Some Progs outside the list will work, so yeah can be hit & miss at times.

---

### Post by Daveth on 2007-11-07
no it runs most happliy under linux and pays no heed to windows, forming its own "version" in your linux partition. Programs do not have to be on the list- as I rough rule of thumb the older and simpler a windows program is, the more chance it will run on WINE if it is not listed. I have several that run quite well and are not listed (yes, I know i should add an entry..). You lose little by trying. Be mindful that not all WINE versions are equal, neither all all windows versions it interfaces, so fiddling with the options can sometimes get things going.

---

### Post by AndyCooll on 2007-11-07
Wine essentially mimics Windows code. It does so by interpreting the commands of Windows apps into Linux code, and then Linux code back into a format the Windows app understands.

:cool:

---

### Post by Orbital75 on 2007-11-07
Good deal so it doesn't need windows at all, that's nice.
There are a few programs that I just don't think wine will
support but I will give it a shot and see.  I think I am still
going to create a duel boot just in case.

Is Wine hard to set up or is it pretty straight forward? 
I'm guessing you just set up a folder or something in your
home and install the windows files in it.

---

### Post by hogwartsnigel on 2007-11-08
I am interested in this answer as I currently only dual boot on one system to enable my kids to use Encyclopedia Britannica...so I´ll be able to use with WINE. That should free me up.
Okay how do I then make my system solo ubuntu..I know I can delete the files and partition but am scared about altering the bootloader etc.


Please advise and thanks in advance

Nigel

---

### Post by AndyCooll on 2007-11-08
No setting up required. You just install it from the repos (i.e. through Synaptic or Add/Remove Programs). It simply "kicks" in to action when a Windows file requires actioning, a bit like Open Office kicks in to action when a .doc (or whatever requires actioning). You can configure aspects of Wine by typing into a terminal (Programs > Accessories > Terminal):
```
winecfg
```

:cool:

---

### Post by hogwartsnigel on 2007-11-08
Thanks Andy
(I turn a shade of green at the cinnamon you have at your disposal, although I´m a tea drinker so what the hey....)
So I install from the disc using the emulation in WINE of the WinDOSE add programms and it will run the install programme?
When it comes to use the software..if I choose to install the full program I would simply open wine and click on the program file within it to start?...and if I choose to anly install the minimum requiring the disc....will Wine auto detect the disc when inserted or will I have to open WINE and start the program from within there?

Thanks Again
P.S. Written to Britannica to express a desire for a linux format!!!!!!

---

### Post by Orbital75 on 2007-11-08
Same here...... Do I create a folder in my Home and dump the entire window program
in that folder?  Not sure how to set it up... Could some one give a crash course
run through real quick... I'll read the manual to get the in depth stuff.
Simply put where do you place the win program and how do you run it.
What part of the win program do I need...

I clicked on the Windows program but it keep telling me that it didn't have a program to open
it.  I though you stated that wine would open it after it was installed.

Thanks guys

---

### Post by AndyCooll on 2007-11-09
Nope, no need to manually create any folders or anything. Simply install Wine from the repos as I mentioned earlier. Then navigate to your Windows app and click on the setup.exe (or whatever). 

First time Wine runs it will automatically create all its required folders, so just wait awhile for it do its configuring. Eventually your Windows app will begin the install process.

What happens is that Wine creates a mock setup of the Windows folder structure. So once installation of the app is complete, if you navigate to your home directory, press CTRL+H (which will display hidden folders) and find your .wine folder. In it you will see a folder called c_drive (or something like that, since I'm not at my Linux box at the moment I cannot recall exactly). And within that there is a folder called "Program Files" etc. And eventually within that is where your app. It's a bit like a "virtual" Windows file structure. To open your app your click on the .exe of your app.

Wine should autodetect the disc. I play Football Manager using Wine, and before the game launches it requires the disc to verify that I have a legal copy. If I forget to put the disc in it prompts me accordingly.

If Ubuntu doesn't detect that the program should be opened using Wine you may need to do this manually. One way is via the command line:
```
wine /path/to/program.exe
```

If your app still won't run under Wine you may then need to resort to dual-booting or using a virtualisation tool such as VirtualBox or VMware. The latter run a complete Windows environment within Linux.

:cool:

---

### Post by Orbital75 on 2007-11-09
You were correct.  I did have to run it from the command line. 
for some reason it just wouldn't allow me to install it just by clicking on
the Setup.exe installation file. I got the program to launch but there
are some other issues that I am going to have to make another post
to solve.  I'm trying to run Winamp and am getting a sound driver
error.... all in all I got wine up and running..... thanks again.

Thank you.....

---

