---
title: "Help please!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by H_91 on 2007-09-12
When I open **Synaptic Package Manager**, this message pops up...
[SIZE="1"][I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I][/SIZE]

How do I correct it? :(



+I have another problem where I can't install any .deb packages because it says that I should close other applications such as aptitude, synaptic, or update manager.. But they are closed. 
What should I do?  How do I close them? Just to make sure they are. *???*

---

### Post by rsambuca on 2007-09-12
Make sure all of your programs are closed first.  Then open a terminal from the top menu bar "Applications  -> Accessories -> Terminal"

Then enter ```
sudo dpkg --configure -a
```

---

### Post by CaptainInsaneO on 2007-09-12
Go into terminal and type

```
dpkg --configure -a
```

The computer is already telling you how to fix it.

---

### Post by H_91 on 2007-09-12
Yeah, I do know that. Its just I tried it several times before, but same problem would occur. Its working right now, but in the middle of the installation, it gets stuck. It has happened before.

---

### Post by kellemes on 2007-09-12
> **H_91 said:**
> 
+I have another problem where I can't install any .deb packages because it says that I should close other applications such as aptitude, synaptic, or update manager.. But they are closed. 
What should I do?  How do I close them? Just to make sure they are. *???*

It's probably the freeking updatemanager running in the background or something.. close it, kill it!

---

### Post by H_91 on 2007-09-12
> **kellemes said:**
> It's probably the freeking updatemanager running in the background or something.. close it, kill it!

Haha.. That was the first thing I did. :)

---

### Post by H_91 on 2007-09-12
The installation keeps getting stuck! =[ 
Don't know what to do..

---

### Post by por100pre1 on 2007-09-12
Try this:

```
sudo apt-get install -f
```

---

### Post by rsambuca on 2007-09-12
What do you mean 'stuck'?  What exactly does the terminal say?

---

### Post by H_91 on 2007-09-12
[IMG]http://i7.photobucket.com/albums/y274/ahgharib/Screenshot.png[/IMG]

Just stops in the process of installing..

---

### Post by rsambuca on 2007-09-12
But what does it say from the "sudo dpkg --configure -a" command?  The picture you have shown is not the terminal.

---

### Post by rsambuca on 2007-09-12
Also, if you haven't installed java before, you will have to agree to the licensing terms before it can continue.

---

### Post by H_91 on 2007-09-12
Yeah, I know that. 

This is what it says..
```
dpkg: status database area is locked by another process
```

---

### Post by mlentink on 2007-09-12
Isn't Java in Add/Remove (or Synaptic)?

---

### Post by rsambuca on 2007-09-12
> **H_91 said:**
> Yeah, I know that. 

This is what it says..
```
dpkg: status database area is locked by another process
```
You have to fix the dpkg error first.  It will not help if you keep trying to use synaptic without fixing the problem.  You must make sure all processes are closed and then run the dpkg command from the terminal.  Reboot if you have to.  Then run the dpkg.

---

### Post by H_91 on 2007-09-13
Solved! Thanks a lot guys! :)

---

