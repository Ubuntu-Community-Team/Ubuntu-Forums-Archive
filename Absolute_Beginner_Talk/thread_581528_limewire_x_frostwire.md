---
title: "limewire x frostwire"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-19
i downloaded both frostwire and limewire and niether work.  when i start limewire i get a blank screen  that says: "Limewire: Enabling  Open Information Sharing"

[IMG]http://i213.photobucket.com/albums/cc307/kernel-fiesty/Screenshot2.png[/IMG]

frostwire is another story, its installed and when i click on it nothing happens.  just nothing at all.  

ive tried afew fixes taht have worked for others but ive seen no change...

---

### Post by nchase on 2007-10-19
first of all, I'd stay away from limewire unless you have some really good reason for using it.

for frostwire: did you download the .deb package from [http://www.frostwire.com/download/?os=ubuntu](http://www.frostwire.com/download/?os=ubuntu) ?

when you run frostwire in a terminal, what is the output?

---

### Post by jordanmthomas on 2007-10-19
If you are running compiz, try opening a terminal and typing this:
```
export AWT_TOOLKIT=MToolkit
```
and then frostwire (or Limewire) to see if it helps.

Also, what are the fixes you tried?

If it helps, we can tell you how to make it permanent.

---

### Post by loganm10 on 2007-10-19
I use gtk-gnutella, it runs on the same network as limewire/frostwire, but its not java dependant and works very well

its in the repositories

---

### Post by loganm10 on 2007-10-19
I use gtk-gnutella, it runs on the same network as limewire/frostwire, but its not java dependant and works very well

its in the repositories

---

### Post by siralphred on 2007-10-19
install java5-jre from synaptic that should help

---

### Post by loganm10 on 2007-10-19
a

---

### Post by linux-loser on 2007-10-19
i think i found the problem, I running 7.04 fiesty x64 with kubuntu installed but using the gnome gui.  but i dont have java installed.  ive tried to use easy ubuntu to install java but i get this:

"Reading state information...

error: 
E: Package sun-java5-plugin has no installation candidate
error: 
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
EasyUbuntu is finished. You may copy this log for debugging purposes."

not really sure how to install an up to date java...

lol sorry i got too many windows with the same things being covered, i posted here by accident

---

### Post by Officer Dibble on 2007-10-19
I've just installed gtk-gnutella and it runs as nicely as any of its contemporaries but without a hitch.

Thanks for the tip Logman10. :)

---

### Post by Frak on 2007-10-19
Click this link below to install needed programs.

[apt:ubuntu-restricted-extras]("apt:ubuntu-restricted-extras")

---

### Post by linux-loser on 2007-10-19
link doesnt work for me

if that link is for gutsy will it work in feisty?

---

### Post by Frak on 2007-10-19
> **linux-loser said:**
> link doesnt work for me

if that link is for gutsy will it work in feisty?
If you are using Feisty, you need to install it manually, by going to synaptic, or launching the terminal in Applications->Accessories->Terminal
```
sudo aptitude install ubuntu-restricted-extras
```

---

