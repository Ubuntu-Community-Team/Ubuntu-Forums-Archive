---
title: "system crash,  stuck in terminal.  how do I get back to the gnome environment"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by jaws31415 on 2008-04-10
my system crashed and now it opens with a full screen terminal. can I get back into the gnome environment/desktop?

---

### Post by TeoBigusGeekus on 2008-04-10
Type
```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure your graphics.

---

### Post by Crafty Kisses on 2008-04-10
> **jaws31415 said:**
> my system crashed and now it opens with a full screen terminal. can I get back into the gnome environment/desktop?

What were you exactly doing at the time of the crash?

---

### Post by jaws31415 on 2008-04-10
I was trying to remove totem-xine plugin package and it started deleting everything...I mean everything,     so I shut it off.

---

### Post by jaws31415 on 2008-04-10
I tried this, no go

---

### Post by perce on 2008-04-10
> **jaws31415 said:**
> I was trying to remove totem-xine plugin package and it started deleting everything...I mean everything

If the problem is that it has removed too much, you can probably fix that with

```
 sudo apt-get install ubuntu-desktop

```

---

### Post by jaws31415 on 2008-04-10
It says E: dpkg interrupted. I need to manually run 'dpkg --configure -a'.  and says I need to be super user. how do I do this, sudo

---

### Post by perce on 2008-04-10
> **jaws31415 said:**
> It says E: dpkg interrupted. I need to manually run 'dpkg --configure -a'.  how do I do this

sudo dpkg --configure -a

---

### Post by jaws31415 on 2008-04-10
the screen went blank.  should this take a long time?  will I be able to retrieve my files?

---

### Post by perce on 2008-04-10
I have no idea, it depends on how many packages it must configure. But what do you mean by blank? everything disappeared, or you can still see some writings? Look at the disk light: if it's on, it's doing something and you shouldn't worry.

---

### Post by perce on 2008-04-10
For your files you shouldn't worry: if you made a separate home partition they'll be safe even if you reinstall. If you didn't make a home partition, you can still use a live CD to retrieve them. But now let's focus on trying to restore the system without reinstalling.

---

### Post by jaws31415 on 2008-04-10
yeah everything disappeared, it is on, I'll give it some time

---

### Post by jaws31415 on 2008-04-10
so this did absolutely nothing.......anybody got any ideas

---

