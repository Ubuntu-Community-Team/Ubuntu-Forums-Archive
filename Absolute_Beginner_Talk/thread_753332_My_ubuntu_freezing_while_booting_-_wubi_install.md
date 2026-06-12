---
title: "My ubuntu freezing while booting - wubi install"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Atro on 2008-04-12
Hi guys
Im using ubuntu with wubi install because I really cant manage the dual booting process.
I updated ubuntu yesterday, I realized one of updates was lunix-gereric blah blah -16, I updated, all fine, but when I was trying to boot into ubuntu today, it freezied while showing booting progress. about 15% in.
So i restarted, pressed ESC and chose linux-gereric blah blah -15, and its booting fine now. Does this mean everytime I want to update my wubi ubuntu, my system will crash? same thing happed while i was trying to update ubuntu 7.04 to 7.10
does anyone have a general solution to overcome this problem?

---

### Post by Crafty Kisses on 2008-04-12
Could you move your mouse cursor? Possibly could have been a one time thing, has this happened before?

---

### Post by Atro on 2008-04-12
> **Codename said:**
> Could you move your mouse cursor? Possibly could have been a one time thing, has this happened before?

waited for 5 minutes nothing happened, didnt see a mouse cursor in booting progress screen. It doesnt freeze in log in window, one step before that

---

### Post by Crafty Kisses on 2008-04-12
> **Atro said:**
> waited for 5 minutes nothing happened, didnt see a mouse cursor in booting progress screen. It doesnt freeze in log in window, one step before that

Did you try doing the following when it froze?
```
Ctrl+Alt+Backspace
```
That should take you back to the login screen, and see if you can log back in.

---

### Post by Atro on 2008-04-12
Thanks will try it now

---

### Post by hyper_ch on 2008-04-12
what can't you manage with dual-booting?

---

### Post by Crafty Kisses on 2008-04-12
> **hyper_ch said:**
> what can't you manage with dual-booting?

Yeah, I was thinking about that. Are you scared you're going to mess up Windows?

---

### Post by Atro on 2008-04-12
Hey I tried this ctrl+alt+backspace thingy, after pressing for 5 or 6 times, it loaded suddently into some DOS like enviroment, and said it can load my Xserver, my graphical enviroment due to some internal error.

About dual booting, I tried it once, worked fine, but then my ubuntu crashed for some reason and I lost my windows too. I had to take my hard disk to a friend to get my important files out and reformat the whole thing. so kinda scared of it now

---

### Post by Crafty Kisses on 2008-04-12
When that happens try:
```
startx
```
You should have only really tried that once, but oh well.

For the partitioning problem, why don't you just get another HDD then install Ubuntu on there. So your Windows HDD isn't even touched.

---

### Post by stuart brogan on 2008-04-12
hmm, I tried the wubi install and I still had to boot into Linux. also truecrypt wouldn't support encypting the harddrive of the winblows OS because of this. Correct me if I am wrong but it is still dual booting, just that your using the windows boot loader not grub.

I found it much more preferable to just relagate windows to about 5GB and put Hardy on the rest, this gave me more options at boot time, as well as solved some other issues. (Having the windows partition, I am told allows my sprint evdo card to be provisioned,)

during all my trials I did run into the hang this person is talking about after installing, uninstalling, and reinstalling wubi. hehe, no wonder.

A clean reinstall fixed all this.

---

### Post by hyper_ch on 2008-04-12
I don't think your harddisk crash had anything to do with the partitioning.

---

### Post by Crafty Kisses on 2008-04-12
> **hyper_ch said:**
> I don't think your harddisk crash had anything to do with the partitioning.

Yeah, honestly. That's why I'm saying if he's really that worried just go buy a 40GB HDD, those can't be all that much anymore. :)

---

### Post by Atro on 2008-04-12
Thank you, startx worked, but everytime I boot I need to enter this code.
I will try a fresh install next week or so. I have to deal with installing eclipse and flex and Axis again.

The reason for not getting a new HDD is that my power supply can not handle any more hadware, Im saving up money to buy a new PC and then I will dedicate this one to ubuntu. sad tho ubuntu always gets the shitty hardware

I was thinking of waiting till I get my new PC and then try ubuntu, but I love this thing, and apart from facing fatal errors sometimes and listening to my girlfriend nagging about it, its a fine experience

---

