---
title: "My first 12 hours of a Linux"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by nathanscottdaniels on 2008-01-25
I have had Windows all my life and I love it but I decided to have an open mind and try Linux out.  I now have Xubuntu 7.10 dual-booting with XP on my laptop.  

WOW THIS IS STRANGE!  So much stuff I never heard of before! xfce? bash? :confused:

I thought I knew a lot about computers but now I feel stupid.  Linux (or maybe just Xubuntu) is SO BUGGY!  It took me 3 hours to get my screen working and another 2 hours to get online.  

But enough with my complaining.  I plan to make Xubuntu the only OS on my laptop in the near future when I (finally) get a decent desktop.  So I need a few questions answered.  

1. It's impossible to run exe files right?
2. How do I make it so that Windows XP is the default OS when it prompts which one I want to run when I turn on my computer? You know, so after 10 seconds, XP loads and not Xubuntu.
3. Why do so many programs just close on me without any warning?  They just go poof!
4. Why is the scroll wheel on my Microsoft (I think that answers my question) mouse SO SLOW?
5. What is the Xubuntu equivalent of Windows' Task Manager?

Thank you all in advance for helping me out.

---

### Post by mivo on 2008-01-25
Welcome to Linux, and to the Ubuntu community. :)  Don't worry about feeling "stupid"! That is perfectly normal -- it's an entirely different environment and OS, so it's much like moving to a foreign country with a  very different culture.

To answer some of your questions:

**1. It's impossible to run exe files right?**

Not impossible. Wine is a program that allows you to run some Windows applications in Linux, almost as if you were using Windows. With some applications this works well, even perfectly fine, with others there are problems and a bit of tweaking is required, and some won't work sufficiently at all. As a rule of thumb, the newer and more complex a Windows program is, the more unlikely it is to run well in Wine. Wine is free software, so you can download it from the repository.

**3. Why do so many programs just close on me without any warning? They just go poof!**

This shouldn't happen. Could you name some programs that do this? It seems that there is some other problem.

Could you tell us a bit more about your computer? What processor, how much memory, etc -- that kind of stuff. Ubuntu (the Gnome version) may be better suited, and there tends to be better support for it. But without knowing your laptop's specs, it's hard to tell whether this might be a viable option.

Again, welcome to Linux! It is going to be a challenging but fun and educating ride! :)

---

### Post by Tyke91 on 2008-01-25
1. you can run many .exe files using the WINE compatability layer, but you will want to install things through synaptic and .deb fiiles, not .exe

2. go to a command line and type ```
gksudo gedit /boot/grub/menu.lst
``` then scroll down until you see the familiar table of OSes... copy and paste Windows to the top of the table

3. which programs?

4. in  your system menu, look for something that looks like mouse controls. edit those in order to speed the scroll wheel.

5. system monitor.

---

### Post by JoshuaRL on 2008-01-25
1.  Maybe.  There's two options that are the most popular and most successful.  Wine is a compatibility layer that runs in Linux and runs most programs.  But not all.  The other option is slower, but will definitely work once you get it running.  That's running a virtual windows computer and running programs in that.  But if you're running games that won't work well.

2.  You would have to change the /boot/grub/menu.lst file so that it reads default next to your windows partition.

3.  Not sure.  You might try running them from the terminal so that it will give you the errors.  We can help you on an individual app basis.

4.  That's what the setting are I believe.  You might want to monkey around in the Preferences Menu to see if you can change that.  If not, I'm sure there is a way from the command line.  I just don't know it.

5.  System Moniter.

And welcome from the Ubuntu Community.  If you were able to get your video card and wireless working you're doing great.  In fact, I bet you could help out some new people here on Absolute Beginners Forums.

And I know you probably know this by now, but XFCE is a desktop manager, my favorite, and bash stands for Bourne Againe SHell.  It is a scriping language for the terminal.

---

### Post by nathanscottdaniels on 2008-01-25
Wine didn't work for the program I tried (YPops)  but I will try some more later.

Some of the programs that crash include that connect four game as well as a lot of other games, Firefox did once, and the file manager does when I try to access certain drives.

There is no scroll speed setting in any of the GUI-based preferences.  I will research some of the command-based options.

I have a low-end gateway laptop which is why I got Xubuntu instead of ubuntu (I heard xubuntu was for lower-end systems).

specs from the top of my head- 

1.7 GHz AMD Turrion 64 processor
ATI Radeon Xpress onboard graphics with 60 MB shared mem.
1.5 GB RAM (1GB was added by me)
Basic 1280 x 800 60 hz laptop monitor
Gateway MX6441 Motherboard
some strange sweedish sound card
Broadcom 802.11 wireless adapter as well as regular LAN

---

### Post by eriqjaffe on 2008-01-25
> **Tyke91 said:**
> 2. go to a command line and type ```
gksudo gedit /boot/grub/menu.lst
``` then scroll down until you see the familiar table of OSes... copy and paste Windows to the top of the tableIn Xubuntu, that should be:```
gksu mousepad /boot/grub/menu.lst
```...gedit isn't installed with Xubuntu by default.

---

### Post by nathanscottdaniels on 2008-01-25
> **eriqjaffe said:**
> ...gedit isn't installed with Xubuntu by default.

I downloaded it though

---

### Post by mivo on 2008-01-25
Hardware is fine for the Gnome-based Ubuntu. I'd go with that unless you had a specific reason to choose Xubuntu?

---

### Post by sumguy231 on 2008-01-25
In menu.lst it's actually better to change the line that says:
```
default 0
```
Near the top to the number, counting from 0, for the Windows entry in the boot list. This will automatically select Windows.

---

### Post by JoshuaRL on 2008-01-25
I have a 3ghz P4 laptop and I use Xubuntu because it's so much faster.  It's not just for computers that can't handle.  But it works for them too.  :p

---

### Post by prshah on 2008-01-25
> 1. It's impossible to run exe files right?
2. How do I make it so that Windows XP is the default OS when it prompts which one I want to run when I turn on my computer? You know, so after 10 seconds, XP loads and not Xubuntu.
3. Why do so many programs just close on me without any warning? They just go poof!
4. Why is the scroll wheel on my Microsoft (I think that answers my question) mouse SO SLOW?
5. What is the Xubuntu equivalent of Windows' Task Manager?


1) You can run .exe files by just (double)clicking on them if you have WINE installed. To install WINE, type the command "sudo apt-get install wine" in a terminal (Applications->Accessories->Terminal).

2) To change the order of booting os's, do the following:
     a. Open Applications->Accessories->Terminal
     b. type the command "sudo mousepad /boot/grub/menu.lst", then enter your admin password when asked
     c. find the section containing your windows entries, then select and cut the entire section
     d. from the top, search for a line containing "begin automagic"
     e. Paste before the "begin automagic" line
     f. you can also change the timeout if you want, search for "timeout"
     g. save and exit mousepad text editor
     h. in the terminal, type the command "sudo update-grub"

3) If certain programs close on you without warning, try to launch the programs from a terminal, then if and when the programs go POOF (sic), take a peek at the terminal for error messages. Post those error messages here or google for them. You can also check if any debugging information is availible using the command "dmesg | tail -15" in a terminal.

4) check in your "/etc/X11/xorg.conf" (pay attention to case) to see if your mouse is recognized as a MS mouse. If not, use the command "sudo dpkg-reconfigure xorg" and select the appropriate mouse when asked.

5) It depends on the task (pardon the pun!) you want to do: In a terminal:
     a. Use the command "top" to study running processes and resources
     b. use the command "users" to see logged on users
     c. use the command "kill" to stop process / programs

     ...though you usually would not need any of these commands. 

Though you consider your laptop specs as "low-end", I would run Ubuntu on that. I use XUbuntu for an old Pentium III 550Mhz, 384Mb RAM, 10Gb HDD. I also ran it on a Celeron 266/192Mb/2.1Gb, before I switched over the DSL (damn small linux).

Point in passing: YPops! is also availible for linux.

And, just nitpicking: the specs are "off the top of your head" not "from the top..."

Cheers,
PRShah

---

### Post by Tylazene on 2008-01-26
Just a quick suggestion from one noob to another. You might not want to get rid of XP too soon. I found that sometimes I got frustrated not knowing how to do some things in linux and went back to windows when needed. It might take a while to learn everthing you need to even in Ubuntu.

---

### Post by bwtranch on 2008-01-26
Wine aka vino is not a solution and I forgot it years ago. Their attempts at compatibility are lame and a waste of time for everybody. The focus here should be, and actually has been, working with Unix based apps that do the job. Not doing a workaround windows from Jobs.

Many people, including some well meaning sorts think that this is the way to go...but, that just the Microsoft way. Linux was created to free the mind, and not keep up with the corporate industrial complex. But, it is doing that anyway. Go figure?

---

### Post by Madpilot on 2008-01-26
> **nathanscottdaniels said:**
> 
I have a low-end gateway laptop which is why I got Xubuntu instead of ubuntu (I heard xubuntu was for lower-end systems).

specs from the top of my head- 

1.7 GHz AMD Turrion 64 processor
ATI Radeon Xpress onboard graphics with 60 MB shared mem.
1.5 GB RAM (1GB was added by me)
Basic 1280 x 800 60 hz laptop monitor
Gateway MX6441 Motherboard
some strange sweedish sound card
Broadcom 802.11 wireless adapter as well as regular LAN

That's not really a low-end laptop - it will run Ubuntu just fine!

You might want to switch up from Xubuntu to Ubuntu; much as I really do like Xubuntu and XFCE, Ubuntu (with Gnome) is a good bit more user-friendly and polished than XFCE.

You can tweak your existing install of Xubuntu to basically turn it into Ubuntu, or just reinstall. Or even triple-boot, with a complete Ubuntu install alongside your existing Xubuntu & XP installs.

But if Xubuntu is working for you, stick with it!

---

### Post by sumguy231 on 2008-01-26
> **bwtranch said:**
> Wine aka vino is not a solution and I forgot it years ago. Their attempts at compatibility are lame and a waste of time for everybody. The focus here should be, and actually has been, working with Unix based apps that do the job. Not doing a workaround windows from Jobs.

Many people, including some well meaning sorts think that this is the way to go...but, that just the Microsoft way. Linux was created to free the mind, and not keep up with the corporate industrial complex. But, it is doing that anyway. Go figure?

Wine is far improved from years ago, and runs some Windows applications decently. Some people would rather be productive than "free their minds" from the "corporate industrial complex". Are you serious?

---

### Post by ugm6hr on 2008-01-26
> **Madpilot said:**
> That's not really a low-end laptop - it will run Ubuntu just fine!

You might want to switch up from Xubuntu to Ubuntu; much as I really do like Xubuntu and XFCE, Ubuntu (with Gnome) is a good bit more user-friendly and polished than XFCE.

You can tweak your existing install of Xubuntu to basically turn it into Ubuntu, or just reinstall. Or even triple-boot, with a complete Ubuntu install alongside your existing Xubuntu & XP installs.

But if Xubuntu is working for you, stick with it!

I would agree.  If you are a beginner, it is easier to get help for Ubuntu than Xubuntu.

Gnome (Ubuntu) is more intuitive than XFCE too.  And the Gutsy (7.10) Xubuntu seems to have most of the same apps anyway - so I think the "low end" suitability is not as true as previously.  Besides which - your "low end" laptop is pretty similar in spec to mine!

If you want to try Gnome / Ubuntu:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

You can later remove XFCE with: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by bwtranch on 2008-01-26
Re # 15 Yeah, I'm serious or I wouldn't have wrote it.

Re# 16 I think this suggestion is good. This person and I have been on some posts and I trust that opinion.

---

### Post by jfinkels on 2008-01-26
> **nathanscottdaniels said:**
> 
1. It's impossible to run exe files right?

Correct. You cannot execute executable files that were compiled to run on Windows computers.
> 
2. How do I make it so that Windows XP is the default OS when it prompts which one I want to run when I turn on my computer? You know, so after 10 seconds, XP loads and not Xubuntu.

Open the terminal and type:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
to make a backup copy of this file, then edit it by typing:```
sudo nano /boot/grub/menu.lst
```
Scroll down to the line that says "default" and change the number that is there to the number of the entry for the Windows boot menu option (remember, the options are indexed starting from 0!). Then press Ctrl X to quit, Y to save, and Enter to confirm.
> 
3. Why do so many programs just close on me without any warning?  They just go poof!

Perhaps you have an unlucky combination of hardware and software. If you open a program from the terminal by typing its name (usually), you might get more detailed info on why the program is terminating prematurely.
> 
4. Why is the scroll wheel on my Microsoft (I think that answers my question) mouse SO SLOW?

I don't know.
> 
5. What is the Xubuntu equivalent of Windows' Task Manager?

I don't know. But if you want to kill a running process, there's a couple of things you can do. For example, if you want to kill the program called "thunderbird", then open the terminal and type:```
killall thunderbird
```

> **nathanscottdaniels said:**
> Wine didn't work for the program I tried (YPops)  but I will try some more later.

Take a look at [http://appdb.winehq.org/](http://appdb.winehq.org/) for more info about programs that run with Wine.
> 
I have a low-end gateway laptop which is why I got Xubuntu instead of ubuntu (I heard xubuntu was for lower-end systems).

specs from the top of my head- 

1.7 GHz AMD Turrion 64 processor
ATI Radeon Xpress onboard graphics with 60 MB shared mem.
1.5 GB RAM (1GB was added by me)
Basic 1280 x 800 60 hz laptop monitor
Gateway MX6441 Motherboard
some strange sweedish sound card
Broadcom 802.11 wireless adapter as well as regular LAN

That's considered low end these days!? I consider that a pretty good system. You should have no problem running GNOME-based Ubuntu, which, as was said earlier, will be easier for other people to help you with.

Let us know if you have any other questions! We're very happy to help.

---

### Post by mivo on 2008-01-26
> **bwtranch said:**
> Wine aka vino is not a solution and I forgot it years ago. Their attempts at compatibility are lame and a waste of time for everybody.

I need one Windows application (the application of my employer) to run, and it works flawlessly in Wine. The programmers made a few tweaks, and that was all that was needed. The company is not currently willing to develop a native Linux version (matter of budget and personnel, and support), but since the existing Windows software works fine in Wine, that is all right. So, Wine hasn't been "a waste of time" for me, and without Wine, I'd not have been able to completely switch to Linux. Dual-booting was never a viable option for me personally.

---

### Post by prshah on 2008-01-26
> **bwtranch said:**
> Wine aka vino is not a solution and I forgot it years ago. Their attempts at compatibility are lame and a waste of time for everybody. The focus here should be, and actually has been, working with Unix based apps that do the job. Not doing a workaround windows from Jobs.

Many people, including some well meaning sorts think that this is the way to go...but, that just the Microsoft way. Linux was created to free the mind, and not keep up with the corporate industrial complex. But, it is doing that anyway. Go figure?

Maybe you should take a fresh look at Wine if you really have given it up "years ago".

I specifically needed Wine because the only critical Windows program for me was my stock terminal trading software from ShareKhan, called SpeedTradePlus. Nope, QTStalker cannot do the same thing since this is a customised version suitable for ShareKhan's operations.

Only caveat: SpeedTrade works only if I run Wine as "sudo" which I know is risky...

Cheers,
PRShah

---

### Post by gn2 on 2008-01-26
One thing I noticed was you said that the file browser (Thunar?) closes when you try to access certain drives.
Are these NTFS, and do you have ntfs-3g installed?
Also, do you have the required permissions to access the files?

---

### Post by BobCFC on 2008-01-26
1.5gb is fine for the full Ubuntu desktop.  XFCE is designed for 512mb or less really.

Once you have gnome installed the friendly equivalent of Task Manager is found in the menu System->Administration->System Monitor

You can see a list of processes and order by CPU or memory, see graphs of CPU use and also the free space on you partitions.

---

