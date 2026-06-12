---
title: "Samba - can't connect from Windows"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-07-21
I have an ISO in my /home folder that I need to copy over to my Windows machine.  I shared the /home folder through samba, but whenever I try to connect to the folder, it prompts me for a userrname and password.  I entered in the username and password I use to log into Ubuntu, but it didn't take it. How do i grant that user access to view the shared folder on Ubuntu?  Thanks.

---

### Post by scxtt on 2006-07-22
on ubuntu, type **smbpasswd -a $USER** - this will add a samba user once you enter a password ... [ you can substitute anything for $USER ]

---

### Post by OMRebel on 2006-07-22
I think I screwed something up.  That didn't work, so I decided I'd reinstall Samba.  But, I got:
E: samba: subprocess post-installation script returned error exit status 1

How bad did I make this?

---

### Post by OMRebel on 2006-07-22
Bump.

---

### Post by OMRebel on 2006-07-22
Nevermind.  I was able to get it fixed.  Removed Samba through Synaptic and then installed through apt-get, and that got it.

---

### Post by PriceChild on 2006-07-22
if you edit smb.conf and change security to share instead of user (uncommenting it also) then you can get rid of all authentication.

---

