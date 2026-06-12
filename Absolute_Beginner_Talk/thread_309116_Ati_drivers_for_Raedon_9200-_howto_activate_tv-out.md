---
title: "Ati drivers for Raedon 9200- howto activate tv-out ?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Dr.Thompson on 2006-11-29
Hi all!
I startet using Ubuntu a week ago and Im getting closer and closer to think this was a very vise desicion. But I have one problem before my "Command center" are up to date.

I need help to locate my ati drivers, I dont know how to activate my Tv-Out, very frustating](*,) . Have missed 4 episodes of my favor series. Including 2 episodes of Southpark :(:( So, Is there anyone outthere who could give me an idiot-proof guide to get the tv-out activatet so I can see South Park on my super-sweet plasma again. 

Mahalo.

---

### Post by Dr.Thompson on 2006-11-29
kristian@kristian-desktop:~$ /etc/X11/xorg.conf 
bash: /etc/X11/xorg.conf: Permission denied
kristian@kristian-desktop:~$ 

hmmmmmm...... arghh.. hmmm

---

### Post by Scorpuk on 2006-11-29
You might want to follow this example: [http://www.ubuntuforums.org/showthread.php?t=209024]("http://www.ubuntuforums.org/showthread.php?t=209024")


To edit the xorg.conf file you need to type this command at the terminal:

```
sudo nano /etc/X11/xorg.conf 
```

This will open the file in a simple text editor within the terminal. You will be asked for your password. As you type it in nothing will be shown on screen for security purposes but it is being entered. Just type it in and hit return.

---

### Post by Scorpuk on 2006-11-29
On a side note, what make and model is your plasma screen?

Some come with computer connectors built in and this would save you the hassle of messing around with the settings to get the tv-out to work.

---

### Post by Dr.Thompson on 2006-11-29
Hmm, I have these connectors, its A "Elfunk 43", only two months old. But on the other hand, I dont have more than one connector on the graphic-card.

---

