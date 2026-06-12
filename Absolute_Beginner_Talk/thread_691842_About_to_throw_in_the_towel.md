---
title: "About to throw in the towel"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by medusa-09 on 2008-02-09
thanks to all of you who have tried to help me get ubuntu and my video card to recognize something besides low res. i've spent all my spare time this week performing sudos, mucking with drivers, running Envy, but at the end of the day - my display looks like crap. 

I'm giving it one last shot. to wit:

i'm running 7.1 on a dual core intel, nVidia GeForce 7050 integrated video. ubuntu has never given me more than 1024x1168 and is now stuck at 800. XP works just fine up to 1920x1200 on the same machine.

please do not tell me to sudo dpkg-reconfigure xserver-xorg -phigh or download envy - all those roads lead nowhere. if somebody has a reasonable fix for this, i will waste part of my Saturday dealing with it. nobody has yet explained what they *think* is going on - i've just been taking pot shots in the dark here.

if I can't get this fixed - hey, life goes on. OSX is fantastic and my XP box has never crashed once in almost two years. but i really want this to have a good ending. please, somebody...

medusa-09

---

### Post by KhaaL on 2008-02-09
hehe, I was actually going to suggest you'd run xserver-phigh :redface:

Anyway, I'll gladly try to help you. I'd like to take a glimpse of your file** /etc/X11/xorg.conf**

just open gedit or any other notepad and open the mentioned file and copy/paste it in here.

---

### Post by fiddledd on 2008-02-09
Just some thoughts, probably not gonna be any help. 

It may be that Ubuntu won't work correctly with the Integrated GFX no matter what you do. you could disable the nvidia driver and go back to the default nv that ships with Ubuntu (that's assuming you have the nvidia driver installed/enabled). The default driver worked better for me as far as resolution and refresh rates was concerned, however I couldn't use Compiz with it (but I didn't want to use it anyway, I don't much care about eye candy).

You could try changing the Monitor setting whether or not it recognised your monitor correctly.

You could wait for Hardy to be released and cross your fingers.

You could try another Distro, Mint, SUSE, PcLinuxOS, Mepis, etc.

As I said, I doubt I've helped you any, good luck :)

---

### Post by Ex-windows on 2008-02-09
Wow, Really wish I knew what could help you. I am assuming that you have the restricted drivers box checked and that you looked over your xorg.conf file to insure that the correct info is in there. Did you check the Manufacturers website for any possible bugs with the card? This may sound Maddening but maybe you could just go and enjoy your saturday and take a break from it. Sometimes that actually works when we get to frustrated with a partigular project. I
had to do that while working with the Wireless drivers.  I hope you dont throw in the towel as I am sure this can get resolved. 
The xorg file (as already mentioned ) is great place to strt
Good luck

---

### Post by R@inm@n on 2008-02-09
> **medusa-09 said:**
> thanks to all of you who have tried to help me get ubuntu and my video card to recognize something besides low res. i've spent all my spare time this week performing sudos, mucking with drivers, running Envy, but at the end of the day - my display looks like crap. 

I'm giving it one last shot. to wit:

i'm running 7.1 on a dual core intel, nVidia GeForce 7050 integrated video. ubuntu has never given me more than 1024x1168 and is now stuck at 800. XP works just fine up to 1920x1200 on the same machine.

please do not tell me to sudo dpkg-reconfigure xserver-xorg -phigh or download envy - all those roads lead nowhere. if somebody has a reasonable fix for this, i will waste part of my Saturday dealing with it. nobody has yet explained what they *think* is going on - i've just been taking pot shots in the dark here.

if I can't get this fixed - hey, life goes on. OSX is fantastic and my XP box has never crashed once in almost two years. but i really want this to have a good ending. please, somebody...

medusa-09



Graphics cards and drivers are Ubuntu's weakness, imo.

I have never been able to get mine to work properly, and have succeeded in wrecking several install of this OS by trying.

 Good luck with your search, in the end I just gave up and run the standard Ubuntu stuff.  

 If ATI ever get around to configuring a decent driver for Linux, i'll be all over it like white on rice...:)


   R.

---

### Post by Ex-windows on 2008-02-09
I dont know if this is relevant or not. perhap some of the more experienced members could check it out. I just visited this link 
[http://www.phoronix.com/scan.php?page=article&item=987&num=1](http://www.phoronix.com/scan.php?page=article&item=987&num=1)
and it implies that New drivers have been released. Maybe there is some hope here.

---

### Post by r4ik on 2008-02-09
@medusa-09

sudo gedit /etc/X11/xorg.conf

Search for section screen and modus,

Put "1920x1200" first save the file restart X (Ctrl-Alt-Backspace)

And see if it works.

Good luck !

---

### Post by smacattack on 2008-02-09
hang in there buddy! 

when i first installed Edgy 10 months ago... I had a motherload of a time trying to set up my display and my video drivers etc... now with Gutsy I can just install and everything works straight off. In a couple of months you may find that Hardy will solve your problem and you will be home free. 

best of luck.

---

