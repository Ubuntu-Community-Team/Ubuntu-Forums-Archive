---
title: "Trying to start Ubuntu in &quot;safe&quot; mode"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-04
I installed Xubuntu from Synaptic. I did this once before and no problem at all. This time there is a conflict. I can't get in because of video hangup. I even tried rebooting. I can't get to the splash screen. I tried starting in "safe" mode. I think that is the term. Anyway, it loads up and then ask me for input. I don't know what to type in there. The line starts with the work "root". Can  anyone give me help and tell what it is asking for? Thank you. I really dislike  having to reload from a fresh install. I'm using Windows to post this.

---

### Post by Spr0k3t on 2007-03-04
Post up the output of your "lshw" and "lspci".  I'm wondering if the conflict isn't in the binary modules.

---

### Post by Aliarse on 2007-03-04
What happens when you try to boot up normally? Does it say X failed to start blah blah blah inside of a blue box?

---

### Post by kittyhawk63 on 2007-03-04
> **Spr0k3t said:**
> Post up the output of your "lshw" and "lspci".  I'm wondering if the conflict isn't in the binary modules.

Don't know what you are referring to or how to get to it. Remember, I hang up "before" I get to any splash screen. I don't see anything having to do with Linux. I don't even see the screen where you see all the installation file lines running and "ok" at the right.

---

### Post by kittyhawk63 on 2007-03-04
> **Aliarse said:**
> What happens when you try to boot up normally? Does it say X failed to start blah blah blah inside of a blue box?

I don't see "anything" but that I need to adjust my monitor resolution.

---

### Post by kittyhawk63 on 2007-03-04
Does anyone know what I am supposed to type in the safe mode screen when it ask for input?

---

### Post by Aliarse on 2007-03-04
Let me get this straight. When you boot up in normal mode, and get to where you normally see the login screen, you just get a black screen, and an out of range error?

---

### Post by kittyhawk63 on 2007-03-04
> **Aliarse said:**
> Let me get this straight. When you boot up in normal mode, and get to where you normally see the login screen, you just get a black screen, and an out of range error?

Edit sorry that is correct.

---

### Post by Spr0k3t on 2007-03-04
> **kittyhawk63 said:**
> Does anyone know what I am supposed to type in the safe mode screen when it ask for input?

```
lshw
```

and

```
lspci
```

Then come back and post your results.

Another option would be to type "startx" to see what information comes up.

---

### Post by kittyhawk63 on 2007-03-04
Aliarse,

That is correct.

---

### Post by kittyhawk63 on 2007-03-04
> **Spr0k3t said:**
> ```
lshw
```and

```
lspci
```Then come back and post your results.

Another option would be to type "startx" to see what information comes up.

Are you telling me to enter these two codes at the input line of the safe mode?

---

### Post by Aliarse on 2007-03-04
hmm. only thing i can suggest is to try those commands spr0k3t gave you.

When you get to the root@username part after booting in safemode, type those commands he posted, which will give you a list of text, write them down and post them back here for sproket to look at.

I thought it was a simple xorg.conf error, but if you cant even see the boot up process, something else is seriously wrong, and is out of my depth of knowledge.

---

### Post by kittyhawk63 on 2007-03-04
> **Aliarse said:**
> hmm. only thing i can suggest is to try those commands spr0k3t gave you.

When you get to the root@username part after booting in safemode, type those commands he posted, which will give you a list of text, write them down and post them back here for sproket to look at.

I thought it was a simple xorg.conf error, but if you cant even see the boot up process, something else is seriously wrong, and is out of my depth of knowledge.

I misspoke. I think I do see the boot up process. I would have to go and look at this again.

I am on my way to see what the results of are with sprok3t suggestion.

---

### Post by Aliarse on 2007-03-04
> **kittyhawk63 said:**
> Aliarse,

That is correct.

So it is booting up, and when you get to the login screen it gives you the out of range error?


If so i think your xorg.conf is messed up. To reconfigure it, start up in normal mode when you get to the black screen, press CTRL + ALT + F1 to get into a login shell. Input your user/pass and press enter, you'll then get an input terminal, type this into there. :

sudo dpkg-reconfigure xserver-xorg

and go through the options.

Once done, type:

sudo /etc/init.d/gdm stop
then
sudo /etc/init.d/gdm start

If that one fails, you could try : 

sudo dpkg-reonfigure -foninteractive xserver-xorg

Which will try to set it up automatically by detecting the values from your hardware. 

Then do the sudo /etc/init.d/gdm stop/start thing again.

HTH.

---

### Post by kittyhawk63 on 2007-03-04
> **Aliarse said:**
> So it is booting up, and when you get to the login screen it gives you the out of range error?
If so i think your xorg.conf is messed up. To reconfigure it, start up in normal mode when you get to the black screen, press CTRL + ALT + F1 to get into a login shell. Input your user/pass and press enter, you'll then get an input terminal, type this into there. :
sudo dpkg-reconfigure xserver-xorg
and go through the options.
Once done, type:
sudo /etc/init.d/gdm stop
then
sudo /etc/init.d/gdm start
If that one fails, you could try : 
sudo dpkg-reonfigure -foninteractive xserver-xorg
Which will try to set it up automatically by detecting the values from your hardware. 
Then do the sudo /etc/init.d/gdm stop/start thing again.
HTH.

Thank you guys. I was hoping to have this resolved with the few minutes I had. I must leave now and get prepared for church. **I will try your suggestion Aliarse** after I get home from church. The request for "lshw" and lspci" went by so fast on the screen that I could not see all the lines. What I did see would have taken me more than a half hour to write down on paper and then type back to you here on the post. 

Thank you both for your help.

---

### Post by kittyhawk63 on 2007-03-04
Hi Guys. I had a few minutes before I head off to church. I am posting this from inside Ubuntu. Thanks you very much for your help. Aliarse, I followed your instructions to the letter and it got me into Ubuntu. I can't thank you enough. I am gong to uninstall Xubuntu and stay away from the Synaptic install of it. The first time I installed it, it went without a hitch. This time I did the same thing and it would not work. :confused:
Again, Thank You. Four gold stars. :KS:KS:KS:KS
kh

---

### Post by kittyhawk63 on 2007-03-05
Well, your directions did get me into Ubuntu. I went in and deleted Xubuntu and rebooted. I had the same problem again. Video hanging. I felt compelled, and reinstalled Ubuntu. Problems are over. Thanks again for all the help.

---

### Post by sdiphoto on 2007-12-15
So, I have the GeForce 6200. It was working fine, spanning 2 monitors...but I was getting the scrolling desktop issue. I set the 2nd monitor to mirror the primary, and after that I couldnt get the Screens and Graphics app to start anymore. Then, when it rebooted, I had nothing but static lines on my screens.

I went into debug, typed in the reconfigure stuff above, and now the monitor flickers 3 times with the NVidia logo, then the screen just sits blank with the following showing

```

* Starting anac(h)ronistic cron anacron [ok]
* starting deferred execution scheduler atd [ok]
* starting periodic command scheduler crond [ok]
* checking battery state... [ok]
* running local boot scripts (/etc/rc.local) [ok]

```

and if I type anything on the screen, it just echoes the keyboard with no effect...I dont know anything about Linux code, which is why I tried Ubuntu 7.10, since it's supposed to be the "beginner" Linux...but this is frustrating.

---

### Post by Guilden_NL on 2008-03-05
> **Aliarse said:**
> So it is booting up, and when you get to the login screen it gives you the out of range error?


If so i think your xorg.conf is messed up. To reconfigure it, start up in normal mode when you get to the black screen, press CTRL + ALT + F1 to get into a login shell. Input your user/pass and press enter, you'll then get an input terminal, type this into there. :

sudo dpkg-reconfigure xserver-xorg

and go through the options.

Once done, type:

sudo /etc/init.d/gdm stop
then
sudo /etc/init.d/gdm start

If that one fails, you could try : 

sudo dpkg-reonfigure -foninteractive xserver-xorg

Which will try to set it up automatically by detecting the values from your hardware. 

Then do the sudo /etc/init.d/gdm stop/start thing again.

HTH.

Two thumbs up for your help! I haven't had to mess with XServer since '98 and have forgotten this.
It worked on my extremely complex home built screamer box.  Everything worked fine until I tweaked the nvidea driver.

I should have left it alone, but was back up and running in <15 mins thanks to your post.

---

### Post by munitor on 2008-05-10
Thanks, Aliarse. This thread really helped me out!

---

### Post by ripudio on 2008-05-24
So, I had the same problem as many of the people in this thread, I updated the ATI drivers and I guess it change the default screen resolution, thus I got an "out of range error." Thankfully I found this thread, went through the steps and now I can see things again! Unfortunately, once I get through the log-in screen, all I see is white. The funny thing is, the desktop cube function still works. I have no idea why this is, or how to fix it and I'd greatly appreciate any help that could be offered, thanks for making my slow migration to ubuntu that much less painful.

---

