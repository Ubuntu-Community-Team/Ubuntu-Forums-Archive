---
title: "metacity config tool error"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Unreal223linux on 2007-09-10
I'm trying to edit my gnome themes but I keep getting an error about "metacity".
I think its because I started out with linux mint xfce edition. I did this because it supported my wifi card MUCH better than any other linux distro. Anyway I hated xfce so I installed gnome and now I'm in linux bliss. I just want to customize things to my liking.

Here is the error:
[[IMG]http://img514.imageshack.us/img514/8636/screenshotzp2.th.png[/IMG]](http://img514.imageshack.us/my.php?image=screenshotzp2.png)

I'm sure this is probably something dumb like a file association or something but I dont know how to fix it in ubuntu. :(

---

### Post by Maestro23 on 2007-09-10
Check this thread, might put you on the right track.

[http://ubuntuforums.org/showthread.php?t=103790&highlight=no+registered+configuration+tool](http://ubuntuforums.org/showthread.php?t=103790&highlight=no+registered+configuration+tool)

---

### Post by Unreal223linux on 2007-09-11
Metacity was already running and restarting it didnt help. :(

---

### Post by Unreal223linux on 2007-09-11
So no one has seen this error before? :(

---

### Post by vambo on 2007-09-11
How about

```
metacity --replace
```

---

### Post by asmoore82 on 2007-09-11
> **Unreal223linux said:**
> I'm trying to edit my gnome themes but I keep getting an error about "metacity".
I think its because I started out with linux mint xfce edition. I did this because it supported my wifi card MUCH better than any other linux distro. Anyway I hated xfce so I installed gnome and now I'm in linux bliss. I just want to customize things to my liking.

Here is the error:
[[IMG]http://img514.imageshack.us/img514/8636/screenshotzp2.th.png[/IMG]](http://img514.imageshack.us/my.php?image=screenshotzp2.png)

I'm sure this is probably something dumb like a file association or something but I dont know how to fix it in ubuntu. :(

My **guess** is that you installed Gnome via apt/Synaptic without using the **metapackage** to
ensure all depencies and defaults get loaded; try this and see if it ties up any loose ends ...
```
~$ sudo apt-get update && sudo apt-get install ubuntu-desktop
```

P.S. you may need to adjust for LinuxMint ?maybe search for "desktop" in Synaptic?

---

### Post by Unreal223linux on 2007-09-11
I used sudo apt-get install ubuntu-desktop. 
Was there another method I was supposed to use? 

If I run that command what is going to happen? Sorry to be a pain but I'm so excited to finally have this working well and I have it set up the way I want it pretty much. This is just a minor annoyance.

I tried that command vambo posted and it didnt work. :(

---

### Post by Unreal223linux on 2007-09-11
Ok I tried that command and got an error saying bash...
But the good news is that I fixed this myself. I just reinstalled metacity using synaptics reinstall options.

---

### Post by asmoore82 on 2007-09-12
cancelled.

---

