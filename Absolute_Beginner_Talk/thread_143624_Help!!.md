---
title: "Help!!??"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by matthewinuk on 2006-03-12
:confused: I apologise if I broke any rules wiht the content of this post.

I am COMPLETELY new to ubuntu and came across it on theopencd. It looks good but im lost amongst all the information. I need a simple beginners guide.
Also I need to know four things.

1. How can I install ubuntu and have the option of using either ubuntu or the MS windows XPSP2 which is already installed on my computer?

2. How can I use software which was made for windows on this OS? Is it possible?

3. Where is the EASIEST place to find software. for example if I wanted a working mp3 player.

4. what is kubuntu? what is the difference.

me = n00b, but i dont mind.:confused: :confused:

---

### Post by taurus on 2006-03-12
1.  Make sure you have an empty partition first so you can install Ubuntu on that!  If you don't, you need to use Partition Magic to resize your current HD to leave some empty space for Ubuntu and you can leave that empty space in fat32 format.  Or get a second HD and install Ubuntu on that.  Then, make sure you install GRUB on MBR so it will handle booting both Ubuntu and XP on your machine.

2.  You can run Windows programs in Ubuntu with an emulator--wine.  However, I recommand you use the ones that come with your Ubuntu system.  Just give the names that you need to use in Windows and we will tell you what programs behave the same fashion in Linux.

3.  No need to look anywhere specific since either apt-get (terminal base) or synaptic (GUI) can install everything else you want.

4.  Kubuntu is Ubuntu except it is using KDE as it window manager while Ubuntu uses Gnome.    Some people like using Gnome while others like using KDE.  You can have both Gnome & KDE on your system and you can pick which one you want to log in at the login screen.

5.  And welcome to Ubuntu...

---

### Post by Sutekh on 2006-03-12
[QUOTE=matthewinuk]:confused: I apologise if I broke any rules wiht the content of this post.

I am COMPLETELY new to ubuntu and came across it on theopencd. It looks good but im lost amongst all the information. I need a simple beginners guide.
Also I need to know four things.

1. How can I install ubuntu and have the option of using either ubuntu or the MS windows XPSP2 which is already installed on my computer?[/QUOTE]The Ubuntu installer will give you the option of installing the GRand Unified Bootloader (GRUB),  the GRUB is capable of booting multiple OS.  Windows is no problem.  

You should have a read of this great graphical installation guide.  
There are guides to installing Ubuntu with Windows (NTFS and FAT32)

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")


[QUOTE=matthewinuk]
2. How can I use software which was made for windows on this OS? Is it possible?[/QUOTE] It *may* be possible though [Wine](www.winehq.com)

You should check out their [application database](http://appdb.winehq.org/) for the software you are interested in.

[QUOTE=matthewinuk]
3. Where is the EASIEST place to find software. for example if I wanted a working mp3 player.[/QUOTE]In Ubuntu the package manager **Synaptic** is used to install software, it is very easy to use.  

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

[http://www.psychocats.net/essays/winuxinstall.php]("http://www.psychocats.net/essays/winuxinstall.php")

As for MP3 players there are so many to choose from

 - Rhythmbox
 - XMMS
 - BMP
 - Amarok
 - Quod Libet
 - Listen
 - the list goes on.

[QUOTE=matthewinuk]
4. what is kubuntu? what is the difference.

me = n00b, but i dont mind.:confused: :confused:[/QUOTE]Kubuntu is basically the same as Ubuntu except it uses [KDE](www.kde.org) as its desktop environment as opposed to [GNOME](www.gnome.org)

---

### Post by andrewsawyer on 2006-03-12
1. When you install, grub (the bootloader) should autodetect Windows.  You will then be able to boot Windows by hitting the escape key at bootup.  You can of course swap this so Windows loads as default and you need to hit ESC to boot Ubuntu.

2. Depending on the software there is WINE which will allow you to run Windows applications like MS Office etc inside Linux.  You can also used paid-for software Codeweavers Crossover Office, which is basically WINE with a nice front end.  Alternatively you can install VMWare which allows you to boot Windows from inside Linux.  Obviously the latter will need more RAM.

3. Synaptic (System >> Administration >> Synaptic Package Manager) which is available from the menu bar at the top of the screen.  Do a search for a key phrase and it will show applications that can be downloaded for free over the net.  Just hi-light the app and download.

4. Kubuntu uses the KDE desktop, which Ubuntu uses the Gnome desktop.  It is user preference as to which you prefer, however I would advise you that you will probably find more help when using Ubuntu as the community will be larger, and therefore more people to help.

You might want to try having a look through the WIKI or [http://www.ubuntuguide.org](http://www.ubuntuguide.org) - please note though that the latter may be a little out of date and some links may not work - it's what I used to get started though, and it's pretty easy to follow.

You will also find that while looking through the forums, you will find stuff written like this:

```
sudo mount /dev/sda1 /media/usb
```

This is basically how people write that something has been typed into the Terminal (Applications >> Accessories >> Terminal) which is kind of like the dos prompt, only far more versitile.

I hope this post has helped you, and if you have any other questions, please post and we will try out best to help out!

Oh, and you didn't break any rules :-)

---

### Post by andrewsawyer on 2006-03-12
Beaten to it - damn!

---

### Post by aysiu on 2006-03-12
[QUOTE=matthewinuk]
1. How can I install ubuntu and have the option of using either ubuntu or the MS windows XPSP2 which is already installed on my computer?[/quote] Step one: back up all your data. Step two: follow these directions...
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

> 
2. How can I use software which was made for windows on this OS? Is it possible? Crossover Office, Wine... or just find a Linux equivalent.

> 
3. Where is the EASIEST place to find software. for example if I wanted a working mp3 player. Almost every MP3 player works with Ubuntu. Software in general...
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

> 
4. what is kubuntu? what is the difference. Ubuntu with a different look and feel. Read more about the difference between KDE (Kubuntu) and Gnome (Ubuntu) here...
[http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

---

### Post by taurus on 2006-03-12
[QUOTE=andrewsawyer]Beaten to it - damn![/QUOTE]
Just have to type faster!!!  :mrgreen:

---

### Post by andrewsawyer on 2006-03-12
Yeah - learning to touch-type is on my list of things to do!  I might even get around to it one day.

---

