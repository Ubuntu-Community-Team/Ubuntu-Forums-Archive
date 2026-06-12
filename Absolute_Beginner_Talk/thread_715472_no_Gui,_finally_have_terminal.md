---
title: "no Gui, finally have terminal"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by raphenry on 2008-03-04
I have a AMD with a Gigabit motherboard, cant really tell you much more about it right now, cause all i have on it is a terminal view.
I tried to start it a couple days ago and it no longer went to the GUI, I have 7.10 on there, thought it was fiesty fawn, but that was 7.06or4 but I upgraded.  How can i do get my gui back?  It was telling me something about x~something already running, but it would just restart, finally it started with the command prompt.

Help

---

### Post by taurus on 2008-03-04
Try to reconfigure your X server again after you've logged in with your username and password.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart it with

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by raphenry on 2008-03-04
> **taurus said:**
> 
Now, restart it with

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

i am told by the pc that /etc/init.d/gdm command not found

---

### Post by glennric on 2008-03-04
Try 
```
sudo apt-get install gdm
```

---

### Post by Ptero-4 on 2008-03-04
A question. Was your GUI y chance a windows-like thing with a K in the start button?
If it was then you need to use ```

sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start

```
to restart your GUI.

---

### Post by raphenry on 2008-03-04
the ubuntu circle was in the bottom corner.

kdm wasnt a good command either, gdm first said that it was not a good command, but when i sudo apt get, it says that it is already installed.

---

### Post by raphenry on 2008-03-04
is there a command i can type to see if something is not working properly??
I am using the 7.10 on the laptop that i type this on, both amd... dont know what to do to get it to work.

---

### Post by raphenry on 2008-03-05
tried to install a new xorg, since it did not seem to like the one i had, that seems to have been a bad idea, now it wont let me get back to the command prompt.  It says check if there is an x server already running when it boots, is there something there that i should know? I will try to get in thru the restore or something.  Also I have a dual boot with xP if that matters.

also dont know it this matters but it says that the guarddog firewall isnt working or installed  but when I sudo apt-get install it shows that it is already installed, but I cant find it.

---

### Post by spiderbatdad on 2008-03-05
It matters if you leave windows hibernating. Make sure to cleanly shut down windows before booting ubuntu

---

### Post by gigaferz on 2008-03-05
typing "startx" ?

---

### Post by raphenry on 2008-03-06
startx seems to be the key, my desktop looks kinda funny...
thanks i will update when i see what happens next [-o<

---

### Post by raphenry on 2008-03-06
okay startx gets me into the gui, but i cant update access the web or anything, when I restarted back to the same, cant load and restart.
something about CHLD... make sure another x is not running... dont know
can't take a screen shot.

any help is good help

thanks guys

---

### Post by gigaferz on 2008-03-06
im just telling you this cause ive been through a lot,(like many around here)

back up,
and 
reinstall
 
   Or provide more information, to see if we could help you google it

what were you doing or tried to do, how did this happen?

I know it looks all "it sstuff" or something but the terminal is actually very friendly ,because is tells you most of the time what is going on, so pay attention when is booting to see what is the problem.

Also if you see the splash screen press alt+f2, (or f1,just try it) to see where the error could be.

---

### Post by raphenry on 2008-03-09
:-?
> **gigaferz said:**
> 
back up,
and 
reinstall
how do i back up thru terminal screen, i never get to the GUI unless i use the startx, and then i have no authority 

   > **gigaferz said:**
> Or provide more information, to see if we could help you google it

what were you doing or tried to do, how did this happen?
I started my computer one morning and i no longer had a GUI, it would just restart.  I mentioned before that it is dual boot with win Xp, wx is always shutdown, so not sure why it tells me that there is another x running when i start from totally shutdown. Lastly i read that it says no listening divice or socket.

> **gigaferz said:**
> I know it looks all "it sstuff" or something but the terminal is actually very friendly ,because is tells you most of the time what is going on, so pay attention when is booting to see what is the problem.  I have pages of info when it boots, one of the pages shows a number repeating like steps, the same number but each boot is a different number, 

> **gigaferz said:**
> Also if you see the splash screen press alt+f2, (or f1,just try it) to see where the error could be.
In terminal, when i hit f1 it beeps, alt+f2 gives me a blank screen.


I do appreciate all of the help, i will try to do a scroll lock and write everything down.

thanks:-?

---

### Post by raphenry on 2008-05-01
okay guess no one had any more suggestions here...
How do i activate my ethernet so I can upgrade to 8.04?  Since I dont have GUI i cant just hit the upgrade manager.  I have terminal window and apt-get upgrade has a lot of failed to fetch http....
any help is greatly appreciated.

Raph

---

