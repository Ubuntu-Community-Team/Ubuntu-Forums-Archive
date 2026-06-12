---
title: "[SOLVED] Selective sharing folders on hard drive"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by ubername on 2008-04-19
Hi

I have two Ubuntu boxes networked, each has multiple users (the same usernames on both boxes).I have a new USB drive on which I have set up a folder for each user. I have successfully set the permissions so that, from the box where the USB drive is attached, each user can access their, and only their, folder. I now would like to make it so that from the other box each user can access their, and only their, folder (Read Write Access). I don't know how to even start this, as I seem to have only the option of sharing a folder with everyone. Have I missed something really obvious?

TIA

---

### Post by linfidel on 2008-04-20
I'm not really sure about this either, but I have a suggestion that might help, and has a finite chance of being correct.  :)

I don't think you can set the permissions on the device itself; a username on one computer is not the same as the same username on another.  Unless you can specify the computer name or domain name (if you have a domain controller) with the user name, there's no way to match them.

I think you can mount it in one computer, set the full permissions for the person on that computer that needs access, and deny all others.

Then, on another computer, set the other user to have full permissions, and deny all others.

Like any drive, if you take it out and put it in a different computer, anyone with root privileges can change the permissions.  Encryption is the only way to really make it private.

---

### Post by sdennie on 2008-04-20
I think you may want to look at Samba.  Some basic but good information about setting up Samba stuff on Ubuntu can be found here: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)

---

