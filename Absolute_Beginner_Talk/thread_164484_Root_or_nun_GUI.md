---
title: "Root or nun GUI"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-22
:mad: :rolleyes:  First of all I think that Ubuntu is a great GNU/Linux build.

Although I am a little diapointed in the fact that I recently switched to linux wanting to learn and explore the guts of linux without the GUI. I guess what I am trying to say is there a way to boot into the console without the GUI?

Also is there a way to login as root?](*,) not USER MODE?

---

### Post by gondilon on 2006-04-22
you can boot without the GUI by rebooting into single user mode.

---

### Post by catlett on 2006-04-22
you should be able to remove the gnome desktop and just have the ubuntu command line login. It shoud be ```
sudo apt-get remove gnome-desktop
``` Do a little googling first but the gui is the x window server and the (gdm) is the gnome window manager. You should be able to remove them to get just gui. Doing sudo apt-get remove gdm might do the trick as well because I believe gdm is what starts the gui session automatically.
Or you could re-install Ubuntu and type "server" at the first prompt. This will do the server install and leave out Gnome. If you just installed, this might be the easiest way to get to a command line Ubuntu

---

### Post by dermotti on 2006-04-22
You can install **bum** and just uncheck **gdm** so it doesnt load. Thats what i did. And its easily reversible.


**sudo apt-get install bum**

---

### Post by zaba on 2006-04-22
[QUOTE=Silver-revo]
I am a little diapointed in the fact that I recently switched to linux wanting to learn and explore the guts of linux without the GUI. I guess what I am trying to say is there a way to boot into the console without the GUI?[/QUOTE]

Like others have said, you are an apt-get remove away from being completely cli-based, but why not leave Gnome in case you get a little lost? You can always access a terminal (i.e. gnome-terminal) from Gnome, which gives you help with the "guts" as it were. Plus, you can always ctrl+alt+F5 (or F4 or F3 or...) after Gnome has loaded and you will be in a text only environment. 

If you explore, Ubuntu is actually a great distro to "get your hands dirty"... there are more .conf files than you will ever now what to do with!

> Also is there a way to login as root?](*,) not USER MODE?

```
su
``` :mrgreen: 

There are actually a few ways to login as root. If su doesn't suit you (or you don't have root set up yet), some of the things [here ]("http://ubuntuguide.org/index.html#usersadministration")might help.

---

### Post by 3rdalbum on 2006-04-23
There's a cheaters' way of logging in as root:

1. Log out of Gnome.
2. Switch to a terminal by hitting Cntl-Alt-F1.
3. Log into the terminal, then type "sudo shutdown now".
4. After your services have been turned off, Linux will switch into Single-User Mode (root).
5. If you have "log in automatically" turned on in the Login Screen Setup program, typing "startx" will open up Gnome as root.
6. To shut down the computer or reboot, type "halt" and look at the command line options it prints for more details.

That's the slightly-ridiculous way of doing it, which I discovered by accident.

---

### Post by aysiu on 2006-04-23
[QUOTE=catlett]you should be able to remove the gnome desktop and just have the ubuntu command line login. It shoud be ```
sudo apt-get remove gnome-desktop
```[/quote] [Actually, there isn't a package called *gnome-desktop*](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnome-desktop&searchon=name&subword=1&version=all&release=all).

---

### Post by fyrestrtr on 2006-04-23
Think maybe he meant ubuntu-desktop

Anway -- what is wrong with terminal? Its just like the command prompt, and you can launch it from within gnome.

If you really want that raw terminal feeling, ctrl+alt+f2 will get you to desktop, if you don't want the graphical login on boot, just remove gdm from the run levels.

Use bum, or since you are terminal fan :

sudo update-rc.d -f gdm remove

If you want to be root after you have logged in, just:

sudo bash && source /etc/profile

---

### Post by catlett on 2006-04-23
> sudo apt-get remove gnome-desktop

Sorry about that. Should have checked before I posted. I started with Ubuntu and did apt-get install kubuntu-desktop for KDE. So I never apt-getted gnome. But I shouldn't have posted without checking and should have been smart enough to realise I apt-getted kde by kubuntu-desktop so I little extrapolating should have led me to deduce gnome would be ubuntu-desktop (getting a little sloppy, please excuse the misinformation,I stand corrected) I hope I didn't cause you confusion or frustration at the terminal  because of my misinformed suggestion. Regards, Catlett
```

sudo apt-get remove ubuntu-desktop
```

---

### Post by aysiu on 2006-04-23
[QUOTE=catlett]
```

sudo apt-get remove ubuntu-desktop
```[/QUOTE] Actually, you're not going to believe this, either, but *apt-get remov*ing the *ubuntu-desktop* metapackage won't remove Gnome.

*ubuntu-desktop* isn't a real package--it's just a pointer to other packages. *apt-get* doesn't keep track of what gets installed along with a pointer, so when it uninstalls the pointer, it doesn't uninstall all the packages that pointer... points to.

If, however, you did a server install and then did ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
``` then this code *would* actually uninstall Gnome: ```
sudo aptitude remove ubuntu-desktop
``` because *aptitude* (unlike *apt-get*) removes the dependencies as well (provided they're not used by other packages).

---

### Post by gr0kzer0 on 2006-04-23
Personally, I much prefer to get to a command line by using Ctrl-Alt-F1 to F6, which gives you six separate terminals, and six shells. And whenever you want the GUI, it's still there, on Ctrl-Alt-F7. This gives lots of flexibility, when running multiple processes at once. Or, for instance, you're using an unfamiliar command, you can have the man page displayed on a terminal, so you can switch to it for quick reference.

As for root login... I enabled root login in console (code: sudo passwd root), and you can also allow root login into Gnome by changing the log-in options. But I rarely log in as root. Sudo is fine.

---

### Post by catlett on 2006-04-23
> Actually, you're not going to believe this, either, but apt-get removing the ubuntu-desktop metapackage won't remove Gnome.Thank goodness I'm not the only person on this forum.:!: :oops:

---

