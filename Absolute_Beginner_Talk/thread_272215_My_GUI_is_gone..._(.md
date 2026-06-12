---
title: "My GUI is gone... :("
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Chake99 on 2006-10-05
I was trying to install XGL for the second time from a second howto, and when I rebooted my computer I couldn't get to the ubuntu login screen and got some message about the x-session not working.

I can get to a command line of course (and right now I'm writing this from the live cd).

What command would I use from the command line to get my xorg.conf replaced with a clean untinkered version?

And unfortunately I can't find the howto I had used... although if I could get the gui working again I could check my bookmarks... I hate catch 22's.

So please help. And ty in advance.

---

### Post by james_san on 2006-10-05
the command is `sudo dpkg-reconfigure xserver-xorg`. if you look at the start of the xorg.conf file there is a command similar to that (I think it includes -phigh or something) that will work even better (more automatic detection instead of questions).
Although, if you have already changed your xserver to xgl, then xorg.conf is not your problem...

---

### Post by blendmaster on 2006-10-05
Wow, same problem from the same tutorial at nearly the same times!
I'll have to try that command (right now I'm using my windows partition). By the way, I don't think that tutorial even works.

---

### Post by Chake99 on 2006-10-05
So far no go...

Is there a recover utility for ubuntu that I can use to reinstall my system config while keeping my /home?

---

### Post by james_san on 2006-10-05
Unfortunately not, save from backing up your home directory to another partition (or usb drive).
Before you try that, try deleting the file /etc/gdm/gdm.conf-custom if it exists. That may help, I think it has something to do with which xserver to start. (delete with `sudo rm /etc/gdm/gdm.conf-custom`)

---

### Post by Josey on 2006-10-05
in /etc/gdm/gdm.conf-custom you need to remove the xgl options in [servers]

---

### Post by Chake99 on 2006-10-06
Sounds familiar, I think I also added another category beneath servers...

how what is the command to edit from the command line? I Spose gedit doesn't work until gnome is running...

---

### Post by blendmaster on 2006-10-06
If you're still not in Linux, try using the command startx , it worked for me (I got into a really bad looking GUI, but it's better than nothing).

---

### Post by blendmaster on 2006-10-06
By the way, I really have no clue why that works. I'm really confused by that tutorial.

---

### Post by bulldog on 2006-10-06
> **blendmaster said:**
> Wow, same problem from the same tutorial at nearly the same times!
I'll have to try that command (right now I'm using my windows partition). By the way, I don't think that tutorial even works.


Nope it doesn't anymore.
You need beryl and emerald now a days,try this one. 

[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

How far did you execute the Howto?
Did you set anything in your sessions menu?

---

### Post by Chake99 on 2006-10-06
Thanks but... what is the command to edit a file from the command line when gedit won't work ](*,) ?

---

### Post by bulldog on 2006-10-06
```
sudo nano /etc/X11/xorg.conf
``` should do it.

It works a little different in compare with gedit.

Look at the bottom for your commands.

---

