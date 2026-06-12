---
title: "Setting a timemachine on a ubuntu"
date: 2012-08-10
forum: Apple Hardware Users
---

### Post by alek66 on 2012-08-10
Hey everybody.

I just installed my brand new headless ubuntu to use as a nas at home.

I tried to configure a timemachine for my mac following this: [http://kremalicious.com/ubuntu-as-mac-file-server-and-time-machine-volume/](http://kremalicious.com/ubuntu-as-mac-file-server-and-time-machine-volume/)
 and [http://ubuntuforums.org/showthread.php?t=1935903&highlight=timemachine](http://ubuntuforums.org/showthread.php?t=1935903&highlight=timemachine)

Heres the set up I am using: I have a dedicated 80gb disk for time machine:
Formated as Ext4, mounted at /mnt/TimeMachine mounted at boot.

> sudo gedit /etc/netatalk/AppleVolumes.default

I have: 
```
# By default all users have access to their home directories.
~/			"Home Directory"

/mnt/TimeMachine/TimeMachine "TimeMachine" allow:username1,username2 cnidscheme:cdb options:tm
# End of File

```

But I get this when I connect from my mac:
[IMG]http://s18.postimage.org/3t0a8yxzd/image.png[/IMG]
And I get no option to use it as my time machine disk from my mac.


Any help would be much appreciated.

---

### Post by alek66 on 2012-08-10
Good advances:

I modified this file:
AppleVolumes.default

# By default all users have access to their home directories.
~/			"Home Directory"

/mnt/TimeMachine "TimeMachine" allow:aleza cnidscheme:cdb options:tm
# End of File


Now I have this:

[IMG]http://i45.tinypic.com/f05emp.jpg[/IMG]

I got time machine to see the disk:
[IMG]http://i48.tinypic.com/21dhc9.jpg[/IMG]

I got this error, I am thinking if there something wrong with the partition and the rights on it?
[IMG]http://i50.tinypic.com/9axwro.jpg[/IMG]

Any ideas?

---

### Post by pinjan on 2012-08-11
Check my thread: 
[http://ubuntuforums.org/showthread.php?t=1935903]("http://ubuntuforums.org/showthread.php?t=1935903")

---

### Post by alek66 on 2012-08-11
Thanks, I could not make it on ow to fix it, from your thread.

Every tutorial uses a folder, and I am trying to use a dedicated disk for it. I don't know if the partition extension is correct, and what rights should I set on the disk.

Thanks anyway!

---

### Post by alek66 on 2012-08-12
Managed to advance now:

Now I get this error when Mounting the shared disk in my apple:
[IMG]http://s18.postimage.org/9lp0w1qgp/error_when_mounting.png[/IMG]
And this error when I do a time machine backup:
[IMG]http://s11.postimage.org/4tdjvmev7/error_time_machine.png[/IMG]
I feel like I am getting really close, and Please don't tell me I won't get 100% compatibility here since is not a mac official thing.

Thanks everyone.

---

### Post by pinjan on 2012-08-12
What comes to first message, change : cnidscheme:dbd. You had it above : cnidscheme: cbd. Second error relates to AFP, Apple FilIng Protocol. Which version of Netatalk you have and what you have in afpd.conf file ? Should be something like: 
Code:
- -tcp -noddp -uamlist uams_dhx.so,uams_dhx2_passwd.so -nosavepassword

---

### Post by alek66 on 2012-08-12
> **pinjan said:**
> What comes to first message, change : cnidscheme:dbd. You had it above : cnidscheme: cbd. Second error relates to AFP, Apple FilIng Protocol. Which version of Netatalk you have and what you have in afpd.conf file ? Should be something like: 
Code:
- -tcp -noddp -uamlist uams_dhx.so,uams_dhx2_passwd.so -nosavepassword

PInjan: Thanks a lot, my netatalk version is 2.2.1.1 

I changed the cnidscheme: bcd to cnidscheme:dbd in the AppleVolumes.default, heres how it is now.

> # The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# By default all users have access to their home directories.
~/			"Home Directory"

#Disco80
/mnt/TimeMachine "TimeMachine" allow:aleza cnidscheme:dbd options:upriv
# End of File


And I changed my line to
My line at the bottom of afpd.conf is: - -tcp -noddp -uamlist uams_randnum.so,uams_dhx.so,uams_dhx2.so -nosavepassword

....now time machine does not even sees the disk. :(

---

### Post by pinjan on 2012-08-12
I checked my afpd.conf file and I have there following:

```
- -transall '-uamlist uams_dhx.so,uams_dhx2_passwd.so
```

Sorry for mistake !

I have same version of netatalk than you are having

---

### Post by pinjan on 2012-08-12
My AppleVolumes.default:

```

# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# By default all users have access to their home directories.
~/                      "Home Directory"
~/ "$u" allow:backupwriter cnidscheme:cdb
/home/username/Backup/TimeMachine "TM" allow:username options:usedots,upriv,tm ea:ad
/mnt/TimeMachine "TimeMachine" allow:username cnidscheme:cdb options:tm,usedots

# End of File
```

Where username is my username naturally :) Hopefully this helps.

---

### Post by alek66 on 2012-08-12
> **pinjan said:**
> My AppleVolumes.default:

```

# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# By default all users have access to their home directories.
~/                      "Home Directory"
~/ "$u" allow:backupwriter cnidscheme:cdb
/home/username/Backup/TimeMachine "TM" allow:username options:usedots,upriv,tm ea:ad
/mnt/TimeMachine "TimeMachine" allow:username cnidscheme:cdb options:tm,usedots

# End of File
```

Where username is my username naturally :) Hopefully this helps.

Which one of the time machines is the one you use? I see two, 

After some errors of the CBD scheme, it started to do the bkp.

I will let you know after it finished, on how it went.

---

### Post by pinjan on 2012-08-12
> **alek66 said:**
> Which one of the time machines is the one you use? I see two, 

After some errors of the CBD scheme, it started to do the bkp.

I will let you know after it finished, on how it went.

I am using TM

---

### Post by alek66 on 2012-08-12
It worked!!!!

As you can see I managed to get a full backup of my laptop.... 
[IMG]http://s13.postimage.org/mw7x3ok9z/timemachineworking.png[/IMG]
But I am still getting this error:
[IMG]http://s12.postimage.org/wmjp0t7f1/error.png[/IMG]
I would like to understand why is this error showing up....

Any ideas?

---

### Post by pinjan on 2012-08-13
Have you restarted netatalk after changes ?

---

### Post by alek66 on 2012-08-13
> **pinjan said:**
> Have you restarted netatalk after changes ?

Yes... At the moment I can do backups with those errors. :popcorn:

---

### Post by pinjan on 2012-08-13
You could try  this:


1. Stop netatalk.
2. Delete the .AppleDB cnid db in the root of your time machine share.
3. Change the cnidscheme to dbd in AppleVolumes.default
4. Start netatalk.

---

