---
title: "&quot;home directory does not exist&quot;"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mrsudo on 2008-01-26
i recently made a new partition for my /home directory and it worked for a bit but the only thing is i had to assume it was working because all my settings would always stay saved but everytime i opened my /home folder nothing would be in it.  i can see all the contents of in when i boot xp.  ive checked and it says its mounted.???   

another thing . . . just yesterday i got an error logging in "you home directory is listed as '/home/kevin' but it does not appear to exist. Do you want to login with the /(root) directory as your home directory?"  

i choose both yes and no and i get kicked back to login everytime.  what can i do?

fstab:
```
# /dev/sdb4

UUID=200d1523-93c6-4f10-aa09-8a58f4e8c66a /               ext3    defaults,errors=remount-ro 0       1

# /dev/sdb2

UUID=26343643-4dc8-435a-86c2-a58bcdb2272f        /home        ext3        defaults      0      2

# /dev/sda1

UUID=3694FC2594FBE4F1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda2

UUID=4B6E-6BC0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda3

UUID=b500d6af-cb8f-4471-a89d-1550a5a6400b /media/sda3     ext3    defaults        0       2

# /dev/sda4

UUID=0c54a357-31de-4cd0-8305-f75c65d3322b none            swap    sw              0       0

# /dev/sdb3

UUID=7c965284-0a19-4e56-a280-1ba5c86794c1 none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by st33med on 2008-01-26
try this: Open up a shell (Alt-Ctrl-F1) and do this after logging on as root:
```
cd /home/kevin
```

---

### Post by drowner on 2008-01-26
Nothing in your fstab is mounted as /home - I think thats your problem.

Which of these drives is supposed to be your /home? And,  are you supposed to have 2 swaps?

---

### Post by mrsudo on 2008-01-26
my home should be located on sdb2.  its weird cause last time i checked it was definately in my fstab file.  
the reason i had 2 swaps is because i have 2 drives and used to have 2 separate different linux installs.

---

### Post by drowner on 2008-01-26
Are you comfortable backing up the fstab and then manipulating it, to mount the correct drive as /home ?

Also, for future reference, 2 different linux installations can share the swap!

---

### Post by mrsudo on 2008-01-27
i think i may have been looking at the wrong fstab.  i logged in to recovery mode and used nano /etc/fstab 
i got his for my /home entry:

```
# /dev/sdb2
UUID=26343643-4dc8-435a-86c2-a58bcdb2272f        /home        ext3        defaults      0      2
```

does this help at all?

when i use 
$ cd /home/kevin
$ ls
all it shows me is are the empty file folders such as: videos music pictures templates documents Desktop public

---

### Post by jflarm on 2008-01-27
Is that directory specified in the /etc/passwd file for the kevin user?

---

### Post by mrsudo on 2008-01-27
here is my /etc/passwd file:  

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:109::/var/run/dbus:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:107:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm:x:108:118:Gnome Display Manager:/var/lib/gdm:/bin/false
kevin:x:1000:1000:kevin henderson,,,:/home/kevin:/bin/bash

```

---

### Post by jflarm on 2008-01-27
I had some troubles in the past with partitions, and what I did was to remove the UUID part from the /etc/fstab file.
MAKE A BACKUP and try that out.

---

### Post by mrsudo on 2008-01-27
taking out my uuid's from /etc/fstab took away the error message.  i get another one right afterwrds about how my session lasted less than 10 seconds.  

i get an xsession error about something like

(precess:5880): Gtk WARNING
this process is currently running set uid or set gid
see http:[www.gtk.org/setuid.html](www.gtk.org/setuid.html)

refusing to initialize Gtk+
/etc/gdm/xsession: beginning session setup
cant create dir /home/kevin/desktop
cant create dir /home/kevin/templates
cant create dir /home/kevin/public

...


it continues on for quite a while and i have no way of accessing the full error message.

---

### Post by drowner on 2008-01-27
Taking out the UUID wasn't going to work, because it couldn't mount anything. sometimes the UUIDS get confused, and you can remove the numbers and replace them MANUALLY with /dev/sdaX as required, but that was never your problem.

I hope you backed up your fstab. Restore it

---

### Post by drowner on 2008-01-27
Now kevin - you need to slow down a little.... lets think

You have told me that 2 disks are supposed to be your /home partition.

One is sdb2 and one is sda2. They are different disks.

One is formatted FAT32 and one is formatted ext3.

Windows *cannot* recognise any ext3 partition unless you have installed some drivers (in windows). Have you installed drivers to read linux partitions in windows? If you have not, then the one you are seeing under windotws is the FAT32 one. This is NEVER mounted as /home, in any fstab

And remember - you only have one fstab.

My suggestion to you is to rund a live cd, and mount your drives.

Then show us exactly what the /etc/fstab has in it.

Edit:

I see you've changed your original post. It now contains a entry in the fstab for a /home. This is sdb2 and formatted ext3.

I get the feeling that your files that you expect to see in your home directory, which you can see under windows is actually sda2. This is formatted Fat32. This is not mounted as /home.

Does that sound right?

---

### Post by mrsudo on 2008-01-27
i am absolutely positive i want sdb2 to be my /home and it is currently formated as ext3.
as for in windows.  i installed something a few months ago to be able to read ext2/3 .  i forget the app name but i can definately see all my mounted ext3 drives in windows. this includes ubuntu and surprisingly all the contents of sdb2, my /home partition.

sda2 vfat partition is my xp recovery partition which i plan on getting rid of as soon as i get all the quirks out of my ubuntu install.

---

### Post by drowner on 2008-01-27
Right ok.

Have you restored your fstab?


Once you have, **back it up again** and replace the line under #/dev/sdb2 (the one that has the UUID stuff) with:

/dev/sdb2 /home ext3 nodev,nosuid 0 2


And try again

---

### Post by mrsudo on 2008-01-27
i got an original fstab right from my live cd and replaced it.
backed it up
added    /dev/sdb2       /home       ext3      nodev,nosuid       0      2
and im still getting the same gtk error

---

### Post by Siyfion on 2008-02-04
Did you ever find a fix for this as I am having similar issues!

---

### Post by mrsudo on 2008-02-04
sadly i have not.  
i totally reinstalled ubuntu and even formatted my /home with no luck.  
i still get the error.

---

### Post by ashmew2 on 2008-02-13
I just did a sudo /etc/init.d/gdm restart and when i tried to log back in , it tells me I dont have a home directory.. I am going to play around a bit. If i hit something ill tell you guys.
Btw , If you cant access the graphical interface. Go to tty1 (CTRL ALT F1)  and then login there. After that create a new user by using the command adduser. 

```
sudo adduser username
```

after that , use the groups command to list all of your groups

and add the new user to all the groups with the command :
```

sudo adduser new-username-you-created groupname

```


That should give you a fully functional new user and /home.

---

