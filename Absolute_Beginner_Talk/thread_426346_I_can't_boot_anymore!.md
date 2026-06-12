---
title: "I can't boot anymore!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by reedfamily on 2007-04-28
I am a complete noob about ubuntu. I tried repairing some sound issues and I apparently messed something up. when I try booting up I end up in a terminal like screen where I can enter my username and pw and then I don't know what to do next. I cannot seem to make it into my desktop. Is there a way to repair stuff I did this morning? I am using the live cd to even get online and find some help. Thanks in advance for help.

---

### Post by taurus on 2007-04-28
Reconfigure your X again after you log in with your username and password.

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by reedfamily on 2007-04-28
did that and wen't through all the steps that it prompted but it still doesn't let me get to my desktop. it still takes me to that terminal like screen. Is there a way to repair whatever I did this morning without losing all my files? I'm sooo lost!

---

### Post by taurus on 2007-04-28
What is the error message when you run startx from a prompt?

---

### Post by reedfamily on 2007-04-28
when i just put "startx" in the prompt I get a grey screen with nothing else. No where to type or anything. Is that even what you meant?

---

### Post by bobplano on 2007-04-28
what about sudo X?

---

### Post by fglrsux on 2007-04-28
try sudo gdm

---

### Post by reedfamily on 2007-04-28
both sudo x and sudo gdm caused similar responses "command not found" 

any other suggestions on how I can repair this and get to my desktop????
txs again.

---

### Post by taurus on 2007-04-28
```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by reedfamily on 2007-04-28
I tried that and after it tried doing something it said something to the effect of "no cadidate version for ubuntu-desktop" and the same things for GDE.

---

### Post by taurus on 2007-04-28
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by reedfamily on 2007-04-28
i tried that and it said no such file or directory :(

I'm soooo frustrated with this :(

---

### Post by taurus on 2007-04-28
```
ls -la /etc/apt
```

---

### Post by reedfamily on 2007-04-28
this is what I got, and bear with me cuz I had to write it all out and then type it in here when I rebooted with cd so I can get on here...

ls: -: no such file or directory
ls: la: no such file or directory
/etc/apt: apt. conf secrng.gb
sources.list.d trusted.gpg
apt.conf.d sources.list_backup
trustb.gph trust.gpg

still no luck

---

### Post by taurus on 2007-04-28
Try

```
sudo cp /etc/apt/sources.list_backup  /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by reedfamily on 2007-04-28
thank you so much Taurus!!!!
after entering that I was able to do sudo aptitude install ubuntu-desktop gdm
and am now up and running. 

:) :KS

---

### Post by taurus on 2007-04-28
See.  There is no need to get frustrated.  Whatever it was, it could be fixed.  Might take a little time but it is doable.

---

