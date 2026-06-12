---
title: "How do you shutdown from the other desktop environment?"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by aysiu on 2006-03-09
I hope Poofyhairyguy doesn't scold me for posting in the Absolute Beginner section. I wasn't sure whether this qualified as a Kubuntu question or a Ubuntu question, and I didn't want to double-post.

So, if I have KDM installed, I can shut down from KDE and log out from Gnome.

If I have GDM installed, I can shut down from Gnome and log out from KDE.

And, yes, I do shut down--I know some people *love* their "up time."

I haven't been able to "decide" on a desktop environment. Right now I have KDE, Gnome, and XFCE, and I love them all. I would also love to be able to shut down from all three. XFCE can shut down from GDM or KDM.

Is there a way that I can tweak KDM to let me shut down from Gnome or tweak GDM to let me shut down from KDE?

P.S. Would WDM solve my problems? And does it always look [this ugly](http://distro.ibiblio.org/pub/linux/distributions/vectorlinux/development/vectelopment-5.0/tmp/screenshot/vl5-wdm.png)?

---

### Post by Xian on 2006-03-09
The only Gnome environment that I've seen which allowed shutdowns from the panel menu while using KDM was Dropline, and I'm pretty sure they used PAM in order to gain this functionality. I really don't have an answer for you short of this, but you can try some, all, or a variety of the following:

$ sudo chmod +s /sbin/halt 
$ sudo chmod +s /sbin/shutdown

$ sudo touch /var/run/console/username

Make a symlink for shutdown and halt into the /usr/bin directory

---

### Post by aysiu on 2006-03-09
Thanks, Xian. Could those be potentially dangerous somehow...?

---

### Post by Xian on 2006-03-10
Well, I'd check your permissions on those halt and shudown files beforehand so you can reset if needed. The others are easily reversible by simple removal. 

$ sudo rm -f /var/run/console/username

And so forth....

This is all just guesswork on my part anyway and probably will have no effect. I'm mainly thinking along the lines of getting some additional functionality in Gnome while using KDM. If you swap those two (KDE using GDM) then I really have no suggestions there (I don't use KDE at all).

---

### Post by aysiu on 2006-03-10
Hm.

Maybe I'll try just creating a launcher (to be run in terminal) with the command ```
sudo shutdown -h now
``` What do you think?

---

### Post by aysiu on 2006-03-10
It worked! It worked!

I didn't follow your exact suggestion, but you got me thinking, so thanks.

I created a launcher to be "Run in Terminal" for the command ```
sudo shutdown -h now
``` and now I can click on that launcher and shut down without having to log out first.

It also means I can switch between KDE and Gnome at whim. Thanks again.

---

### Post by byen on 2006-03-10
AH! I wish I saw your thread a little early! Yes that works..that is what I have been doing. It still asks for a password but sure beats the hell out of logging out!

An advise: I got a little lazy typing in the password so I got a little cocky and tried editing the "/etc/sudoers" file and adding the "shudown -h" command to my user name. Oh Boy! my sudoers list got all crazy and gave me an error saying that there was an invalid entry. So Please do not try it! If you have tried it and survived...let me know how to did that!

Goodluck!

---

### Post by aysiu on 2006-03-10
You know, I have a separate test computer. I'm going to play around with the /etc/sudoers file on that and see if I can't get it to work. I'll report back if it works.

---

### Post by kaamos on 2006-03-10
just create a /usr/local/bin/shutdownnow with
```
#!/bin/bash
#

shutdown -h now
```
and use visudo to add
```
username ALL = NOPASSWD: /usr/local/bin/shutdownnow
```
Then change the launcher to "sudo shutdownnow"

---

### Post by aysiu on 2006-03-10
Thanks, kaamos. I think I'll try that later.
I have a similar hack for shutting down in XFCE without a password.

---

### Post by aysiu on 2006-03-11
I tried it out.

First I had to make the file executable.

Even after that, though, it didn't work because the shutdown command still requires root or sudo permissions, even if no *password* is required.

I had to change the line to say ```
sudo shutdown -h now
``` instead of ```
shutdown -h now
```

I still don't recommend this yet. I'll play around with my experimental computer for a few more days. If I don't notice any adverse effects, I'll give this method my full endorsement.

---

### Post by aysiu on 2006-03-13
It appears to work! Go for it, people. Go for it.

---

### Post by xtacocorex on 2006-03-13
I read through this thread and got confused at the end as to what you were trying to do, but I re-read the first post and it made sense.

As for the WDM picture, I think it looks bland.

I might have to try this out since I switch between Fluxbox and KDE with XFCE when I get bored. 

Do you know of a way to get KDM to pick a different default WM based upon ACPI status? I posted this some time ago in the forums, but I think it's way too technical, but since you brought this up I figured I'd ask.

---

### Post by aysiu on 2006-03-13
What does ACPI status mean?

**Edit**: By the way, you don't need to make a new bash script. You can just add this to your /etc/sudoers file: ```
ALL ALL = NOPASSWD: /usr/sbin/shutdown
``` and make the command ```
sudo shutdown -h now
``` Of course, only people who have *sudo* permissions will be able to use the command.

---

