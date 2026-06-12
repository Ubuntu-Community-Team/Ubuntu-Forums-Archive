---
title: "Having Trouble"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by 02lancastr on 2007-08-18
I'm pretty new to ubuntu, i have been using the live CD for a while but i decided to install it on my second hard drive. Everything installed fine, but now that i am using it i cant use any admin permissions, if i got to install something, or change a setting, it asks for my pass so i put it in and i get this: 
Can anyone help?

[IMG]http://img528.imageshack.us/img528/396/screenshotgksumt3.png[/IMG]

Ps. sorry for rubbish grammer
Thanks in advance

---

### Post by Happy_Man on 2007-08-18
Are you using the same account that you created when you first installed?

---

### Post by taurus on 2007-08-18
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by 02lancastr on 2007-08-18
Yer i am using the same account i installed it on.
i get this from the terminal: 

uid=1001(lancastr02) gid=1001(lancastr02) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),113(lpadmin),1001(lancastr02)

thanks for the fast reply

---

### Post by 02lancastr on 2007-08-18
Please help :( I really like ubuntu, but i cant continue to used it unless i sort this porblem.

Is it something obvious that im not seeing or something? please help

---

### Post by 02lancastr on 2007-08-18
Is it something obvious that im not seeing or something? please help

---

### Post by taurus on 2007-08-18
You also need to belong to group admin in /etc/group as well as adm.  Therefore, boot into recovery mode from GRUB menu and at the prompt, run

```
nano -B /etc/group
```
Scroll down near the end and add your login name, lancastr02, after group admin.  Save it with <Ctrl>o and exit with <Ctrl>x.  Reboot and see if you can use sudo now.

```
shutdown -r now
```

---

### Post by SpiritIsReality on 2007-08-18
taurus    thanks for your posts
I was getting tangled searching for an answer

seemed that a recovery single user boot
and a visudo was helping

when I run id I get uid=1000
and 02lancastr has uid=1001

looking forward to solution
[http://ubuntuforums.org/showthread.php?t=473630&highlight=users-admin](http://ubuntuforums.org/showthread.php?t=473630&highlight=users-admin)
[http://ubuntuforums.org/showthread.php?p=3086753#post3086753](http://ubuntuforums.org/showthread.php?p=3086753#post3086753)
[http://ubuntuforums.org/showthread.php?t=462991&highlight=users-admin&page=2](http://ubuntuforums.org/showthread.php?t=462991&highlight=users-admin&page=2)

[http://ubuntuforums.org/showthread.php?t=484828&highlight=users-admin&page=2](http://ubuntuforums.org/showthread.php?t=484828&highlight=users-admin&page=2)

---

### Post by taurus on 2007-08-18
> **fmat said:**
> taurus    thanks for your posts
I was getting tangled searching for an answer

seemed that a recovery single user boot
and a visudo was helping

when I run id I get uid=1000
and 02lancastr has uid=1001

looking forward to solution
[http://ubuntuforums.org/showthread.php?t=473630&highlight=users-admin](http://ubuntuforums.org/showthread.php?t=473630&highlight=users-admin)
[http://ubuntuforums.org/showthread.php?p=3086753#post3086753](http://ubuntuforums.org/showthread.php?p=3086753#post3086753)
[http://ubuntuforums.org/showthread.php?t=462991&highlight=users-admin&page=2](http://ubuntuforums.org/showthread.php?t=462991&highlight=users-admin&page=2)

[http://ubuntuforums.org/showthread.php?t=484828&highlight=users-admin&page=2](http://ubuntuforums.org/showthread.php?t=484828&highlight=users-admin&page=2)

The first user on your machine usually gets the UID of 1000.  Then the next user that you create would be 1001 and so on and so far.

---

### Post by SpiritIsReality on 2007-08-18
taurus   thanks

---

### Post by SpiritIsReality on 2007-08-18
02lancastr   how's it going

---

### Post by 02lancastr on 2007-08-18
Thanks alot for the solution, everything working fine now.

---

