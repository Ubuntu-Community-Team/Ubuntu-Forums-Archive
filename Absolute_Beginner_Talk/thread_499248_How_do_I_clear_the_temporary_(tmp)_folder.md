---
title: "How do I clear the temporary (tmp) folder?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-07-12
My Ubuntu guide book has the following instructions for clearing the temporary folder, which involves changing to run level 1 (to prevent from clearing files that are still in use):

sudo killall gdm
[log in with username and password]
sudo init 1
rm -rf /tmp/*
rm -rf /tmp/.*
reboot

But after I enter the killall command, I can't use my mouse and the system doesn't respond because (I assume), I have stopped all services.

So do I have to manually shut the system down and reboot after the "killall" command, and then enter my username and password, then continue with the rest of the commands?

Or is there a better way to delete the files in the folder?

---

### Post by bradleyd on 2007-07-12
killall gdm is suppose to stop gdm daemon, which should in turn bring you to a command prompt. From that terminal you can then init 1. If that does not work try ctr-alt-F1. Then from there:
```
sudo init 1
rm -rf /tmp/*
rm -rf /tmp/.*
reboot
```
Let me know if that works.
Brad

---

### Post by black_ice on 2007-07-12
** [COLOR="Red"] you can make abash script and load it in acron job to performed automatically [/COLOR]**

---

### Post by Outrunner on 2007-07-12
Use

```
sudo /etc/init.d/gdm stop
```

instead of 
```
sudo killall gdm

sudo init 1
```

---

### Post by F_r_e_d on 2007-07-12
Brad -- OK I will try this tonight or tomorrow.  All I know is that when I entered the "killall" command I was not able to get anytihing to work, and I didn't see another terminal pop up.  I had to shut down manually and restart.

---

### Post by bradleyd on 2007-07-12
you should not see a terminal popup. The screen should go black(NO gui) and thee should be a prompt there to login.

---

### Post by F_r_e_d on 2007-07-12
Brad,

Yes!  My screen did go black after I manually logged out and restarted.  Then I entered the remaining commands.  Does that mean I probably did it correctly?

---

### Post by bradleyd on 2007-07-12
if you are in your xwindow environment(i.e. gnome or kde) and you type ```
killall gdm
``` from a command line or ```
sudo invoke-rc.d gdm stop
``` it should go to a black screen with a login prompt. Is this what happened to you?

---

### Post by F_r_e_d on 2007-07-12
Brad -- No, it did not go black right after I typed the killall command from a terminal command line.  Everythihng was still there with a white screen in the backgrouns.

I had to do a manual shutdown and reboot to get the black screen and I thought I messed up my whole system (really scared me!).  I'll try it again tonight.  Maybe I didn't wait long enough after the killall command.

---

### Post by pistcivet on 2007-07-12
I'm curious as to why anyone would need to do this.
Since the /tmp directory is cleared automatically at reboot.
(If you rarely/never reboot, I assume there's a cron job already running that will do it for you)

Right now, my /tmp folder contains 28 items totaling 25.2 KB.
I've seen large ISO files in /tmp after copying a CD (for example)
I've never deleted them, they just get deleted at reboot.

What am I missing? :confused:

---

### Post by Genecks on 2007-08-16
> **pistcivet said:**
> I'm curious as to why anyone would need to do this.
Since the /tmp directory is cleared automatically at reboot.
(If you rarely/never reboot, I assume there's a cron job already running that will do it for you)

Right now, my /tmp folder contains 28 items totaling 25.2 KB.
I've seen large ISO files in /tmp after copying a CD (for example)
I've never deleted them, they just get deleted at reboot.

What am I missing? :confused:

My /tmp folder is not being cleared at reboot. Otherwise, I wouldn't be looking at this thread. I did, however, put /tmp on a seperate partition.

---

### Post by Alchera on 2008-01-22
[How to clean /tmp/ folder contents on shutdown]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_clean_.2Ftmp.2F_folder_contents_on_shutdown")

---

### Post by jsast21 on 2008-04-03
I had the same problem:   my /tmp folder filled up.  Should it be emptying out each time I shut down? Because I noticed that it was not. And I did edit the sysklogd file (followed the link that Alchera (thanks btw) recommended below). I rebooted again and noticed that there was still stuff in the folder. Can I just safely delete everything in that folder to free up space? and what other things could I try to get that to happen each time I shut down?

Thanks.

jsast21.

---

