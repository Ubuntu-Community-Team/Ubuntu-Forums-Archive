---
title: "Recognise and format hd."
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-06-04
I have a master and slave harddrive. I am trying to get Ubuntu to recognise the slave. If I look under System>Administration>Disks, I can see the hard drive, but if I look under Places>Computer, that hard drive is not listed. I want to format it and use it for Ubuntu. What do I have to do?

And another thing,
When I use Valknut I can share files, but not download them. I am in passive mode because I am behind a router. Any comments on this either.

All in all I am loving Ubuntu. :)

---

### Post by catlett on 2006-06-04
I'm in Dapper and I can't tell if you have Dapper or Breezy. But go to System<Administrative<Gnome Partition Editor. In Breezy I believe it is System<Administrative<Gparted.
They are the same thing. For some reason in Dapper they are using a different name. Anyways, it is the application "gparted". It is a partitioning application like Partition Magic etc.
If you don't see it you may have to install it from synaptic so give the command if it isn't in the menu ```
sudo apt-get install gparted
``` This application will allow you to format and partition your other drive.

---

### Post by r3st on 2006-06-04
is it just me or does "Recognise" looked spelled wrong?

---

### Post by aysiu on 2006-06-04
[QUOTE=r3st]is it just me or does "Recognise" looked spelled wrong?[/QUOTE] It's just British. In America, it's spelled *recognize*.

By the way, this thread is a double-post. The other thread is [here](http://www.ubuntuforums.org/showthread.php?t=188997).

---

### Post by catlett on 2006-06-04
You straightened 2 things out with one quick post:D  (I hope "straightened" is spelled correctly):D

---

### Post by tdrusk on 2006-06-04
[QUOTE=aysiu]It's just British. In America, it's spelled *recognize*.

By the way, this thread is a double-post. The other thread is [here](http://www.ubuntuforums.org/showthread.php?t=188997).[/QUOTE]
Is it a bad thing that I am from America lol. I wasn't thinking. I am trying to work with Gparted and I cant get the disk to mount. I changed the filesystem to ext3 and if I go to Places>computer and right click "mount volume" it says "unable to mount the selected volume. Error: device/dev/hdb1 is not removable.
Error: could not execute pmount.

any suggestions?

---

### Post by tdrusk on 2006-06-04
It was an hour before anybody answered me so I figured the guys in hardware could help. Sorry.

---

### Post by catlett on 2006-06-04
To mount for "one session" only. This won't be permanent. Do these commands. First make a place to mount the drive ```
sudo mkdir /media/drive2
``` Then give the command to mount ```
sudo mount /dev/hdb1 -t ext3 /media/drive2
``` If all goes well there will be an icon on your desktop for your drive.

---

### Post by tdrusk on 2006-06-04
Okay I tried that and it did not work. I looked a gparted and clicked the partition that I made and clicked properties. There is a warning, "WARNING: unable to read the contents of this filesystem! Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

*sigh* Any suggestions?

EDIT: I clicked Information, not properties.

EDIT AGAIN: I looked into system>disks and i selected that disk and then went to partitions. the status was "inaccessible". Do you think if I go into format of the disk manager, then change the access path to something (can you help me out there) that it would work?

---

### Post by catlett on 2006-06-04
Enter this command in the terminal ```
sudo fdisk -l
``` That will show your drives and partitions. Post it here. If /dev/hdb1 isn't the label of that partition then the mount command won't work.
Also did you do everything in gparted? Did you hit apply and it said everything completed successfully? What does gparted label the drive and/or the partition as i.e. ext3, fat32, deleted, unallocated, unknown etc

---

### Post by tdrusk on 2006-06-04
It labeled it as ext3, but I just messed something up with the system. Since I am not that far I'm going to reinstall. To save trouble of trying to fix things. I have no idea what I did. But I still will need help getting this disk to work. Once I get it set up I will do what you said then post back.

---

### Post by catlett on 2006-06-04
Since you're reinstalling, make a /home partition along with root and swap. This is good just for this reason. If you have to reinstall your personal data won't be lost. Home will not be reformatted, just root and swap/
Root only needs 5gb at most but if you have a large disk you can give it what you want but anything over 10gb is wasted space. The rule of thumb for swap is twice your ram i.e. 256mb ram = 512mb swap/ Home is whatever is left over b3ecause that will hold all your documents,mp3s,dvds etc. 
If swapping files and data between windows and linux is important to you, you may want to make a 4th partiton to serve as "common space". Make this partition Fat32 because both windows and linux can read and write to fat32 no problem. 10gb should be more than enough. You could actually go smaller because the biggest thing you would probably want access to is a 4+ gb movie. Anyways good luck and post if you have problems.

---

### Post by tdrusk on 2006-06-04
[QUOTE=catlett]Since you're reinstalling, make a /home partition along with root and swap. This is good just for this reason. If you have to reinstall your personal data won't be lost. Home will not be reformatted, just root and swap/
Root only needs 5gb at most but if you have a large disk you can give it what you want but anything over 10gb is wasted space. The rule of thumb for swap is twice your ram i.e. 256mb ram = 512mb swap/ Home is whatever is left over b3ecause that will hold all your documents,mp3s,dvds etc. 
If swapping files and data between windows and linux is important to you, you may want to make a 4th partiton to serve as "common space". Make this partition Fat32 because both windows and linux can read and write to fat32 no problem. 10gb should be more than enough. You could actually go smaller because the biggest thing you would probably want access to is a 4+ gb movie. Anyways good luck and post if you have problems.[/QUOTE]
okay, So what if I made my second hd (the one we are working on) for my home files, than make the other for system files and programs?

---

### Post by catlett on 2006-06-04
Yeah, you can do that as well. They can be on different partitions or different drives. Just remember that root doesn't have to be that big. 5gb is plenty but 10gb if you have the space protects against any possibility of running out of space. Home is for everything else. It can be the whole drive or part of the drive. The fat32 partition was mentioned in case you wanted to easily move data between windows and linux.
If you are going to reformat everything I would recommend using "Gparted live". It is the partitioner that comes wioth ubuntu except it is on a live cd. The download is small, 30mb, and the goos thing is your drives are unmounted so you can apply changes right there and then because the application is running off the live cd. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by tdrusk on 2006-06-04
How exactly do I make partitions for each thing. It opened GParted. I made one partition, but how do I specify as /root?

---

### Post by catlett on 2006-06-04
First do this. Choose the drive you want to format and delete it. Then choose the deleted space and select "new". Next a bar graph comes up that will show the space to make a partition. Drag the side of the graph until you get the size partition you want.
Do root first so it is up front.  (you don't have to do these numbers they are just for example). Move the graph from right to left until it reads 10gb and   there is no free space in front of the partition and all the free space is after the  partition . Choose to make it an ext3 primary partition. Next choose the deleted space and select new. Move the bar graph again to 512mb with no space free between root and this one. Format this one linux swap or swap (I forget how it is listed). 
Choose the deleted space and either make 1 big partition out of the rest of the space and make it ext3 or make a 20gb ext3 and  and make the rest a Fat32 partition.
The point is you just make the partitions here. You label them root, home, swap,data during install.
If you are using the Dapper Live cd install, you will get to the partitioner. Choose to manually edit the partition table. DO NOT create any new partitions. We are going to use the ones we just made.
When you get to the next page you will see ALL your partitions. The ones you made and any other ones on the other drive. There will be drop down boxes next to the partitions. Next to the 10gb partition choose '/" (root) from the drop down box. Next to the 512mb choose "swap". Next to the 20gb (or whatever you made for home) choose "home". If you made a data partition you don't have to choose anything it will have a mount point.
THIS IS IMPORTANT. Next to each partition is a circle with "format" above the circles. Only choose to format the partitions you made for linux i.e /, swap, home and the partition you made as fat32 if you made it.
DO NOT check off the other partitions or they will be formatted and the data lost. Just leave them as they are. Dapper has given them default mount points and that is fine. They will be icons on your desktop after the install. Just leave them as they are and DO NOT check off "format?" next to them.
Let the install run.

---

### Post by tdrusk on 2006-06-04
are boot and root the same? or is root labeled /

---

### Post by catlett on 2006-06-04
Sorry, they are different. Root is labeled /    ..Nothing else is next to it. Boot is another label but you don't need it. It comes into play with large size drives and you want to boot from a partition that is beyond the boot parameters. But your boot will be a folder in root. It will be up front on the drive so no need to make one. Just make /, swap and home. You don't need to choose a boot.

---

### Post by tdrusk on 2006-06-04
Yes!
Everything went as planned. Thank you so much for your help.
My computer folder now looks like [this]("http://img144.imageshack.us/img144/9011/screenshot2lb.jpg")

---

### Post by catlett on 2006-06-04
Great news!! =D> Glad things worked out. Well you're on your way. Take care.

---

