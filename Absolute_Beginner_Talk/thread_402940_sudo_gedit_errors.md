---
title: "sudo gedit errors"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by j1n3l0 on 2007-04-06
hi,

i have noticed that lately when i try opening files with sudo gedit

```
sudo gedit some.file
```

i keep getting errors like this

```
(gedit:6130): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
```

the number **(gedit:nos)** is not always the same. i am not aware of any connections being made so i don't understand the need for a reply which it is talking about.

has anyone seen something like this? is there any reason i should be worried? what's this message bus being referred to?

newbie confused :mad:

---

### Post by taurus on 2007-04-06
What happens if you use

```
gksudo gedit some.file
```

---

### Post by j1n3l0 on 2007-04-08
hi,

i get the same error message after the following message

```
(gedit:4625): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

by the way i am using ubuntu 6.10 :) 

thanks

Nelo

---

### Post by al7kz on 2007-04-08
deleted

---

### Post by taurus on 2007-04-08
> **j1n3l0 said:**
> hi,

i get the same error message after the following message

```
(gedit:4625): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

by the way i am using ubuntu 6.10 :) 

thanks

Nelo

And a gedit window didn't open?  Otherwise, use a text editor like nano then.

```
sudo nano -Bw some.file
```
Save and exit with <Ctrl>o and <Ctrl>x.

---

### Post by Happy_Man on 2007-04-08
I get two errors, but it isn't a problem for editing stuff. The thing here, is whether it opens or not. If it doesn't, you have a problem. If it does, don't worry.

---

### Post by j1n3l0 on 2007-04-09
thanks for your help.

a gedit window does open, i was just worried it may be hiding a bigger problem! i will proceed like its all good and perhaps have a look at nano.

once again, thanks folks!

Nelo

---

### Post by bulldog on 2007-04-09
The 'error' you're getting,is a known bug with 'low priority'.
It doesn't harm your system in any way,so don't worry about that.

---

### Post by STREETURCHINE on 2007-04-09
oops you were to quick bulldog...:)

this has been a bug for a while,i have been using ubuntu for about six months now ,may be a bit longer.but it has been present the whole time i have been using it .

nothing to worry about.
there was a post about this a while ago cant remember where .

---

### Post by Ubluedog on 2007-04-09
i got the same error "none pf the authentication protcols are installed "etc when trying to sudo gedit files.
i reinstalled , no luck , then installed the alternate cd, then installed the  normal instal over that. all of a sudden it worked , so its like a module got left out on the main install. now my machine is old and limited, its a armada 1700
cheers

---

