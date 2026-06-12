---
title: "Doesn't main user get permissions?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by leftover1 on 2007-10-18
Confused about the "permissions" thing...
Decided to play with Ubuntu on my old pc after I upgraded.  Converted drive to ext3 with 3 partitions, installed Feisty from the live cd, with just 1 user.
When I try to copy a file to the 3rd partition (not the root or the swap) using the Gnome desktop, I get the "you do not have permissions to write to this folder" error.
When I check the permissions tab for the partition, owner and group are "root," no others are listed. I tried "sudo chown myusername /hda5" it comes back with "cannot access '/hda5': no such file or directory." 
Tried "gksudo nautilus /" & was apparently allowed to change settings, but still wasn't able to write/create files.
I check user settings, and my username is part of the root group.
If I try to switch user to root, apparently my password doesn't work.
The hard drive does appear on the desktop.
I thought as the 1st user of a new installation I'd automatically get all permissions, no?  Is there a way to set it so I can write or save a file without having to type something in a terminal window each time?

Thanks!

---

### Post by Cannaregio on 2007-10-18
> I thought as the 1st user of a new installation I'd automatically get all permissions, no? Is there a way to set it so I can write or save a file without having to type something in a terminal window each time?

No.
The point is that you should NOT be root by default.
Of course you can be root as long as you want without using sudo every time, just execute

```
sudo -i
```

But that's insane on a GNU/Linux system, and it is gonna hurt you badly soon or later.

Just "get used" to use [COLOR="#0000ff"]sudo[/COLOR], or [COLOR="Blue"]sudo nautilus[/COLOR], when appropriate, and enjoy.

---

### Post by bodhi.zazen on 2007-10-18
> **Cannaregio said:**
> Just "get used" to use [COLOR="#0000ff"]sudo[/COLOR], or [COLOR="Blue"]sudo nautilus[/COLOR], when appropriate, and enjoy.

:lolflag:

That should be [color=red]gksu nautilus[/color] or perhaps [color=blue]kdesu nautilus[/color]

And the classic link : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

EDIT: Nice post.

---

### Post by Cannaregio on 2007-10-18
Oops, sorry:  indeed using sudo with graphical applications, you get root-owned junk in your /home directory. [COLOR="Blue"]gksudo[/COLOR] (or [COLOR="#0000ff"]kdesu[/COLOR]) will instead use root's conf files, instead of the user's conf files.

I blush, my mistake, i slurped too many [COLOR="#0000ff"]sudo gedit[/COLOR], but maybe this will still help people understand the difference between sudo and gksudo.

---

### Post by leftover1 on 2007-10-19
OK, for some odd reason, when I posted the other day it wouldn't let me do ANYTHING, not even creating a bookmark for Firefox, because of permissions...
Tonight, it's fine.  I can copy a file, make a bookmark, etc.  I don't think I'm doing anything differently, so chalk this up to noob learning experience!
Thank for the replies!

---

### Post by bigboy_pdb on 2007-10-20
When you use gksudo and sudo, both should work with the password that you used to log in to your account. If they are not working, it could be because you are not in the group "admin". To see if you are in the group admin use the command "cat /etc/group | grep ^admin". If you see your user name listed then you should be able to use those commands. Otherwise, you will need to add yourself to that group using a user who is in the group "admin".

Regarding your additional partition, it doesn't sound as though it is mounted to the folder "/hda5". To check what file systems are mounted and what their mount points are you can either use the command "mount" or the command "df". If you don't see the file system /dev/hda5 listed then you will need to mount it. You can do this using the command "sudo mount /dev/sda5 *dir*" where *dir* is the directory that you want to mount the drive to (and *dir* must be a directory that exists). To have the file system mounted when Ubuntu starts up (if this doesn't currently happen), you will need to change the "/etc/fstab" file

The easiest way to save files on the drive as your current user would be to add a new folder on the file system and then to change the owner and group to your user. We will refer to that folder as *nfolder*. In the terminal (Applications -> Accessories -> Terminal) move to the directory where /dev/hda5 is mounted to and execute the command "sudo mkdir *nfolder*". The folder should now be in the directory. Use the command "sudo chown *user*:*user*" to change the file so its owner and group are *user* where *user* is the name of the user who you want to be able to access the files in the folder. If you don't know what user you are logged in as (though I'm guessing that you should know) then you can use the can use the command "whoami" to find out.

**[EDIT]***user*:*user* is "user:user" (the colon might not be properly visible due to the italics**[/EDIT]**

---

