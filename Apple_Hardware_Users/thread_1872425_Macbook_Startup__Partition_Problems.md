---
title: "Macbook Startup / Partition Problems"
date: 2011-10-30
forum: Apple Hardware Users
---

### Post by josh6680 on 2011-10-30
Sorry if this isn't the right place to post this.

I will start by going through the steps before the problems occurred.

It all started with an update. (Before this update, everything was working perfectly fine.)
I hadn't updated Xubuntu 11.04 in a while, so I checked for updates.
It said that there were a couple hundred updates, and it also said that there was a new version of Xubuntu available and gave the option to upgrade.
I clicked upgrade and went through the upgrade installation process with no problems (supposedly).
It then prompted me to restart, and I did so.
The first problem then occurred.
I tried booting into Xubuntu partition, but only got a flashing underscore. (Black screen with white _ flashing in top left)
So I decided to ignore it for now, and just shut it down and left it alone.

Some things about my computer:
Model: Macbook 1,1
RAM: 1GB x 2
Triple booted system: Mac OS X, Xubuntu, Windows XP
It also has rEFIt installed as the boot loader.
(I can get more information if needed)

Everything (except Xubuntu) was working like normal for a while before the next problem.
I booted into Windows, and everything was going fine for a while, but then it appeared to "freeze". I could still click buttons - with no effect - like pressing the close button on an application did nothing, minimize did nothing, start menu did nothing, Ctrl+Alt+Delete did nothing, power button did nothing, etc.
So I held down the power button to shut it off. I didn't use it the rest of the day.
The next time I went to use my computer, it turned on, but then when I booted Windows, there was just a Blinking Underscore.
...
I also tried booting Mac OS X, but it was taking incredibly long to boot, I left it for a while, and it loaded the login screen, I logged in, and then it took another long while loading the desktop - not normal. I tried accessing the Windows partition from OS X (using Tuxera NTFS) - Error occured, and Mac reported 0 files, but still calculated free space and total space correctly.

I then shut off the computer, and tried fixing Windows. I started up from the Windows disk and pressed 'r' for the repair console, I tried [FONT=Courier New]chkdsk[/FONT], but it got to 25% and reported "One or more unrecoverable errors". I tried [FONT=Courier New]fixboot[/FONT], it said it was successful (but I doubt it was). I then typed [FONT=Courier New]dir[/FONT], and it said 'An error occurred while enumerating file directory tree' (something like that).

I then typed exit, and shut the computer off.
I turned it back on, and this time, no operating systems work.
Mac OS X just gets a Kernel Panic error,
Windows says:
[FONT=Courier New][SIZE=2]Invalid BOOT.INI file
Booting from C:\windows\
NTDETECT failed[/SIZE][/FONT]
and Xubuntu just has a blinking underscore.

I can still boot from Xubuntu Live CD perfectly fine.
When booted from the Live CD, it can mount my Xubuntu partition with no problems and it looks okay.
It gets an error when mounting the Mac OS X partition, and it doesn't even find the Windows partition.
[FONT=Courier New]fdisk -l[/FONT] shows the Windows partition as [FONT=Courier New]/dev/sda1[/FONT] though.

Any help is appreciated. 

I can get more detailed information using the Live CD if I need to.[FONT=Arial][SIZE=1][COLOR=Gray]
[/COLOR][/SIZE][/FONT]

---

### Post by josh6680 on 2011-11-01
Never mind, the Hard Drive is physically damaged.

---

