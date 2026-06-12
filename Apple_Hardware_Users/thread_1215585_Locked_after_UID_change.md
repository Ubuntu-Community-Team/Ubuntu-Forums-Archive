---
title: "Locked after UID change"
date: 2009-07-17
forum: Apple Hardware Users
---

### Post by tripundra on 2009-07-17
Hi.

I recently changed the UID and GID for Ubuntu, fromm 1000 to 501.
Did this to be able to open my user directory on the Mac Osx partition. It was working alright , even loged out and back in and it was ok.
After a shut down and reboot, I was not able to open my account. It says I have no permissions to read and right any file.
How can I change permissions again to be able to log in or how do I change all the files permissions to 501?
I'm a newbie so please bear with me!

Thankshttp://ubuntuforums.org/images/icons/icon8.gif

---

### Post by Richardcavell on 2009-07-17
Hi, tripundra.

I'm eager to help you, but I'm not sure what symptoms you are getting. Can you log in to Ubuntu and get to a desktop?  Once you are in Ubuntu, can you try this within an Ubuntu terminal: ```
cd ~ && ls -l && id -u && id -g
```and print the output here for us to look at.

Richard

---

### Post by tripundra on 2009-07-17
hi Richard,

I can log into my account but like I said I get plenty of error messages.
I do not get a complete desktop, the mouse loads, but none of the deskbar with the menus appear. I cannot load a terminal, afaik. and doing alt+ctrl+del to log out gets a msg saing" couldn't execute command: gnome session-save, etc etc".
I tried log in with root but I hadn't allowed root to log in, so I can not.
There is only one account created.

---

### Post by tripundra on 2009-07-17
Hi Richard,

I entered in recovery mode and asked to "Drop to root shell prompt"
pasted the commands you sent and came out as,
total 0
0
0

Don't know if it's what you want!Or if I need to change to my user account,( don't know how to do it)!

thanks
Edgar

---

### Post by iamkrazee on 2009-07-17
```
chown -hR <username> /home/<username>
```

---

### Post by sisco311 on 2009-07-17
> **Richardcavell said:**
> Hi, tripundra.

I'm eager to help you, but I'm not sure what symptoms you are getting. Can you log in to Ubuntu and get to a desktop?  Once you are in Ubuntu, can you try this within an Ubuntu terminal: ```
cd ~ && ls -l && id -u && id -g
```and print the output here for us to look at.

Richard

in recovery mode you are logged in as root so ~ is /root and id returns root's uid...

@OP:
post:
```
ls -l /home/username
ls -ald /home/username/
id username
```

btw, how did you change your uid and gid?

---

### Post by iamkrazee on 2009-07-17
IMO although my method is crude, chown should set the right UID/GIDs.

And the "cd ~" part is why i told you to skip that and go straight for chown. Should work. Please report back.

---

### Post by tripundra on 2009-07-17
tried the chown -hr .....
comes out as :
chown: invalid option -- 'r'


did the ls -l /home/tripundra

came out as:
total 0 
lrwxrwxrwx 1 root root 56 Jul 15 18:00 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 root root 56 Jul 15 18:00 README.txt -> usr/share/ecryptfs-utils/ecryptfs-mount-private.txt


then :  ls- ald /....
came as:

dr-x------ 3 tripundra 1000 4096 Jul 15 18:00 /home/tripundra


then : id tripundra
comes as:

uid=501(tripundra) gid=501(tripundra groups=501(tripundra),4(adm),20(dialout),24(cdrom),29(audio),46(plugdev),109(lpadmin),117(admin),122(sambashare)




I changed the UID and GUI by following the post on Apple users for Ubuntu 9.04 installation.


Thanks
Edgar

---

### Post by sisco311 on 2009-07-17
try:
```

chown -R tripundra\: /home/tripundra
chmod 0750 /home/tripundra

```

---

### Post by tripundra on 2009-07-17
Hi Just followed the manual again to rechange to UID and GID to 1000 
I don't know what the code means but know how to past it! jejeje


Code:

sudo groupmod -g 1000 tripundra

sudo usermod -u 1000 -g 1000 tripundra

And now I'm able to log on,

So it's now working!
Thanks to you all!
If you have an idea on how to change the UID and GUI to 501 and still log in, I would really appreciate!!
As a side line I followed your thread Richard!! It made my Installation very easy!!Thanks

---

### Post by iamkrazee on 2009-07-17
Little advise, you need to read the cases properly, it was a capital 'r' in chmod. Nonetheless, good to know your problem's solved.

---

### Post by iamkrazee on 2009-07-17
Ok sorry, I missed your last line. So your problem still isn't solved. This time, don't go to failsafe terminal. Just fire up the one you have.

Do 
```
sudo su
```

<Code to change your uid/gid combo>

then 

```

chown -hR tripundra /home/tripundra
chmod 0774 /home/tripundra

```

This is, again, a very crude method. But it'll get you working without fail.

Fire up all those commands together in the same konsole.

---

### Post by iamkrazee on 2009-07-17
> **iamkrazee said:**
> Ok sorry, I missed your last line. So your problem still isn't solved. This time, don't go to failsafe terminal. Just fire up the one you have.

Do 
```
sudo su
```

<Code to change your uid/gid combo>

then 

```

chown -hR tripundra /home/tripundra
chmod 0774 /home/tripundra

```

This is, again, a very crude method. But it'll get you working without fail.

Fire up all those commands together in the same konsole.

By the console you "have" i mean your gnome-terminal/konsole. 

Also, the code should have been:

```

sudo chmod 0774 /home/tripundra
sudo chown -hR tripundra /home/tripundra

```

---

### Post by Richardcavell on 2009-07-17
Hi,

I'm glad to hear that you liked my instructions. However, I'm always keen to hear when people manage to find a loophole. Yes, you should have used a capital 'R' on that command. I'll update my instructions to make certain that people know that.  Please continue to let me know if there's anything I can do to make the instructions more foolproof.

Richard

---

