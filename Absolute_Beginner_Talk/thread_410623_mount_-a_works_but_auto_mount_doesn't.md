---
title: "mount -a works but auto mount doesn't"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by bananabob on 2007-04-15
I have been driven crazy by this problem. My final course of action is to ask here for help.

I have a mount command in my fsab

> //thorium/bananabob /mnt/thorium smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user 0 0

This will not work on bootup.

If I try a 
> mount -a
There is no problem at all the thing mounts.

If I enter
> sudo smbmount //thorium/bananabob /mnt/thorium -o credentials=/root/.credentials,uid=1000,mask=000
It also mounts no problem

The fact that I have no problem with mount from the command line and with a mount -a indicates to me that everything is OK, and yet I must have something wrong for the mount not to work at bootup.

What have I got wrong guys?

---

### Post by Scunizi on 2007-04-15
did you create a directory in /media for thorium?  If not it has no place to mount at boot.

---

### Post by bananabob on 2007-04-16
I didn't have a directory in /media for thoriuim, but Iput one in, and it still doesn't work.
I used
> sudo mkdir /media/thorium
to create it, and then did a reboot. No luck at all

---

### Post by rsambuca on 2007-04-16
From the looks of things, should the thorium directory be in /mnt?

---

### Post by bananabob on 2007-04-16
That really shouldn't make ant difference. So to find out I mkdir a directory in /home, and it still doesn't work. But the mount -a does. That is the strange thing that I want people who read this to consider
This is from the mount man page

>   (i) The command
              mount -a [-t type] [-O optlist]
       (usually given in a bootscript) causes all file  systems  mentioned  in
       fstab  (of  the  proper  type  and/or  having  or not having the proper
       options) to be mounted as indicated, except for those whose  line  con&#8208;
       tains the noauto keyword. Adding the -F option will make mount fork, so
       that the filesystems are mounted simultaneously.

So iread that to mean that mount -a will; do exactly the same as automount at boot, but for me it doesn't work at boot, only when I mount -a. :confused:

---

### Post by NicoleM on 2007-04-16
i wish i knew the answer.  i have the same problem though.

i have one stubborn drive that won't auto mount but as soon as i give the mount command from the command line or I sudo mount -a it works like a charm.

it is correctly listed in my fstab also.

any chance your problem drive is external?  I'm not sure if it would make a difference but all of my drives auto mount fine except for the one (USB) external drive.

i've only been using ubuntu for a couple weeks now so I'v ebeen busy customizing and ironing out a few other minor issues so i haven't really sat down to deal with this yet...glad to see i'm not alone though

---

### Post by bananabob on 2007-04-16
It is external in a way - It is a samba fileshare on my other ubuntu box. Glad to know others have the same problem. Means that it is not just me doing something wrong. :D

---

### Post by aberry5555 on 2007-04-16
This presumably means the samba software starts up AFTER the fstab is initilialised, what you might want to do is, rather than include the network path in fstab, include it as a startup command (i.e. something like sudo mount //thorian) try and put it in as late a stage as possible.

---

### Post by bananabob on 2007-04-16
That's just what I thought after my last post - where would i put this mount command??

---

### Post by aberry5555 on 2007-04-16
ummmm, off the top of my head I can't really remember, lemme look at my post history and get back to you in a few minutes hehe

---

### Post by aberry5555 on 2007-04-16
the file you need to add the commands to is /etc/rc.local. Also, rather than deleting the entry in fstab, it would probably be easier and better to leave it in there and just add 

```
mount -a
```

also I don't think you have to add the "sudo" command to it as I think this file already assumes super-user status.

Good luck!

---

### Post by bananabob on 2007-04-16
:D :D :D :D :D  It works - Thank you for your help, I can stop sharping the razor now!

---

### Post by aberry5555 on 2007-04-16
Hehe, np

---

### Post by bananabob on 2007-04-16
That rc.local script is handy to know about. I have not come across that before.

---

### Post by aberry5555 on 2007-04-16
yeah I know, I came across it, used it a fair amount (to pre-load kde librariers for amorak and a messenger) then forgot about it :p. it's just like msconfig in windows, really.

---

### Post by NicoleM on 2007-04-16
thank you! this worked for me as well.   Not sure what caused it in my case as I'm not using samba, but I'm not going to look a gift horse in the mouth.  adding mount -a to the rc.local script worked like a charm.

:D

---

