---
title: "Want to migrate from Kubuntu to Ubunutu, few questions"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by TooManyGames on 2007-06-24
I've been using Kubuntu for a while now, but I want to start using Gnome for my desktop environment.  I would like to lose the smallest amount of data possible, what do I need to backup to keep as much of my software and their settings as possible?  Is my home folder enough, or should I backup more to prepare for the migration?

Christ, I misspelled Ubuntu in the thread title.  Sorry.  8*)

---

### Post by freebird54 on 2007-06-24
No need to remove anything unless you want to.  If you just add the Gnome desktop, you can decide whether to drop the KDE one later...

Explanations here:   [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

On the same site are comparos, instructions for removing whatever you don't want, etc.  Enjoy!  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by maharbA on 2007-06-24
Try:
sudo apt-get ubuntu-desktop

that will install everything you need for the Gnome Ubuntu experience.
You'll basically have both -- and be able to choose at login which to use.

EDIT:
Damn -- too slow!

---

### Post by Huw on 2007-06-24
Why not just install Gnome on your current installation?  I'm no expert but as far as I'm aware you can just use Synaptic to download it, then at the login screen select Gnome as the current session.

The question of backing up is worth answering anyway though.  Generally, all applications keep their configurations and stored data in hidden directories within your home directory.  For example, if you use Thunderbird you should find your email and settings in /home/TooManyGames/.Thunderbird.  As a result, backing up your home directory is usually enough.

As for backing up software, this isn't necessary since your settings will be backed up with /home, so just reinstalling your software should be enough.  However, it's worth mentioning that software you've installed that hasn't come from the repositories (for example, a binary package you've downloaded from a project's website) usually goes into a directory like /opt.  You should get the option when you first install it.

---

### Post by Enverex on 2007-06-24
You don't need to back up anything, this is the problem with the whole "*ubuntu" thing. Just install "ubuntu-desktop" with Synaptic and Tada, it's now the same as Ubuntu. The only difference between all these different "sub distros" is the pre-installed software. If Apt asks you, you want to use GDM from that point onwards. When you log in after installing it all you should have an option on the settings somewhere on the login screen to use Gnome as your session instead of KDE.

---

