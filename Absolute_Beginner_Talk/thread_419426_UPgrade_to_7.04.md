---
title: "UPgrade to 7.04"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-23
If I enter $ gksu "update-manager -c" into Terminal, it gives me bash: $: command not found . If I enter gksu, it gives me "run program", where if I put in "update-manager -c" it doesn't give me the option to upgrade to 7.04 . If I just start update manager, same story.

How can I get it to give me the upgrade option?

I have a full install CD of 7.04. What happens if I just install it over 6.10 - or can I do that at all?

---

### Post by RealG187 on 2007-04-23
uh  yeah, i installed edgy via an alternate cd, then got kde [see my sig].

if i want feisty do i use a ubuntu cd or one for kubuntu? do i need alternate again.

i mainly use my kde....

---

### Post by siciliancasanova on 2007-04-23
What happens if you install over 6.10?  :)  Then it is no longer there.  That's the easiest way to do things.  Unless of course you have files or something that you don't want deleted.  Everything has to be a catch 22 it seems.

---

### Post by Tux Aubrey on 2007-04-23
In reply to RogerDavis:

1. Now that Feisty has been released you should be able to just start update manager from your Admin menu and it should have the 7.04 upgrade option (above the window).  

2. If not, try the terminal option again but don't type the "$" sign - just gksu "update-manager -c"

3. If you put the disk into your CD drive while still logged into edgy, it will give the option to try an upgrade from the CD.  I've never done this myself.

4. And yes, a clean instal from the booted LiveCDl will overwrite your edgy install - including your /home unless you have it on a separate partition and elect to keep it.

---

### Post by RealG187 on 2007-04-23
Do I use a ubuntu CD or a Kubuntu CD, I used a normal ubuntu CD originally but then installed kde via: 

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

