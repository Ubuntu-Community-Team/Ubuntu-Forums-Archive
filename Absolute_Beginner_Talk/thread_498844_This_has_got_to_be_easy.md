---
title: "This has got to be easy"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-07-11
I dont know if I was asking it right.

I need to know how to do this 

"if this the apt-get code does not work than search for XGL in Synaptic"

Its the first step in this guide 

[http://ubuntuforums.org/showthread.php?t=457640](http://ubuntuforums.org/showthread.php?t=457640)

---

### Post by Nekiruhs on 2007-07-11
> **FNDII said:**
> I dont know if I was asking it right.

I need to know how to do this 

"if this the apt-get code does not work than search for XGL in Synaptic"

Its the first step in this guide 

[http://ubuntuforums.org/showthread.php?t=457640](http://ubuntuforums.org/showthread.php?t=457640)

Enter the command in the terminal (Applications > Accessories > Terminal). If that doesn't work, open synaptic package manager (System > Administration > Synaptic Package Manager) and search for XGL.

---

### Post by Immolatus on 2007-07-11
There's no harm in trying xgl from synaptic. If it doesn't work just uninstall it. the worst thing that will happen is the 3D effects just wont run. You will also find aiglx in there (different version of the same thing), you can try that if xgl doesn't work.
Also try beryl instead of compiz.

---

### Post by FNDII on 2007-07-11
Ok i did the search and found the pkg. It wasn't install so i installed it and two other dkgs that it was were dependent.

Now the guide wants me to file in a blank file?
I dont see a blank file anywhere.

---

### Post by Nekiruhs on 2007-07-11
> **FNDII said:**
> Ok i did the search and found the pkg. It wasn't install so i installed it and two other dkgs that it was were dependent.

Now the guide wants me to file in a blank file?
I dont see a blank file anywhere.
Just make the file. Run the commands he tells you.

---

### Post by FNDII on 2007-07-11
ok i made the 2 files now i have to "Log out and hit sessions and select GNOME+XGL"

The sessions option under preference? I don't see a GNOME+XGL. How do you log out and hit sessions?

---

### Post by Nekiruhs on 2007-07-11
> **FNDII said:**
> ok i made the 2 files now i have to "Log out and hit sessions and select GNOME+XGL"

The sessions option under preference? I don't see a GNOME+XGL. How do you log out and hit sessions?
Do the ENTIRE guide. The rest makes it so you have that option.

---

### Post by Seisen on 2007-07-11
Go to System>Quit and then select log out. When you logon screen shows up there should be an option to that says "Session" there you can pick Gnome+XGL.

---

### Post by picpak on 2007-07-11
Ahh, don't log out yet! If you check the guide again, you'll notice that every instance of :[color=black]p[/color] has been replaced with a smiley. So in that case, /usr/local/bin/startxgl.sh should read this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session
```

hope that helps!

---

### Post by FNDII on 2007-07-11
if i cut and paste it shows up correct i think

It is loaded up, the reason I didn't see it before is my log on screen is all messed up and out of resolution.

I also just tried booting up wow and i could barely log oonit was so choppy. do i need to reinstall it?

---

