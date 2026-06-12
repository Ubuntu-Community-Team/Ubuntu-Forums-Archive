---
title: "GUI disappears... can log in..."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-11-24
My GUI has disappeared, but I can log in, in text form, on a black screen.  The folder system is accessible remotely, so no files lost.  But how do I get the GUI back?  

I get the message:

'no resume image, doing normal boot'

Thanks in advance.

---

### Post by Ub1476 on 2007-11-24
Try to reconfigure X:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by getmeoutofhere on 2007-11-24
Thanks.

I tried that, but I hadn't a clue how to answer the various questions.  I guessed, but it didn't help.  If it can be set up automatically on installation, when can't it be set up automatically now?

I think problems like I am having show why Linux is going to find it very difficult to become mainstream!

---

### Post by Partyboi2 on 2007-11-24
you could try:
```
sudo startx
```
also have a look in the xorg log for errors
```
less /var/log/Xorg.0.log
```

---

### Post by philinux on 2007-11-24
what exactly were you doing prior to the gui vanishing?

---

### Post by getmeoutofhere on 2007-11-24
Good point.  I was trying to get my USB sound card to work.  I read somehwhere that by taking it off and putting it back again that might fix the problem.  Don't ask me exactly what I did... but it seemed that my amateur attempts to fix a medium-size problem created a massive problem.

---

### Post by philinux on 2007-11-24
When you say taking it off then putting it back - do you mean physically or by editing some files.

If the later what did you edit. I always make a note in a notepad of changes I make, It's good practise.

---

### Post by getmeoutofhere on 2007-11-24
I know it's good practice... but I didn't!

I uninstalled and reinstalled.

Having said that, the computer was showing signs of stress beforehand... the USB soundcard suddenly not working.

At least I'd set up the facilities for remote access before the GUI went down.

I'm pretty much resigned to a re-install, though my concern is about what if it happens again.  If I can't fix it, then the problem will keep recurring.

---

### Post by philinux on 2007-11-24
I'd try this again, cut and paste into command line.

sudo dpkg-reconfigure -phigh xserver-xorg

Now with most of the options it's pretty safe to say "yes" as the system is detecting your hardware etc.

Some screens need you to press esc to get out of as they're messages.

Have a go you got nothing to loose.

If all else fails move home to a separate partition. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

and reinstall.

---

### Post by getmeoutofhere on 2007-11-24
philinux,

Thanks.  I'll try that when I've finished backing everything up.  It's going to be another three or four hours!

---

### Post by philinux on 2007-11-24
Good idea, I move my home a while back and its a doddle to reinstall as all your settings are preserved. Just make sure if you do that you use exactly the same name for your desktop userid and password as you have now.

Also this is good to enable application reinstall. 
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

I also took a copy of my sources.list as well.

---

