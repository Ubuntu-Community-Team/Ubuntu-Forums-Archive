---
title: "root password"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by ZiGz on 2006-04-04
On one machine I did an expert install and had trouble with sudo, I was able to get instructions on adding my user account to the admin list and that worked great.  I was also able to use root if I wanted.

This machine I did default and was not asked for a root password.  What is the deal are we not smart enough to be trusted with admin access on our own machines?  How do I set a root password.  

I want to be able to use Find / Replace in Gedit to edit the Source file from Hoary to Breezy so I can update this install and I can't even do that with this user.

---

### Post by ZiGz on 2006-04-04
Ok I see where I can Manually set the root password, if I do this will I break sudo?

---

### Post by meborc on 2006-04-04
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

there is a point behind sudo... why it is used...

---

### Post by carlosqueso on 2006-04-04
You are trusted with the password to your machine.  You use sudo to temporarily become root, and then you type your USER password.  It basicly makes it hard for people to break into your machine. 

That said, to create a root password, type sudo passwd root in a terminal, and you can set it.  It MAY break some of the graphical config tools though.

---

