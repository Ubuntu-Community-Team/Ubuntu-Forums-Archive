---
title: "permissions"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-24
**I was in the Forum quite a bit yesterday and solved a lot of my problems thanks to the members. My main problem was being able to see a new slave HD.  However, even though I can see it under Home now there is a lock on it and also on my Examples folder.  I guess it boils down to changing permissions.  Any suggestions?**

---

### Post by mattg89 on 2007-06-24
Would

sudo chmod 775 /some/folder

work? I'm not sure how it copes with mounted drives.

---

### Post by guddr on 2007-06-24
I appreciate the help but i'm such a beginner im not sure what to type?  Would it be: sudo chmod 775 /media/HD40?

---

### Post by isaacj87 on 2007-06-24
There's one thing you could do...it's really really noobish...but you could log out and log in as root. then go to the selected folder, right click, properties and go to permissions.

---

### Post by chrisbish on 2007-06-24
> **isaacj87 said:**
> There's one thing you could do...it's really really noobish...but you could log out and log in as root. then go to the selected folder, right click, properties and go to permissions.

how do you login as root?
i have got this probleme to
i tried login in at the login screen as root and it said i cant login here.

---

### Post by guddr on 2007-06-24
Hi,  Thats just my problem..  I tried the same thing, to log out and it asked for my name and password.. I tried to change permissions this way and could not.  Maybe im like you and not really logging in as root. Hopefully some member can solve our problem..Regards:)

---

### Post by chrisbish on 2007-06-24
yea i tried changing my account in users and groups and put my self in the root group - dindt work
then i tried loggin in as root and it said i cant log in at the login screen so were do i log in as root from?

---

### Post by Vodkayum on 2007-06-24
ubuntu does not allow root login I have the same problem and tried that

---

### Post by Vodkayum on 2007-06-24
This seems to be a common issue has anyone ever resolved this?

---

### Post by guddr on 2007-06-24
Probably there are a few commands that would do what we want but I dont know what they are. Hopefully someone can help us out.

---

### Post by chrisbish on 2007-06-24
im trying to set up Apache + PHP
its finished installing but i cant past anything in the web folder

and its to do with permissions again

---

### Post by isaacj87 on 2007-06-24
Here the solution:

Go to System->Adminstration->Users & Groups

Choose root, then properties, and then set the password by hand. Close it.

Then go back to System->Adminstration->Login Window

Go to the Security tab and in the Security part check 'Allow local system adminstrator login'

Now you can log in and log back out.

Remember to log out of root when you're done..not switch user.

Let me know guys if this works.

EDIT: Like I said...it's noobish, but I just like logging in as root and moving files or changing permissions that way...it makes it easier to do. :) oh and REMEMBER your root password that you set!!

---

### Post by Vodkayum on 2007-06-24
thx sam for telling about the chown command that did it for me. My problem is resolved thx much

---

### Post by dhruva023 on 2007-06-24
open terminal
and type this command 

"
gksudo nautilus

"

it will open a file browser with root access.

in that file browser, you can modefy any file.
but if you close that file browser, then you have to follow this again.

---

### Post by isaacj87 on 2007-06-24
> **chrisbish said:**
> im trying to set up Apache + PHP
its finished installing but i cant past anything in the web folder

and its to do with permissions again

Could you clarify this a little more?

---

### Post by isaacj87 on 2007-06-24
> **dhruva023 said:**
> open terminal
and type this command 

"
gksudo nautilus

"

it will open a file browser with root access.

in that file browser, you can modefy any file.
but if you close that file browser, then you have to follow this again.


THANK YOU....I've been looking for a way to access Nautilus as root without having to log out and in as root. :)

---

### Post by Ayuthia on 2007-06-24
The preferred route to do things as root is to use sudo or gksudo/gksu (for graphical programs needing root access).

---

### Post by chrisbish on 2007-06-24
it just screwed my ubuntu
i logged out of root

for 10mins all i had was a black screen mith my mouse in the busy mode

i hit reboot now it loads past the ubuntu loader then come up with> BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by guddr on 2007-06-24
Thanks for the suggestion however when I go into nautilus as root all I can see is Desktop and not any HD or other folders.  What can I do to see all the folders in root? Thanks.+

---

### Post by zenkaon on 2007-06-24
open a terminal, cd to the directory you want to edit files in. Type:
chmod 755 *

bingo

---

### Post by guddr on 2007-06-24
Thanks however here is what I get:

macd@macd-desktop:/media/HD40$ cd /media/HD40
macd@macd-desktop:/media/HD40$ chmod 755 *
chmod: changing permissions of `lost+found': Operation not permitted
macd@macd-desktop:/media/HD40$

---

### Post by guddr on 2007-06-24
How do I change th HD40 HD folder to macd instead of root?

macd@macd-desktop:~$  dir -l
total 184
drwxr-xr-x  2 macd macd   4096 2007-06-22 21:23 Desktop
drwxr-xr-x 28 macd macd  12288 2007-06-20 16:15 Documents
lrwxrwxrwx  1 macd macd     26 2007-06-16 07:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 root root   4096 2007-06-23 19:38 HD40
drwxr-xr-x  2 macd macd 122880 2007-06-17 22:57 My\ Music
drwxr-xr-x 16 macd macd  36864 2007-06-16 21:38 My\ Pictures
drwxr-xr-x 13 macd macd   4096 2007-06-18 10:58 Photos

---

### Post by guddr on 2007-06-24
I am still trying to unlock my slave HD.  Ive logged in as root through Administration, Users and Groups and have actually changed permissions in the folder HD40.  It doesnt seem to do anything after I log out of root and in under my name. What am I doing wrong?? My dir -l is:

macd@macd-desktop:~$ dir -l
total 184
drwxr-xr-x  2 macd macd   4096 2007-06-22 21:23 Desktop
drwxr-xr-x 28 macd macd  12288 2007-06-20 16:15 Documents
lrwxrwxrwx  1 macd macd     26 2007-06-16 07:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 root root   4096 2007-06-23 19:38 HD40
drwxr-xr-x  2 macd macd 122880 2007-06-17 22:57 My\ Music
drwxr-xr-x 16 macd macd  36864 2007-06-16 21:38 My\ Pictures
drwxr-xr-x 13 macd macd   4096 2007-06-18 10:58 Photos

Thanks for any help you could supply.

---

