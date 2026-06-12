---
title: "Permissions"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by RinSess on 2006-09-16
I would like to change the permissions for 2 folders so I can use them.

1. USB Drive. I plugged it in and the icon appeared on the desktop but I can't write to it. It says I do not have permission. 

2. An Ext3 partition which is on the same drive as the Ubuntu OS. Again, it says I can't write to it as I do not have permission. I went to the permissions tab and noticed that the file owner and file group is 'root'. Also, only the owner had permissions to perform read, write and execute functions while the file group and others had read and execute functions.

So, how do fix these folders so I can write to them?

---

### Post by smartalecks on 2006-09-16
The easy way is to browse in root.
To do this, go to Places and drag the "Home" item onto your desktop. Right click the newly created icon, and select the "launcher" tab. Replace the text in the "Command" input line with 

```
gksudo nautilus
```

Close it, and double click the icon. This should prompt you for your password . Navigate to the folder you want to copy/write to and you should be able to.

---

### Post by spur on 2006-09-17
Easier to go to the run command and type 'gksudo nautilus' if you use gnome or 'kdesu knoqueror' if you use kde this should open up a file manager you can then change to your desktop directory and change the file permissions.

---

### Post by Mimsy on 2006-09-17
I have a similar problem. I want to delete a folder in my home directory,and it won't let me, since I don't have permission. I tried the 'gksudo nautilus' but the folder doesn't show up when I do.

Any help is appreciated.

Thanks.
Mimsy

---

### Post by RinSess on 2006-09-17
**smartalecks**

Thanks, it worked.

---

### Post by fontenot_1031 on 2006-09-17
There are some folders and somethings on my Ubuntu filesystem that say I need superuser abilites.  Could I use the same comands in the first reply to fix that problem?

---

### Post by CatKiller on 2006-09-17
[Permissions]("http://psychocats.net/ubuntu/permissions")
[RootSudo Wiki page]("https://help.ubuntu.com/community/RootSudo")
[File Permissions Wiki page]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by Mimsy on 2006-09-17
Thanks for the links. I read through them all, and tried the "browse as root" solution, however, the folder still isn't showing up. The window that opened after I typed in 'gksudo nautilus' had my home folder, my desktop, and nothing else. So I dragged the folder I wanted to edit into that window, opened it and delete the subfolder I wanted to remove, then tried to drag the  main folder back to where it belongs. It said I can't do that becuase I don't have the proper permissions in place.

I can copy the folder and paste it back into the home folder,so this makes no sense to me. I can't drag-and-drop it into my home folder, but I can copy and paste it? Why is that?

Thanks,
Mimsy

---

### Post by CatKiller on 2006-09-17
The folder that you're in when you run nautilus as root probably **isn't** *your* home folder (/home/mimsy), but instead is /root. Perhaps this will help clear up what's going on.

---

### Post by Mimsy on 2006-09-17
And that makes perfect sense, I thought that was the case. What I did to get around this was to drag /home/mimsy/music/ to the /root folder, so I could delete a locked folder in /music. Once that was done, I couldn't drag /music back into /home/mimsy and that looks weird to me. As root I could take a folder out of /home/mimsy and copy-paste it back, but I cannot drag it back? 

Just to clarify, since copy-paste worked, this isn't a problem, the /music folder is back where Amarok can find it, I'm just curious about whhat to me looks like an inconsistency.

Thanks,
Mimsy

---

### Post by CatKiller on 2006-09-18
I think that what's happened is that you'd made the folder read-only. So you could copy, but not move. And Nautilus does seem to default to move when I'm not expecting it, so that could be why you could do it one way but not another.

Without seeing you do it, it's hard for me to say for sure. Glad to see you managed to do what you wanted, anyway.

---

### Post by spur on 2006-09-18
I got around this type of thing by opening up two windows as root ie kdesu konqueror  twice.

---

### Post by Mimsy on 2006-09-18
Read-only would make sense. Especially since the folder originally came over from a Windows PC. :)

Thanks!

/Mimsy

---

### Post by CatKiller on 2006-09-18
For future reference, you can make it writeable by right-clicking on it, selecting Properties and then going to the Permissions tab. If the Permissions tab shows that root is the owner, then you can run **gksudo nautilus** as you did before to look at it as root, and then change the owner to mimsy.

Unless the file is still on an NTFS partition. Then you probably shouldn't do anything with it :)

---

### Post by Mimsy on 2006-09-18
I don't think it is... how do I find out what format I'm using in Ubuntu? I don't have anything else on the laptop.

Thanks,
Mimsy

---

### Post by arsadogi on 2006-09-18
try in terminal *sudo chown yourusername folder* this command needs password.if you have any troubles type *man chown*

---

### Post by CatKiller on 2006-09-18
> **Mimsy said:**
> I don't think it is... how do I find out what format I'm using in Ubuntu? I don't have anything else on the laptop.

I was just referring to the fact that nature of NTFS means that you shouldn't be writing to it from Linux (and you can't by default). A partition will only be NTFS if it came from a recent version of Windows, and the chances are that you'll already know if it is, since you'd have had to set it up manually.

That'll teach me to make frivolous comments :) 

I think that the disks-admin utility will tell you what filesystem each disk partition is using, if you're interested.

---

### Post by Mimsy on 2006-09-18
Not particularly. As long as Ubuntu knows and can use it, I don't really care. I'm more interested in the file system Amarok uses to sort my music... Metallica is gone! :(

Off to re-rip I go...

/Mimsy

---

### Post by aktiwers on 2006-09-18
I love the script tthat Automatix installs. Then you can just do a right-click, pick scrips and root-nautilus here. Bang! Im in as root! :)

---

