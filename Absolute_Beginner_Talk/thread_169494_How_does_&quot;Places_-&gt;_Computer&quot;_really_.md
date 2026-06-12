---
title: "How does &quot;Places -&gt; Computer&quot; really work?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Holgaas on 2006-05-02
Hi,

I've just installed Ubuntu, and made three partitions (A "Boot"-partition <20gb>, an "everything else"-partition <138gb>and a "swap"-partition <1.5gb>) during the installation process, but all i can see in "Places -> Computer" is something called "Filesystem".

I don't understand whats going on, where my partitions went or how to find them.
In "System -> Administration -> Disks" i can see all of them, but not really do anything. I've installed Gparted, but didn't find anything to help me with my problem.

Also, i can't seem to change anything on my "Places -> Computer" as i am not "The Owner". I understand that the owner is "root", and that i will have to logg in as "root" or use some sort of "sudo" command to change those settings. i'm new to linux, and quite helpless, so any tips would be of great help.


Thanks alot.

---

### Post by BarFly on 2006-05-02
You can see the partitions by going into System, Administration, Disks, Partition and putting in the root pass.

I am not sure I follow you about what you want to change.

---

### Post by harisund on 2006-05-02
See, your computer file system is organized in a very structured manner. At the top there is '/' also called the root partition. Now, when you created the partitions while installing you would have said the 'everything else' partition (138gb) should be mounted somewhere, right? Assuming you said it had to be mounted at /home, Linux doesn't really show you /home seperately. Its just a part of your file system. You shouldn't be expecting a C:\ or D:\ and instead be looking for everything under the \ partition

When 'Computer' shows only 'Filesystem', it's because that's al the computer is made of. You have to click 'Filesystem' and you will see a list that has stuff like '/var, /tmp /home' and so on. You can then continue to navigate further down.

---

### Post by nanotube on 2006-05-02
to see where your things are mounted, open up a terminal, and type command "df". that will show you where all your partitions are mounted to.

---

### Post by catlett on 2006-05-02
Is "everything else" your home partition? This is important. You can have an install with 3 partitions. A Root, a Swap and a Home. If it is like that then your root file system is in the 20gb. Your home folder will be in the 138gb and your swap in the 1.5gb.
When you look in the file system the folders will represent the space and when you open ther folder the content folders are inside etc.
The issue is if the 138 isn't designated home then your whole install went on the 20gb and your not using the 138gb space. The install can go on 1 partition. The installer will format a swap space and put everything in 1 partiton. You had to specify the 138 as home. If you didn't the partition might not be mounted and the space is not available.
If you did install home then everything is there. Linux just does things different. You will see folders and / not partitions. The base is / "root" then it goes from there /home, /boot, /boot/grub/menu.lst, /home/catlett/pictures, etc

---

### Post by wylfing on 2006-05-02
The take-away from all that explanation is this:

1. Don't worry about partitions. What you're seeing in Filesystem is correct, relax.

2. You **do not** want to start tromping around changing things you see under Filesystem. Just stick to your Home folder -- in there you'll be able to change whatever you want.

---

### Post by Holgaas on 2006-05-02
Thanks for your replies.

Ok, i think i understand now, but i would like to be able to change thinks around my HD but i have to login as "root". I've tried to do it in the "terminal" using "sudo -s -H", but that doesn't give me the chance to change the "permissions" of "Filesystem". How can i log in as "root"?


Thanks again.

---

### Post by catlett on 2006-05-02
You don't log out/log in as root in Ubuntu. Sudo gives you root priveleges for the command that follows. So you would do sudo command. It will ask for a password. Use your user password. There is no sudo or root password to put in, just your user password. Then the command will be executed as root.
Follow this link from nanotubes signature [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#User_privileges_and_editing_files](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#User_privileges_and_editing_files)

---

### Post by openmind on 2006-05-02
OK, on (Roughly!) the same subject could someone please enlighten me on this; I have a 40G vfat partition for sharing between WinXP and Dapper, works fine, but it's mounted on /media/windows, and I can get to my vfat files with that route but the 'used' space on it doesn't show when I look at the / (root) filesystem (10G). 

Why not? If it's a hierarchal system it should show up right?

---

### Post by steve.horsley on 2006-05-02
Can you explain what you are trying to change, and why?

And please open a command prompt (Accessories->Terminal) and enter the command **df -h** and then post the resulting output. This will tell us what partitions are mounted where.

---

### Post by Holgaas on 2006-05-02
Ok, i get it. But then, is there any way to give other users the chance to change the "permissions" of "filesystem", or a way to do it in "terminal".

---

### Post by nanotube on 2006-05-02
catlett is right about the sudo stuff. 
for a more in-depth tutorial about it, check out 
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by nanotube on 2006-05-02
[QUOTE=Holgaas]Ok, i get it. But then, is there any way to give other users the chance to change the "permissions" of "filesystem", or a way to do it in "terminal".[/QUOTE]
you, as the administrator of the system, have to set the proper permissions on the various parts of the filesystem, if you want other users to have access to them. so, for example, if you want to make a directory readable by everyone, you would use command "chmod" and change the permissions.

---

### Post by Holgaas on 2006-05-02
Well, i tried "chmod", but don't understand how it will let me change the "permissions" of filesystem.

I've installed "WineHQ" using SPM but i was unable to choose where to install it. It just installed in /usr/bin. And since i can't "write" in that part of "filesystem" i'm unable to save the changes made in Winecfg.:-k 

I'm sure this is something that can be easily solved, but the problem really being that i'm new to how this Ubuntu works. So if anyone can explain it to me like you would explain it to a five year old micronesian child, it would be of great help.;) 


Thanks for all your post, people!:-D

---

### Post by nanotube on 2006-05-02
[QUOTE=Holgaas]Well, i tried "chmod", but don't understand how it will let me change the "permissions" of filesystem.

I've installed "WineHQ" using SPM but i was unable to choose where to install it. It just installed in /usr/bin. And since i can't "write" in that part of "filesystem" i'm unable to save the changes made in Winecfg.:-k 

I'm sure this is something that can be easily solved, but the problem really being that i'm new to how this Ubuntu works. So if anyone can explain it to me like you would explain it to a five year old micronesian child, it would be of great help.;) 


Thanks for all your post, people!:-D[/QUOTE]

heh well, read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
to understand how to do stuff as root.
basically, whenever you are trying to do something that will change files outside of your home dir, you should run those commands with sudo. and /usr/bin is certainly outside of your home dir. :)

---

### Post by Holgaas on 2006-05-02
Ohh.. I've managed to use "chown" so that i may change folders, but i cant change files within folders. Is there a way to changa a folder and all the files in it?

---

### Post by nanotube on 2006-05-02
[QUOTE=Holgaas]Ohh.. I've managed to use "chown" so that i may change folders, but i cant change files within folders. Is there a way to changa a folder and all the files in it?[/QUOTE]
use "chown -R" for that.
see "man chown" for more details. :)

---

### Post by Holgaas on 2006-05-03
Hi,

Problem solved!:D 

Thanks for all the help people. 


All the best..

---

