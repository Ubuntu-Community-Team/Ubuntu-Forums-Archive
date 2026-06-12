---
title: "NTFS mounts to consecutive folders"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by tsphere on 2008-04-06
Hi,
I'm using, as of today, the latest Hardy Heron ubuntu.
Noticed that every time I reboot, my windows partition is mounted to a different folder inside /media.
It was drive1, later drive2, and I'm in drive4 now.
The previous folders are there, but are locked.
Also, it only mounts if I click on "media" inside File Browser.

I want it to mount to one specific folder, at startup, so I can use it for example in Amarok, and not have to scan the library again and again with every reboot. Can it be done?
Also, I want to create shortcuts to My Documents that will work on startup, so I don't have to go through all the folders to get there every time. How can it be done?

Thanks, great OS, hope I can ditch windose,
Eyal

---

### Post by softtower on 2008-04-06
I am not sure what is happening to your "locked" directories under /media, do you shut down Ubuntu normally? Perhaps the NTFS disk (your windows drive) needs to be checked, I would do it by going back to Windows and running disk check on them.

But as far as "my documents" are concerned, in Ubuntu (unlike windows) your personal folder is very easy to access:
Using Gnome's top-level menu simply go to "Places/Home". What can be easier? :-)

---

### Post by tsphere on 2008-04-06
Thanks for the reply.
My locked directories have an X symbol of them, and it says I don't have permissions to display them. the disk is fine, I did a checkdisk before installing ubuntu.

I need the my documents from windows, and in general I want to know if there is a way to create a shortcut to a mounted directory.

Thanks,
Eyal

---

### Post by softtower on 2008-04-06
Yes, try ln command, but you'll need a "soft" link, i.e.

ln -s /path/to/your/windows/documents /path/where/you/want/your/shortcut

---

### Post by tsphere on 2008-04-07
Thanks mate!

Abount the mount, I think I figured a way. First I unmounted all the false directories and deleted them, and I added a startup command to unmount the disk. Hope it works.

Now all I need is a way to mount the ntfs at startup, and I'm done :)

---

### Post by IanW on 2008-04-07
This is a known bug, Launchpad #101845.

---

