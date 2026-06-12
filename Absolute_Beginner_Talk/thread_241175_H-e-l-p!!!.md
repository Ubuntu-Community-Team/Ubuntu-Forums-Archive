---
title: "H-e-l-p!!!"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-08-21
I recently installed Kubuntu and all has been going fairly well except for a problem with the screensaver.  I was told that it was due to a bug in the KDE 3.5.3 and to upgrade to KDE 3.5.4.  So last night I found a HOW TO on upgrading the KDE and it seemed to work OK until it began to install the updates, where it found some broken packages and stopped installing.  So I did the upgrade again and this time it seemed to install everything but at the end it just sat on "Done 100%" and I couldn't do anything else.  I tried to close the window but a message apprared saying that Adept was not responding.  Eventually I Logged Off and rebooted.  Now I can't get ANYTHING AT ALL!  It just says "Signal out of range"  So, I rebooted using "Recovery" but after loading it wants an input from me.  I typed in my password but that was not it.  

So, what can I do?  If I use Recovery option what do I put after the #

Of course the other option is to do a full install again but I would rather save everthing I have already installed.

Can anyone help please.

Russty.

---

### Post by richardward101 on 2006-08-21
Try the following:
Boot up until you get the signal error, wait a few seconds and press Ctrl+Alt+F1 to get a terminal. login and type```
 sudo apt-get dist-upgrade
```
see what happens. If it says somethings wrong and recommends a course of action then follow it (it'll tell to to run the command with certain options.  otherwise now restart the computer and see what happens.

---

### Post by Russty of Oz on 2006-08-22
I tried that but Ctrl + Alt + F1 does nothing.

---

### Post by Russty of Oz on 2006-08-22
Just thought I would bring my post back up the list so it doesn't get lost in case anyone knows the answer.

---

### Post by deadgobby on 2006-08-22
Is it asking you to run fsck at boot up? 
Gobby

---

### Post by Russty of Oz on 2006-08-22
> **deadgobby said:**
> Is it asking you to run fsck at boot up? 
Gobby

No, it just says Signal out of range.

---

### Post by nalmeth on 2006-08-22
> I tried that but Ctrl + Alt + F1 does nothing. Boot into recovery mode like you did before, and follow the poster's advice. You won't need sudo since you will be root.

apt-get update
apt-get dist-upgrade

---

### Post by deadgobby on 2006-08-22
> **nalmeth said:**
> Boot into recovery mode like you did before, and follow the poster's advice. You won't need sudo since you will be root.

apt-get update
apt-get dist-upgrade

So at the # prompt type in fsck 
It should fix any orphan stuff and you may be ask a yes or no questions. Say y for yes. After it does it mojo. Do the following above.
Gobby

---

### Post by Russty of Oz on 2006-08-22
> **deadgobby said:**
> So at the # prompt type in fsck 
It should fix any orphan stuff and you may be ask a yes or no questions. Say y for yes. After it does it mojo. Do the following above.
Gobby

Well, I did that and all it said then was 
  **Partition /dev/hda4 is mounted with write permissions, cannot check it**

Now what?

Russty

---

### Post by Russty of Oz on 2006-08-22
Hi again!

I have decided to do a complete reinstall and see how that goes.

Wish me luck!

Russty :)

---

### Post by deadgobby on 2006-08-22
i google your error message. Would this help?


[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Gobby

---

### Post by deadgobby on 2006-08-22
Good luck! 
Tried to help, but fresh install never really hurt.

---

### Post by Russty of Oz on 2006-08-22
> **deadgobby said:**
> Good luck! 
Tried to help, but fresh install never really hurt.

I do appreciate your help, I just decided a fresh install might be easier.  I have hit another problem though, and that is with the upgade to KDE 3.5.4   I don't seem to be able to edit my /etc/apt/sources.list   Kate won't let me edit it. Oh well, I will keep trying and search the forum before I ask for further help.  The thing is, I feel lost without my Kubuntu!

Russty

---

### Post by Russty of Oz on 2006-08-22
Well, now I have a REAL problem!

Yesterday I reinstalled Kubuntu 4 times and each time it works at first, but after doing the updates, when it reboots I just get the "Signal out of range" error.  

Everytime I installed it I checked the display settings and for some reason they are set at 75Hz but it seems that Kubuntu only likes 60Hz.  I tried changing it but it wont stay at 60Hz and it wont change the screen resolution either!  I clicked the administrator button but it just wont change the settings.

Does anyone know what I can do?  

Russty.

---

### Post by Russty of Oz on 2006-08-22
I think I have worked it out.

This time (my 5th install!) I ran the live CD and changed the resolution to 1024X756 and 60Hz **BEFORE** installing. So far it seems to be working well.

Fingers crossed!!

Russty.

---

### Post by Russty of Oz on 2006-08-23
**IT WORKED!**:D 

So I just had to set my resolution BEFORE installing Kubuntu!  I feel so much better now I have it back.  

Now if only I could get the screensavers to work!  Before it wouldn't do anything about the screensaver, but now at least the screen goes blank after the prescribed time.  I guess that is "progress".  :roll: 

Russty.

---

### Post by deadgobby on 2006-08-23
MMM what type of vid card to you have?

---

### Post by Russty of Oz on 2006-08-23
> **deadgobby said:**
> MMM what type of vid card to you have?

NVidia FX 5200.

---

### Post by Russty of Oz on 2006-08-23
> **deadgobby said:**
> MMM what type of vid card to you have?

NVidia FX 5200.  I installed the drivers through Automatix.

Russty

---

### Post by deadgobby on 2006-08-23
Ok now we are getting some where. Sorry to say I do not that type of vid card or run Kubie. At least there is people how can solve this for you. Perhaps start a new post of the type of vid card you have and the problems you are haven.
Gobby

---

### Post by Russty of Oz on 2006-08-23
Hmmm, I don't know if I have just installed something or whether it just wants to make a fool out of me, but the screensaver is now working!!  AT LAST! 

Thanks for the help along the way.

Russty.

---

