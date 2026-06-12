---
title: "LAMP/Samba permission woes"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by BlueAngel-CPT on 2007-12-08
Hi everyone,

I'm hoping someone here will be able to help solve my problem. I've recently installed Ubuntu Gutsy on my old PC, with three main purposes:

1) to serve as a LAMP server
2) to serve as a file server
3) for me to get more comfortable with Linux in general

I've spent quite a bit of time Googling around for answers to a particular problem I'm currently experiencing.

Brief overview: I've got /var/www/ set up as a shared folder using Samba. Every time I save any file from my Windows PC (regardless of what I've made the permissions before), it resets the owner and permission levels on the file, with the end result that I can't view it through the browser. I've tried changing the permissions on the parent directory, I've tried changing Samba from being user level (i.e. you have to provide login details in order to be able to connect to the shared folder) to being anonymous shares ... that didn't seem to make a difference.

What I'd like to know, is what the proper way is to set this up, so that I don't have to chmod the file before being able to view it through my browser. I thought about creating a Samba user www-data ... but somehow I don't think that is the right way of doing things. I'm pretty sure the solution is probably pretty obvious, but I'd like someone to steer me in the right direction, please.

---

### Post by BlueAngel-CPT on 2007-12-09
*bump*

---

### Post by BlueAngel-CPT on 2007-12-09
I fixed it! After reading some more documentation on Samba, I figured out that I need to make my smb.conf look something like the below:

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

with the most-important bits of course being about create-mask, and possibly force-group.

Yay!

---

