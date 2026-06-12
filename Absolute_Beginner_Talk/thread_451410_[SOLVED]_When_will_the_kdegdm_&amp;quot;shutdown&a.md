---
title: "[SOLVED] When will the kde/gdm &amp;quot;shutdown&amp;quot; and &amp;quot;restart&amp;quot; bug be fi"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-05-22
The bug I am referring to is here:

[https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695]("https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695")

I see that a fix has been put into the feisty-proposed repo, but is it wise to go ahead and install it from the proposed repo, or would it be much better to wait until it gets put into the main updates repo?

And does anyone have an idea of when that patch will be moved into the main updates?

---

### Post by Cypher on 2007-05-22
OK..I'm curious, if you want to use KDE as your WM, why not use KDM as well?

---

### Post by laptoplinux on 2007-05-22
Mostly because I like to switch back and forth between the two from time to time, and I've noticed that if I use kdm, gnome's keyring is unable to remember the password for my wireless network and I have to enter my password twice at login.  But if I use gdm, gnome works fine on that point and kde can still always remember my wireless password.

---

### Post by Pollywoggy on 2007-05-22
> **Cypher said:**
> OK..I'm curious, if you want to use KDE as your WM, why not use KDM as well?

I use gdm because if I compile gdm with the secure xdmcp option, I can securely use xdmcp if the remote side runs sshd.

I believe I can't do that with kdm.

BTW I did not know it was a bug, I thought it was the way KDE was supposed to behave now.
It would be nice to be able to shutdown or restart without first exiting to gdm.

---

