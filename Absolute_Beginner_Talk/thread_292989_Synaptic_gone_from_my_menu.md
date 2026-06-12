---
title: "Synaptic gone from my menu"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by BWF89 on 2006-11-04
I booted up this morning to find that Synaptic Package Management was gone when I went to *System > Administration*.

So I go to *System > Preferences > Menu Layout* figuring the synaptic box must have gotten unchecked somehow. So I go to re-check the synaptic box and nothing happens. It won't let me put synaptic back in the menu.

So I figure I'd go into Terminal and type in "synaptic" to access it manually. The program loads up and tells me I'm "Starting without administrative privileges. You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them."

How can I get synaptic back into my menu and how do I start with admin privileges?

---

### Post by Ecthelion on 2006-11-04
```
sudo synaptic
```

for the root acces...

---

### Post by BWF89 on 2006-11-04
When I type in "sudo synaptic" it asks for my password so I put in the admin password I made. It keeps saying that I didn't get the password right.

Then I exit out of that and enter "su -", my admin password, then "synaptic" and it says "(synaptic:8084): Gtk-WARNING **: cannot open display:"

---

### Post by ewl1217 on 2006-11-04
Try doing this instead. Press Alt+F2 and run
```
gksudo synaptic
```The errors from the terminal are harmless (EDIT: Actually, I'm not sure. I misseed the su part.), but this method avoids having to open the terminal. Also, you should **never** use sudo for graphical programs; use gksudo instead.

---

### Post by Ecthelion on 2006-11-04
>  Also, you should never use sudo for graphical programs; use gksudo instead.

Didn't know that. Why is it? I never used anything else than sudo

---

### Post by ewl1217 on 2006-11-04
I've heard that using sudo for graphical programs can cause errors (something to do with logging out, but I'm not really sure).

---

### Post by heathen on 2006-11-04
his sig says he's running 6.10... didnt i hear something about synaptic being removed from that version?   or am I off in my own world again?

---

### Post by CatKiller on 2006-11-04
> **Ecthelion said:**
> Didn't know that. Why is it? I never used anything else than sudo

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Personally, I'd wager the OP has removed himself from the admin group.

---

### Post by BWF89 on 2006-11-05
I did gksudo synaptic, put in my password, and got this

[I]Failed to run synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/I]

---

### Post by BWF89 on 2006-11-07
I was getting [some other things]("http://ubuntuforums.org/showthread.php?p=1729503") worked out in another thread and when I was done Synaptic is back in my menu again. But whenever I click it my mouse turns to the waiting picture and than nothing comes up. I checked the address where it leads to (gsku/usr/sbin/synaptic) and it's leading to the right file, but for some reason it won't come up.

---

