---
title: "[SOLVED] Help needed to recover a partition!!"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by javierfh on 2006-07-09
Hello,

when i created my system i just did 2(3) partitions, one for windows XP and then one for linux (plus the swap).
So then i read that it is wise to create a partition just for the /home, so i did. I went to XP side and used partition magic to resize the old partition, and when i got some space in hard drive i created a new one that it was from the Linux type and called ext 3.
So far no problem, i formated it as linux and well when i log into linux, i cant even see it, i see it under "computer" but i guess that appears as something else, probably not recognized.Then if i try to mount it it says

error: device /dev/sda4 is not removable

error: could not execute pmount

And if i right click mouse and go to properties,it says

type:desktop configuration file
size:unknown
location:computer:///
Mime type: application/x-desktop


Does anyone know how can i recover that partition? i have checked little the man fdisk and well it seems that now has asigned it as some weird type.

How can i recover that partition and format it as normal linux to mount it then under /dev/hdaX (i guess would be hda 2 or 3 in my case)


Please any help would be more than welcome.

Javier

---

### Post by rowlie on 2006-07-09
I had lots of probs with this .I sorted all my own out with the windows start up disk/system recovery disc, or a W98 floppy to get DOS command.You can't do the Fdisk from the command prompt inside Windows.If there is nothing in it then it won't matter to format/remove it and you get chances to stop the format anyway.It isn't too bad a job really. I just worked systematically through the options. I did a good back up before hand and actually wiped my windows by mistake,but the recovery disc restored it all. Don't be put off. In the end I just let the install process do the partitioning automatically and it all seems fine.  I have great dual boot system on my laptop -all functioning, even if it took me many hours of learning to get it right.I'm still thrilled to bits!

---

### Post by daou on 2006-07-09
Mounting the volume from the File Browser with a mouse click probably won't work.

Try going into the terminal and type (I am assuming the partition you lost is sda3, the third partition on your first hdd).

sudo mount -t ext3 -o users,umask=0000 /dev/sda3 /mnt

If it doesn't give an error go to the File Browser and open the Filesystem volume. Then open the mnt folder and the partition should be there. If the partition is empty, so will be the mnt folder. (if the previous command gives you an error, you need to try a partition other than sda3, maybe sda4 ?)

Now you need to edit your /etc/fstab file to mount the partition every time Ubuntu boots. Terminal:

sudo gedit /etc/fstab

You need to add the following line

/dev/sda3       /mnt           ext3    defaults        0       2

If you want it to mount somewhere else other than /mnt (which is probably wise), you need to make a new directory to which you want to mount to (example /mnt/somedrivename). To make the new directory use the following command in terminal:

sudo mkdir /mnt/somedrivename

or whatever directory you want. If you haven't already, save the fstab file. Now try seeing if the fstab file is correct by typing

sudo umount /dev/sda3     (this unmounts the previous mount we did for testing)
sudo mount -a          (this mounts all the partitions mentioned in fstab)

If it doesn't give any error messages, all is well and the partition will always load at boot to whichever directory you told it to.

---

### Post by javierfh on 2006-07-09
Hello and thanks for your comments.

Before i got your replies i decided to give a try to something i saw once in this chat, which is the online help, a bunch of guys willing to help.
I dont have words to thank for their work.

I love the feeling of comunity where people help others without asking anything back. I wish someday im in the situation to help other people.

Great for qunu and specially for muep who was the one that helped me with my problem. If others want to get help or give help this is the link
[http://alpha.qunu.com/index.html?search=ubuntu](http://alpha.qunu.com/index.html?search=ubuntu)

Hope that this helps other people,

Javi

---

