---
title: "i sware my comp esploded"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by skaspud on 2007-07-14
right now i have a mil things wrong with ubuntu
big ones:
1. i can't get beryl to work
2. i can't get wine to work
3. i can't get windows on my other harddrive to boot

1. i have beryl fully installed using [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI)
i have the driver for my ati x850 pro working fine and everything
the lil beryl icon just sits up top and chills there not doing anything, i've rightclicked-window manager and tried switching to beryl from gnome and it would reload the windows and everything but nothing happened...

2. i've got wine all downloaded and installed, i have it installed but i can't get it to start up,it's not in the applications menu.

3 this is a big one...
i installed ubuntu 6.06 on a second hard drive in my computer, using this i was easily able to switch from ubuntu and back to windows by just switching the bios when booting up. but after i installed 7.04 i tried booting the windows bootup from the bootup menu that ubuntu shows, it starts the windows splash screen but then it doesn't work, it tries loading up GRUB. then says error17 (i think). I can access my C: partition from ubuntu when its hooked up, but i need the stuff from my other partitions. especially the programs and such.

Thanks (hopefully) in advance :]

edit:
i installed my graphics driver using envy- in case it helps...

---

### Post by Noodels on 2007-07-14
Okay, I had the same problem with Beryl and wine doesn't work quite like that.

Step 1 : You're gonna wanna fix your dual boot as soon as possible, I'm no expert at dual boots and I jumped straight into ubuntu because I couldn't be bothered with one. But whatever you do fix that first else all the other stuff you do could end up wasted.

Step 2 : Wine works through the terminal, when you have a .exe file go to it's directory and type WINE <filename>.exe , I *think* that's how it works.

Step 3 : Right click on Beryl Manager in the top tray, go to select window manager and choose Beryl. There are many problems and solutions, my problem was similar and this was my solution.

PS. A more appropriate title would have been nice btw, but no pressure. I've seen worse, like when people make a whole block of text out of leet, not pretty I tell you.

---

### Post by Hendrixski on 2007-07-14
> **Noodels said:**
> 
I've seen worse, like when people make a whole block of text out of leet, not pretty I tell you.

yikes... didn't 1337 die in the 80's or something?

Anyway beryl can be tricky but mostly becase the drivers are tricky.  you may think your drivers are properly installed but then you'll run a command to check and they're all like "hah hah... I tricked you!"

I blame the stupid companies that refuse to write open drivers for Linux.  The result is that it's really hard to get their products to work right.  Just bad business on their part.

Do you _need_ wine?  I bet you don't.  But if you do then you don't launch it separately, you launch a Microsoft program that uses wine. 

I would recommend finding people in your area who can sit down and help you with this stuff... like a LUG (linux users group) or a Loco team (check the link on the front page of ubuntuforums about the LoCo teams).

**and welcome to the community!!! :-)**

---

### Post by jfinkels on 2007-07-14
> **skaspud said:**
> right now i have a mil things wrong with ubuntu
big ones:
1. i can't get beryl to work
2. i can't get wine to work
3. i can't get windows on my other harddrive to boot

Please post one thread for each problem, it will facilitate the troubleshooting process for all of us!
> 
1. i have beryl fully installed using [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI)
i have the driver for my ati x850 pro working fine and everything
the lil beryl icon just sits up top and chills there not doing anything, i've rightclicked-window manager and tried switching to beryl from gnome and it would reload the windows and everything but nothing happened...

Start the beryl-manager from the terminal, and see if you get any error output. Open a terminal before starting beryl and type:```
beryl-manager
``` Then try enabling it from the tray icon's menu if it is not already enabled, and see if there are any error messages.

You may need to do some editing of the file /etc/X11/xorg.conf, but we can't really tell without some more information.

> 
2. i've got wine all downloaded and installed, i have it installed but i can't get it to start up,it's not in the applications menu.

Open the terminal in "Applications > Accessories > Terminal", browse to the directory containing the executable file you want to run like this:```
cd /path/to/directory
``` and type the following```
wine file.exe
```
> 
3 this is a big one...
i installed ubuntu 6.06 on a second hard drive in my computer, using this i was easily able to switch from ubuntu and back to windows by just switching the bios when booting up. but after i installed 7.04 i tried booting the windows bootup from the bootup menu that ubuntu shows, it starts the windows splash screen but then it doesn't work, it tries loading up GRUB. then says error17 (i think). I can access my C: partition from ubuntu when its hooked up, but i need the stuff from my other partitions. especially the programs and such.

Well you can always manually mount the other partitions from Ubuntu if you want to do that. Just do ```
mount /dev/sd*X**#* /path/to/mountpoint
```where *X* is the letter that represents the physical disk that holds the partition, *#* is the number of the partition you want to mount, and /path/to/mountpoint is any folder. You can view the layout of your drives using the following command:```
sudo fdisk -l
``` That's one easy way to get data from your partitions into Ubuntu.

Or you can fix up your GRUB to enable you to boot from Windows. I suggest making a new thread for that, or searching. You will have to manually edit your /boot/grub/menu.lst file to add your Windows installation to the list of bootable partitions. This will ultimately be easier than manually changing your BIOS and restarting your computer every time :P
> 
Thanks (hopefully) in advance :]

edit:
i installed my graphics driver using envy- in case it helps...
I think envy installs drivers for nVidia graphics cards...that may be a problem :P

EDIT: Also, please try to avoid posting your problems in more than one thread, it is easier for all of us to coordinate our efforts that way! Thanks.

---

### Post by Noodels on 2007-07-15
> **Hendrixski said:**
> yikes... didn't 1337 die in the 80's or something?

Apparently not, try [http://www.runescape.com/](http://www.runescape.com/) and have a look at the forums, particularly the suggestions forum. But whatever you do DON'T PLAY THE GAME IT IS A WASTE OF YOUR LIFE!!

> **jfinkels said:**
> I think envy installs drivers for nVidia graphics cards...that may be a problem :P

I completely forgot about the drivers!! To get mine working I went to System --> Administration --> Restricted Drivers Manager. The rest from there was pretty painless, it practically installed itself, didn't even need Synaptic.

---

### Post by skaspud on 2007-07-18
envy does ati too, and with auto configuring xorg.conf

o and i haven't been able to get on my comp yet. sorry i will tell you as soon as i can, thanks sooooooooooooooo much for teh help, beryl is like one of the main reasons i installed ubuntu.

o aaaaannnndddd
ya, thanks i got wine to work idntk that...

---

### Post by codenametiger on 2007-07-18
> **Noodels said:**
> Okay, I had the same problem with Beryl and wine doesn't work quite like that.

Step 1 : You're gonna wanna fix your dual boot as soon as possible, I'm no expert at dual boots and I jumped straight into ubuntu because I couldn't be bothered with one. But whatever you do fix that first else all the other stuff you do could end up wasted.

Step 2 : Wine works through the terminal, when you have a .exe file go to it's directory and type WINE <filename>.exe , I *think* that's how it works.

Step 3 : Right click on Beryl Manager in the top tray, go to select window manager and choose Beryl. There are many problems and solutions, my problem was similar and this was my solution.

PS. A more appropriate title would have been nice btw, but no pressure. I've seen worse, like when people make a whole block of text out of leet, not pretty I tell you.

Wait a minute. I think his right most of the way, but linux doesn't run .exe extensions. (but I totally agree w/ what he said about 1337!) Anyway, good luck..

P.S. if you were trying to run a .exe file, I know the problem. Go to the source URL (the place where you got it unless it came with the system) and download the linux version.

---

### Post by Celegorm on 2007-07-18
> **Noodels said:**
> Apparently not, try [http://www.runescape.com/](http://www.runescape.com/) and have a look at the forums, particularly the suggestions forum. But whatever you do DON'T PLAY THE GAME IT IS A WASTE OF YOUR LIFE!!

You could say the same of almost any mmo. I think runescape is quite fun personally.

More on topic, > Wait a minute. I think his right most of the way, but linux doesn't run .exe extensions Linux doesn't run .exe files, but wine does.

---

