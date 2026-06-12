---
title: "changing the root user"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-12-15
Having installed 7.10 using my name and password. I now wonder if its possible to change these details and remove my own. I've now added my daughter as a root user in administration - users and groups and then deleted myself from the list. Trouble is when the PC is rebooted I'm still there as a user and can log on with my details. Looking for advice please.

---

### Post by llamakc on 2007-12-15
So you wish to remove yourself as a user completely, correct?

---

### Post by a.v.l on 2007-12-15
> **llamakc said:**
> So you wish to remove yourself as a user completely, correct?

Yes thats right, I'm giving my daughter this PC and want only her details on it.

---

### Post by llamakc on 2007-12-15
Okay, this does exactly what it sounds like it does. You'll need to run it as your daughter (who has admin powers according to your post).

```

sudo deluser --remove-home YOURUSERNAME

```

And yes, it will remove every file in your /home/USERNAME directory, as well as the directory itself. 

Please be certain there is nothing you want or need before proceeding.

---

### Post by a.v.l on 2007-12-15
> **llamakc said:**
> Okay, this does exactly what it sounds like it does. You'll need to run it as your daughter (who has admin powers according to your post).

```

sudo deluser --remove-home YOURUSERNAME

```

And yes, it will remove every file in your /home/USERNAME directory, as well as the directory itself. 

Please be certain there is nothing you want or need before proceeding.

Thanks that worked fine, but for one small thing,  It seems that my name remains as a group user according to a message in the terminal. 


Quote:
userdel: cannot remove group MYUSERNAME which is a primary group for another user.
End of quote

It tells me that I have been removed as a root user, which I've confirmed by rebooting the PC in my daughters name and I no longer appear as a user 

What would be the code to remove me as a group user please.

---

### Post by HokeyFry on 2007-12-15
Actually your username *is* a group as well. On my system the only members of this group is myself and root. Maybe remove root from the group?

---

### Post by llamakc on 2007-12-15
What is the output of this:

```

cat /etc/group | grep YOURUSERNAME

```

---

### Post by rahul_bhise on 2007-12-15
may be going to system>administer>user and group
clicking on maneage group and deleting your group may help
but take advise of someone who has more beans than me

---

### Post by a.v.l on 2007-12-15
> **llamakc said:**
> What is the output of this:

```

cat /etc/group | grep YOURUSERNAME

```

This is the output:

DAUGHTERSUSERNAME@MYUSERNAME-desktop:~$ cat  /etc/group 1 grep MYUSERNAME
MYUSERNAME:x:1000
DAUGHTERSUSERNAME@MYUSERNAME-desktop:~$
DAUGHTERSUSERNAME@MYUSERNAME-desktop:~$
DAUGHTERSUSERNAME@MYUSERNAME-desktop:~$
************************************************************************
I was unable to copy and paste this from one computer to the other so I've typed it out but there is one mistake in the above text where there is a number 1 after (etc/group 1 grep) The 1 should be a vertical line as found on the key above the tab key, but I couldn't work out how to use it as there are two other choices in the same key. 

The smiling face is not my doing either there sould be a :cross there:X

---

### Post by a.v.l on 2007-12-15
> **rahul_bhise said:**
> may be going to system>administer>user and group
clicking on maneage group and deleting your group may help
but take advise of someone who has more beans than me

Thanks but that didn't work as my name kept appearing there after deleting it.

---

### Post by llamakc on 2007-12-15
As your daughter:

sudo delgroup YOURUSERNAME

:)

---

### Post by a.v.l on 2007-12-15
> **llamakc said:**
> As your daughter:

sudo delgroup YOURUSERNAME

:)

Thanks - When I do this I get the message:

usr/sbin/delgroup: DAUGHTERSUSERNAME still has MYUSERNAME as their primary group!

---

### Post by llamakc on 2007-12-15
```

cd /home && ls -l

```

and

```

cat /etc/group | grep DAUGHTERUSERNAME

```

Please.

---

### Post by a.v.l on 2007-12-15
The results:

I was unable to copy and paste the terminal results because I was informed I was trying to send to many images.  So I've typed some of them out best possible.




floppy:x:21: daughtername
tape:x:26: daughtername
audio:x:29: daughtername
dip:x:30: daughtername
plugdev:x:46: haldaemon.daughtername
scanner:x:104: hplip. daughtername
fuse:x:106: daughtername
admin:x:110:daughtername
daughtername@myname-desktop:/home$

 


I'm still in groups and if I delete my name there when I open it again it re-appears.

---

### Post by a.v.l on 2007-12-15
The smillies appear when ever I type a colon followed by a cross :   x

---

### Post by llamakc on 2007-12-15
Well then what about the single line that begins with

DAUGHTERNAME in /etc/group?

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> Well then what about the single line that begins with

DAUGHTERNAME in /etc/group?

*************

My apologies.

drwxr-xr-x 27 Daughtersusername Myusername 4096 2007-12-16 10:59 Daughtersusername
Daughtersusername@Myusername-desktop:/home$ cat /etc/group | grep Daughtersusername

---

### Post by llamakc on 2007-12-16
```

usermod -g DAUGHTERUSERNAME DAUGHTERUSERNAME

```

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> ```

usermod -g DAUGHTERUSERNAME DAUGHTERUSERNAME

```

Results of above:

Daughtersusername@Myusername-desktop:~$ usermod -g Daughterusername Daughterusername
usermod: unknown group Daughterusername
Daughterusername@Myusername-desktop:~$

---

### Post by llamakc on 2007-12-16
Doh! I'm a doofus. Your daughter was a member of YOUR group and didn't have her own.

Doing the following will change YOURUSERNAME to DAUGHTERUSERNAME for the gid.

```

sudo groupmod -n DAUGHTERUSERNAME YOURUSERNAME

```

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> Doh! I'm a doofus. Your daughter was a member of YOUR group and didn't have her own.

Doing the following will change YOURUSERNAME to DAUGHTERUSERNAME for the gid.

```

sudo groupmod -n DAUGHTERUSERNAME YOURUSERNAME

```


"YOU ARE BRILLIANT"

My group has now gone - thanks so much. One thing when I go to the terminal my name still appears as below. Anything I do to remove it?

Daughtersusername@Myusername-desktop:~$

---

### Post by llamakc on 2007-12-16
sudo nano /etc/hostname

And you may have to change a line in /etc/hosts too.

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> sudo nano /etc/hostname

And you may have to change a line in /etc/hosts too.

*******************************************************


Results of doing the above:

GNU nano 2.0.6 File: /etc/hostname


myusername-desktop

Then a number of different  menues appear at the bottom of the treminal like: 
get help - writeout - read file - prev page- cut text and more. 

At this point I'm lost again

---

### Post by llamakc on 2007-12-16
You can use a graphical editor instead. I assumed you were familiar with nano. My bad.

```

sudo gedit /etc/hostname

```

```

sudo gedit /etc/hosts

```

and replace YOURUSERNAME with whatever you want. Just make them match character for character in both files.

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> You can use a graphical editor instead. I assumed you were familiar with nano. My bad.

```

sudo gedit /etc/hostname

```

```

sudo gedit /etc/hosts

```
a
and replace YOURUSERNAME with whatever you want. Just make them match character for character in both files.

**************************************************

When I enter sudo gedit /etc/hostname I get to a graphical page open where I have been able to change my user name to my daughters username and then saved it.

When I then enter sudo gedit /etc/hosts in the terminal again, I only get a "blinking" curser and nothing happens.

Repeating the the above does the same but I notice the second time around when I enter sudo gedit /etc/hostname and get taken to the graphical page the entry there is now my daughters username - desktop.  So close now I can taste  success, ,

---

### Post by llamakc on 2007-12-16
ls -l /etc/hosts

---

### Post by The Cog on 2007-12-16
Now you have a problem. You probably cannot use sudo any more. It could be a mistake to edit /etc/hostname then /etc/hosts. If your hostname in /etc/hostname isn't listed in /etc/hosts then sudo doesn't work. So after changing /etc/hostname, you can't do the second step of editing /etc/hosts. 

I think you will need to boot into recovery mode and then use the command 
**nano /etc/hosts**
and use the nano editor to change and save your hosts file. There should be a line starting with "127.0.1.1" and a space and then the computername as given by /etc/hostname. Once these two files agree, you can reboot and log in normally, and sudo will work again. Nano isn't too hard, fortunately.

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> ls -l /etc/hosts

Results:

Daughterusername@Myusername-desktop:~$ ls -l /etc/hosts
-rw-r--r-- 1 root root 248 2007-12-08 14:21 /etc/hosts
Daughterusername@Myusername-desktop:~$ 
Daughterusername@Myusername-desktop:~$

---

### Post by llamakc on 2007-12-16
> **The Cog said:**
> Now you have a problem. You probably cannot use sudo any more. It could be a mistake to edit /etc/hostname then /etc/hosts. If your hostname in /etc/hostname isn't listed in /etc/hosts then sudo doesn't work. So after changing /etc/hostname, you can't do the second step of editing /etc/hosts. 

I think you will need to boot into recovery mode and then use the command 
**nano /etc/hosts**
and use the nano editor to change and save your hosts file. There should be a line starting with "127.0.1.1" and a space and then the computername as given by /etc/hostname. Once these two files agree, you can reboot and log in normally, and sudo will work again. Nano isn't too hard, fortunately.

Thanks, The Cog. I've never ran into that issue before. Good catch. 

To reach the OP's desire of changing the hostname, would you have recommended changing /etc/hosts FIRST before /etc/hostname?

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> Thanks, The Cog. I've never ran into that issue before. Good catch. 

To reach the OP's desire of changing the hostname, would you have recommended changing /etc/hosts FIRST before /etc/hostname?


No, thank you, you have been extremely helpful.  Am I right in thinking we have come to a stop for the moment?

---

### Post by The Cog on 2007-12-16
**sudo gedit /etc/hostname /etc/hosts**
is good. Or use the GUI networking setup, which configures both at the same time. Personally, I always **sudo -i** before doing a series of changes, and in this case I don't need sudo again so the gotcha doesn't arise.

a.v.l.: Is the box sorted out now, or do you still have a problem?

---

### Post by llamakc on 2007-12-16
> **The Cog said:**
> **sudo gedit /etc/hostname /etc/hosts**
is good. Or use the GUI networking setup, which configures both at the same time. Personally, I always **sudo -i** before doing a series of changes, and in this case I don't need sudo again so the gotcha doesn't arise.

a.v.l.: Is the box sorted out now, or do you still have a problem?

I too do sudo -i (and am comfortable with using root in situations). 

I hope the OP has it figured out.

---

### Post by a.v.l on 2007-12-16
> **The Cog said:**
> **sudo gedit /etc/hostname /etc/hosts**
is good. Or use the GUI networking setup, which configures both at the same time. Personally, I always **sudo -i** before doing a series of changes, and in this case I don't need sudo again so the gotcha doesn't arise.

a.v.l.: Is the box sorted out now, or do you still have a problem?

My username has been removed from Root user and from groups -  great. It still appears in the terminal as shown below, My daughter tells me it isn't a problem for her so can you see any issues arising from it still appearing in the terminal:

Terminal example:

Daughterusername@Myusername-desktop:~$

---

### Post by llamakc on 2007-12-16
> **a.v.l said:**
> My username has been removed from Root user and from groups -  great. It still appears in the terminal as shown below, My daughter tells me it isn't a problem for her so can you see any issues arising from it still appearing in the terminal:

Terminal example:

Daughterusername@Myusername-desktop:~$

Until you reboot it will remain that way. The issue tha was brought up was the usage of 'sudo'. 

Can you successfully use "sudo" to do anything right now?

---

### Post by a.v.l on 2007-12-16
> **llamakc said:**
> Until you reboot it will remain that way. The issue tha was brought up was the usage of 'sudo'. 

Can you successfully use "sudo" to do anything right now?



Forgive me but I've become a little lost I'm afraid, I've rebooted my PC and now when I open the terminal now I get this below, which I imagine is what I need it to be.

DAUGHTERSUSERNAME@DAUGHTERSUSERNAME-desktop:~$   




I'm unsure if sudo is working, can I ask if there is a command I can enter in the terminal to test it.

---

### Post by llamakc on 2007-12-16
> **a.v.l said:**
> Forgive me but I've become a little lost I'm afraid, I've rebooted my PC and now when I open the terminal now I get this below, which I imagine is what I need it to be.

DAUGHTERSUSERNAME@DAUGHTERSUSERNAME-desktop:~$   




I'm unsure if sudo is working, can I ask if there is a command I can enter in the terminal to test it.

Yes: open the terminal and type:

sudo apt-get update

Does that update the repositories?

---

### Post by a.v.l on 2007-12-17
> **llamakc said:**
> Yes: open the terminal and type:

sudo apt-get update

Does that update the repositories?

llamakc

Entering the above command in the terminal gave the result below, which I assume means my daughter is up and running as normal with only her name as root and in groups and sudo is working under my daughters name and password. 

Terminal Result of (sudo apt-get update)

daughtersusername@daughtersusername-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Fetched 1B in 0s (1B/s)  
Reading package lists... Done
daughtersusername@daughtersusername-desktop:~$ 


Have we done it? :)

---

### Post by llamakc on 2007-12-17
Sure looks like it to me.

---

### Post by a.v.l on 2007-12-17
> **llamakc said:**
> Sure looks like it to me.



In that case ..........thank you very much, you have been a great help.

---

