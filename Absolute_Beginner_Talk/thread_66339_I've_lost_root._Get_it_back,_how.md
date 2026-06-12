---
title: "I've lost root. Get it back, how?"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by Haschtomte on 2005-09-16
Hello!

I have a Internetfriend which I've known for a while. I know that he is a so called "Linux guru". So I asked him to install some packets and configure it the way I wanted. He did it swelling and so on.

But today the devil got into him and he got made som funny things with my computer. So I deleted his account. And after that I can't login as root.
My other friend said that he maybe set himself as "UID=0". 

So, now I can't download any updates or do whatever.

Is it possible for me to root back?

Excuse my bad english. It has been many beers tonight. 

//Haschtomte

---

### Post by az on 2005-09-16
When you boot, can you chose the recovery mode (hit escape if you do not see the grub menu) and get to the command line prompt?  If so, type

adduser (name)

and then edit the /etc/sudoers file to make that new user have all the privileges.  (Read the comments in that file to see how to set it)

nano /etc/sudoers

If you get a prompt for the password when you enter recovery mode, then you are screwed.  That means your friend had set a password for the root account and you will need it.  To get past that you need to boot from a live cd and fix things through that.

---

### Post by Muhammad on 2005-09-17
If you're a sudoer, it's as simple as "sudo passwd root"

---

