---
title: "Samba again"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-01-01
Hello all,
I'm having some difficulty setting up a samba share. First, I installed Samba. Next, I created a directory called shared in the root (this directory is on a new hard drive I just added). I can write to the disk from my user account, wgant. The directory is owned by root.

Now, I right-clicked on the directory to make it a share. I also edited the samba configuration file as follows (this isn't the whole file, just the relevant section):

security = user
username map = /etc/samba/smbusers

I can map the drive from Windows, but I can't write to it. Also, I checked out in the file system and the smbusers file isn't there. What do I need to put in the file to make this work?

---

### Post by mistypotato on 2007-01-01
Well,

Day 3 of Samba hell I give up.
I'm a rather experienced user...not so much Linux...but IT person for 20+ years.
Used Samba once before with Mandrake and got it working.
USUALLY... I can get things working when noone else can.....but not this time.

Tried everything in hundreds of posts here and could not get the .....thing working.

So I was going to uninstall Samba and all the other files I had installed and try to start fresh,,,but then Linux blew up and started telling me there were "broken" packages and generally everything started falling apart.  ](*,) 

So much for samba. [-( 

Hope you have better success.

---

### Post by freebeer on 2007-01-02
have you added users to the Samba list?  It sounds from your description that you need to set the permissions within Samba.

---

