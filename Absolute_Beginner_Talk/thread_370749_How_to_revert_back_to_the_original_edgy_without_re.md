---
title: "How to revert back to the original edgy without re-installing"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Doomedelite on 2007-02-26
Hello all, I switched to ubuntu... around eight hours ago, and I still have no clue what I'm doing (twelve years using the Windows OS makes you inept at everything else), and I feel that while I was trying to install some programs, I screwed up ubuntu somehow (doesn't let me "sudo apt-get install msttcorefonts", tell me "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ", and when I run that, it gives me "dpkg: requested operation requires superuser privilege", even though I am the only user on this computer. I'm really frustrated so far, but I REALLY don't want to go back to Windows if I can help it. Is there a way to format edgy back to the original "factory" settings and programs without re-installing? This would help me tryout things without worrying about screwing up something. Thanks for your help everyone.

---

### Post by WW on 2007-02-26
**sudo** is the command that you use to run another command with superuser privileges.   If apt-get tells you to run 'dpkg --configure -a', you would give the command
>  sudo dpkg --configure -a
(Caveat: I have no idea if this will actually fix your problems with apt-get.)

---

### Post by Doomedelite on 2007-02-26
I freaking love you. *ahem* yea... Thanks for that though, it helped with all the previous problems. Anything about the "reverting back to factory settings" for edgy? Oh another question I thought I'd pop in - When I type "su", and it asks me for the password, my usual password doesn't work. Is there a default root password which I should be aware of? Thanks again!
EDIT: I get "andrew@andrew-desktop:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.31.0.1ubuntu1~edgy1) ...
Downloading...
--02:42:58--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.110.70
Connecting to fpdownload.macromedia.com|72.246.110.70|:80... "
and it just stays like that forever...

---

### Post by Doomedelite on 2007-02-26
Fixed that problem (the one above), just had to type it in repeatedly until it worked... 10th try :(

---

### Post by floke on 2007-02-26
flash is in the repositories

sudo apt-get install flashplayer-nonfree

jobdone

---

### Post by Doomedelite on 2007-02-26
Thanks, I got that all fixed, but I'm still wondering if there is a way to make your edgy "fresh" again, without all the programs installed, without having to re-install it. I'm looking for a command or something I would guess.

---

### Post by floke on 2007-02-26
No idea apart from uninstalling the progs you downloaded.
I've had to do 2-3 fresh installs after buggering things up. I consider it good practice!
If you have your home directory set on a different partition, then its no big hassle really.

---

### Post by Doomedelite on 2007-02-26
Alright, thanks for the help! :popcorn:

---

### Post by luisromangz on 2007-02-26
I think there is no automatic way to restore Ubuntu (nor any other distro) to "factory defaults". And well about a root's password so you can use "su", try simply "sudo su".

Good luck!

---

### Post by madsurfer on 2007-02-26
Hi

I have a simular problem, been using Ubuntu for several weeks now and have installed several (lots!) programs, while changing from the default evolution to thunderbird I have lost my email icon and also the alacarte menu from accessories. note if I type either of the programs in the shell  both start up if I put the path into where the exe is. How do I restore them back to the original settings? So far have been happy with Ubuntu but this is driving me wild!!

Adrian

---

### Post by tbraun on 2007-02-26
Hello, and welcome to Ubuntu!

Honestly, I don't know of a single command, which would revert an entire Ubuntu installation back to the 'factory settings' (so to speak). However, there are two approaches that seem to work. For both, however, it would be a good idea to create separate partitions for your /home directory (vs. 'the rest').

Once you have /home in a separate partition, you can do two things easily:

[LIST]
[*] Make backups of your system partition, which can then be easily reinstalled, if something should get screwed up. I have a friend who does that, but he uses a Windows (!) program for that task. Does anyone know of a good Linux program that can do the same?
[*] Reinstall the OS, without wiping/disturbing your home directory. That way then, you don't loose your documents, bookmarks, or all your personal Desktop settings and such. Sure you then do have to go through a reinstall, but after answering some initial questions, most of that can happen on its own.
[/LIST]

I use the last option, since I also like to make fresh installs when a new version of Ubuntu comes out. I remember all the additional packets and applications I install in a little text file, where it then says things like:

```

    yes | sudo apt-get install build-essential
    yes | sudo apt-get install gcc-doc
    yes | sudo apt-get install autoconf
    yes | sudo apt-get install automake
    yes | sudo apt-get install libtool
    yes | sudo apt-get install manpages
    yes | sudo apt-get install manpages-dev
    yes | sudo apt-get install tcsh
    yes | sudo apt-get install python-all-dev
    ...
```

And so on.

After the basic OS is installed, I can then simply copy-and-paste this text into a terminal window, and a while later, my system is exactly like it was before.

Tom

---

### Post by Doomedelite on 2007-02-26
The "sudo su" also worked, thanks for all the fast responses guys!

---

### Post by floke on 2007-02-26
A good program for restoring partition images is 'partimage'
It's on this - [http://www.sysresccd.org/](http://www.sysresccd.org/) - but the site is currently down. 
Search on the forum for instructions on how to use it - Aysiu has some good ones on psychocats.

 As for editing the menus - just right-click on the menu heading (places, system etc.) and select 'edit menu' - you can alter everything from there.

---

