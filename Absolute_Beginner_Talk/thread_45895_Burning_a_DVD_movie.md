---
title: "Burning a DVD movie"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by lolailo on 2005-07-02
Hi,  I'm very new to kubuntu and linux and I can't seem to get anything working.  I was hoping someone would be kind enough to help me.

I would like to burn an avi from an XP partition on to a DVD so I can watch it on my DVD player.

My first problem is when I start K3b I get a notice saying:
      Unable to find cdrdao executable
      K3b uses cdrdao to actually write CDs.
      Solution: Install the cdrdao package.

I don't understand why k3b would be installed with packages missing.  Anyhow since it says this package is neded to write CDs I'm assuming I won't be affected by this since I only want to write DVDs.

The next problem I have is that I mounted the XP partition where I have the movie I want to burn but I obviously did something wrong because when I want to open the folder it says:
      You do not have enough permissions to read file:///c
For some reason in the properties of the folder it says the owner is the ROOT (whatever that means).

I guess this is all pretty basic but I'm really stuck.

---

### Post by sonny on 2005-07-02
well... first things first... you DO have to install cdrao in orderder to burn. the way you do it is by opening kynaptics, and search for it with the search option. You click on it, and choose mark to install (or something like that).

Second... your hard drive, usually windows uses NTFS filesystems, wich Linux is only capable of reading it, so you don't have write permissions, as for the root thing, root is the super user in Linux, the user that can do anything he/she wants, even destroy your system (use the sudo command carefully). to mount a drive you need super user privilege, so only root (your sudo command) can acces to it, but I presume it is a NTFS filesystem, so you won't be able to write to it; you should be able to read it, though.

You should check you mounting. 3 steps:

1.- Find the XP partition, with qtparted, look for the name something like hda1 or hda2, hdb1 or something.
2.- Create a mounting point in /media/hda1 (if it's hda1, change it to your partition number)
3.- code: sudo mount -t ntfs /dev/hda1 /media/hda1

What you should do is, open konqueror as root, find the avi file you want to burn, copy and paste it to your home directory, then open K3B and burn de dvd.

---

### Post by lolailo on 2005-07-02
Thanks sonny for your help,

I had already thought of getting the cdrdao package with kynaptic (I'm glad to see I wasn't so far off) but the search doesn't show anything by that name.  Maybe I'm doing something wrong.

I'm not sure what "qtparted" is but since I want to access the first partition of my seccond hard drive I imagine it would be "hdb1" right?

You mention opening conqueror as root.  How do you do that?

I think I understand everything else fine.

---

### Post by lolailo on 2005-07-02
I've been trying to change the ownership of /media/windows to myself so that I can change the permissions and open the folder.  What happens is that when I do it acording to the ubuntuguide instructions I get a message saying I give too few arguments.  Here's what I'm putting:
sudo chown my_username/media/windows

---

### Post by johnistpropaganda on 2005-07-03
Can k3b convert avi to video dvd? in my version (0.11.23) it says that k3b does not yet support transcoding, and that you need to have the vob and ifo ready when you burn. 

I have been using this link to convert avi's and burn, with moderate success:

[http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709) 

Its all command line and you'll prolly have to apt-get a few packages, but don't be scared!

I hope I'm wrong about k3b though. That would make things much easier!

hope this helps
j

---

### Post by sapo on 2005-07-03
[QUOTE=johnistpropaganda]Can k3b convert avi to video dvd? in my version (0.11.23) it says that k3b does not yet support transcoding, and that you need to have the vob and ifo ready when you burn. 

I have been using this link to convert avi's and burn, with moderate success:

[http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709) 

Its all command line and you'll prolly have to apt-get a few packages, but don't be scared!

I hope I'm wrong about k3b though. That would make things much easier!

hope this helps
j[/QUOTE]

i use tovid to do this job.. it creates even the vobs for me:

[http://tovid.sourceforge.net](http://tovid.sourceforge.net)

And i use this script to burn in a dvd:

```
#!/bin/sh

# Create an AUDIO_TS subdirectory if it does not exist
[ ! -d AUDIO_TS ] && mkdir AUDIO_TS

chown -R root:root AUDIO_TS VIDEO_TS
chmod 500 AUDIO_TS VIDEO_TS
chmod 400 VIDEO_TS/*

growisofs -dvd-compat -Z /dev/dvd -dvd-video .
```

---

### Post by sonny on 2005-07-04
[QUOTE=lolailo]I'm not sure what "qtparted" is but since I want to access the first partition of my seccond hard drive I imagine it would be "hdb1" right?[/QUOTE]
Well that is correct.

[QUOTE=lolailo] Here's what I'm putting:  sudo chown my_username/media/windows[/QUOTE]
well actually the code should be: sudo chown username:usergoup /path/to/folder

But IF windows is in NTFS format you WONT be able to write to it. 
Qtparted is a tool that shows you all your connected HD, and tells you wich fylesystem they use, search for qtparted in kynaptics, it's easy to use, at least just for some references.

---

