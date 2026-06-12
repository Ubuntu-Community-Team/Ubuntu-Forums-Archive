---
title: "Can access internet but can't access local network computers"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by holc7omb on 2006-06-10
When I try to access my local network and get to my other computers I get a prompt for a log on user id and password.  I have no idea what it is looking for, I tried my logon and password.  I can access the internet however.

I can, from my windows laptop, access the ubuntu machine via VNC but I cannot log on to the computer from the windows machine to browse the hard drive.

Lastly, I cannot access the ubuntu box via my Mac desktop using Apple remote.  When I use Chicken of the VNC to remote control the connection is very very slow as compared to my windows laptop connection which is very fast.  

I want to be able to browse my ubuntu hard drive and share files back and forth.  Any ideas?

---

### Post by blackjack6.21.91 on 2006-06-10
Yeah.  It looks like you have samba installed, but not configured.  Post the contents of your sources.list by entering the following command (assuming you are in gnome)

> sudo gedit /etc/samba/smb.conf

It's a file that essentially defines your shared preferences.  And I would look to make sure Samba is compatible with Macs.. I wouldn't know

---

### Post by holc7omb on 2006-06-14
I tried this.  I changed a couple of things but honestly I didn't see anything that seemed to pertain to a mac.  It seems there are a lot of options that aren't populated in the file.  Do you know what I should be looking to change?

---

