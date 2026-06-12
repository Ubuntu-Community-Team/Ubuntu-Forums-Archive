---
title: "Using ubuntu and windows"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2007-07-25
I used to use Ubuntu on my laptop but it got fried so now I'm stuck on a windows xp machine and it's really driving me insane.  I can't switch it over to Ubuntu because it's a family computer and so I was wondering if there was a thread somewhere detailing how to use the windows partition to store the files and the ubuntu partition to use and manipulate all the files.  It seems like something that should be easy to find but I'm really not getting the right search phrases or something because I'm not finding it.  Any help would be greatly appreciated.
Thanks,
Nolan

---

### Post by skymera on 2007-07-25
ok, it is possible to dual boot XP.
like me :) fiesty and uhhh XP.

they sya you should defrag your windows drive
then boot up the Live CD, and select the install.
create a root drive, home and swap

from ubuntu as you know you can Read/Write to Windows.
it is possible i believe to do the same from XP to ubuntu.

---

### Post by rickycodie on 2007-07-25
if you have a flash drive you should check out pendrivelinux.com a os on your flash drive.

---

### Post by Daveth on 2007-07-25
check out

[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

you need to search for FAT32 which both OS are happy writing to. You could then dual boot and happily move data about for all the family.

---

### Post by madddonkey255 on 2007-07-25
Thanks for the help, I didn't explain it too well before but dual booting isn't my issue.  I'm just not sure about how seamlessly I can use and manipulate files stored on the windows partition, any info about that would be appreciated.
Thanks,
Nolan

---

### Post by gimpguy2000 on 2007-07-25
I know i'm a newbie myself but what I did is open the computer, click on the volume in the left and it mounts the drive\partition, all I have to do then is open it up and find all my Windows files. 

 Hope this helps some...

 Paul

BTW, they can stay mounted and will show on desktop, then you can unmount them at any time..:)

---

### Post by Hitchhiker42 on 2007-07-25
Are you talking about having ntfs write support? If so, just grab ntfs-3g and ntfs-config from the repos, and you should be able to fiddle with the files on your Windows partition, no problem. (Of course, if your Windows partition is FAT32, you should be able to read and write to it by default.)

---

### Post by madddonkey255 on 2007-07-26
So I am right now typing this on the new ubuntu partition and it's rocking, slight problem accessing the windows files.  Automatix has a script to allow read/write priviledges on ntfs so that's sweet but when I installed it it said I may have to restart to access the partitions properly.  Without restarting I tried accessing the the drive and it said I didn't have access, now I can't find any icon anywhere to be able to get to it, I have access to the other harddrive with windows on it fine, I even tried using a shortcut but ubuntu doesn't know what to do with the .lnk of the shortcut.

So I was wondering how to find/mount this partition again and get that working, because all the files I need are on that part.
Thanks,
Nolan

---

### Post by madddonkey255 on 2007-07-26
I logged into Windows to do some work and then when I rebooted and switched back to Ubuntu the problem seems to have fixed itself.
Thanks again,
Nolan

---

