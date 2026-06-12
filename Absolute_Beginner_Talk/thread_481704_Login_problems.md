---
title: "Login problems"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Shadou00 on 2007-06-22
Okay, this morning I went into the Login screen settings GUI and changed some things (i cant tell you what exactly, i don't remember) and now when i boot up my computer the login screen doesnt come up after the loading thing. a loading mouse cursor just appears and it does that forever.

my question is: how do i reset my login screen?

Also i cant reinstall because there are files i want on my harddrive and im on vacation and don't have my Ubuntu CD

---

### Post by Crafty Kisses on 2007-06-22
> **Shadou00 said:**
> Okay, this morning I went into the Login screen settings GUI and changed some things (i cant tell you what exactly, i don't remember) and now when i boot up my computer the login screen doesnt come up after the loading thing. a loading mouse cursor just appears and it does that forever.

my question is: how do i reset my login screen?

Also i cant reinstall because there are files i want on my harddrive and im on vacation and don't have my Ubuntu CD
You can try reconfiguring your X server, press Cntrl-Alt-F1 and try this:

```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

---

### Post by Shadou00 on 2007-06-22
> **Codename said:**
> You can try reconfiguring your X server, press Cntrl-Alt-F1 and try this:

```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

The IRC suggested this and i tried this and it didnt work, it gets stuck like it did before

---

### Post by Crafty Kisses on 2007-06-22
> **Shadou00 said:**
> The IRC suggested this and i tried this and it didnt work, it gets stuck like it did before

Hmmm, what are your system specs?

---

### Post by NeoLithium on 2007-06-22
Have you tried
```
sudo dpkg-reconfigure gdm
```

---

### Post by Shadou00 on 2007-06-22
> **Codename said:**
> Hmmm, what are your system specs?

ATI Mobility
Intel pentium 4 2.80ghz
512mb of ram

i don't know any of the other specs :(

---

### Post by Crafty Kisses on 2007-06-22
> **Shadou00 said:**
> ATI Mobility
Intel pentium 4 2.80ghz
512mb of ram

i don't know any of the other specs :(

That's good enough, you should try the command suggested by NeoLithium, that might do the trick.

---

### Post by Shadou00 on 2007-06-22
> **Codename said:**
> That's good enough, you should try the command suggested by NeoLithium, that might do the trick.

> **NeoLithium said:**
> Have you tried
```
sudo dpkg-reconfigure gdm
```

didn't work :(

---

### Post by NeoLithium on 2007-06-22
Well, the only other thing I can think of, is to log in though the recovery mode kernel, and once you get to the command line environment, as root, type: ```
startx
``` Once you're in there you should be able to go to the login window preferences and see what you might have done in there.

There may be a better way, but this is the only thing that comes to my mind :(

---

### Post by Crafty Kisses on 2007-06-22
> **NeoLithium said:**
> Well, the only other thing I can think of, is to log in though the recovery mode kernel, and once you get to the command line environment, as root, type: ```
startx
``` Once you're in there you should be able to go to the login window preferences and see what you might have done in there.

There may be a better way, but this is the only thing that comes to my mind :(

You beat me too it ;), the RAM seems fine and everything else seems OK, so I don't see what the problem is, you might want to use a older Version of Ubuntu 6,10 possibly.

---

### Post by Shadou00 on 2007-06-22
> **NeoLithium said:**
> Well, the only other thing I can think of, is to log in though the recovery mode kernel, and once you get to the command line environment, as root, type: ```
startx
``` Once you're in there you should be able to go to the login window preferences and see what you might have done in there.

There may be a better way, but this is the only thing that comes to my mind :(


recovery kernel?

---

### Post by NeoLithium on 2007-06-22
> **Codename said:**
> You beat me too it ;), the RAM seems fine and everything else seems OK, so I don't see what the problem is, you might want to use a older Version of Ubuntu 6,10 possibly.

No, his system is perfectly fine for running the version he has; there's something that he changed within gdmsetup that I can't quite guess at, perhaps this might let him get a look and refresh his memory :)

---

### Post by Shadou00 on 2007-06-22
> **NeoLithium said:**
> No, his system is perfectly fine for running the version he has; there's something that he changed within gdmsetup that I can't quite guess at, perhaps this might let him get a look and refresh his memory :)

i changed the login theme....and the text it displayed and "allow administrator to login" or something

also when i hit Ctrl+Alt+f1 it gives me an error every once in a while:

[  920.932097] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

### Post by NeoLithium on 2007-06-22
> **Shadou00 said:**
> recovery kernel?

You bet. When you boot your computer up, you'll see the grub countdown, you can hit ESC to enter the grub menu, and just select the kernel that has (Recovery Mode) next to it. That gives you a command line interface as root, no Xserver, so you can fix some things.

Once you're in that mode, type
```
startx
``` and it should load gnome for you, and allow you to find out what went wrong :)

---

### Post by Shadou00 on 2007-06-22
> **NeoLithium said:**
> You bet. When you boot your computer up, you'll see the grub countdown, you can hit ESC to enter the grub menu, and just select the kernel that has (Recovery Mode) next to it. That gives you a command line interface as root, no Xserver, so you can fix some things.

Once you're in that mode, type
```
startx
``` and it should load gnome for you, and allow you to find out what went wrong :)

:D X started

But when i tried to open the Login window GUI setup it told me that GDM isn't running

?

---

### Post by NeoLithium on 2007-06-22
Ahhh, ok. Open up a terminal and type:
```

sudo /etc/init.d/gdm start

```

That will restart the GDM daemon for you :)

---

### Post by Shadou00 on 2007-06-22
> **NeoLithium said:**
> Ahhh, ok. Open up a terminal and type:
```

sudo /etc/init.d/gdm start

```

That will restart the GDM daemon for you :)

i changed everything back and it still hangs :(

is there any way to make everything default again?

---

### Post by NeoLithium on 2007-06-22
Hmmm, this is just another shot in the dark by me, you might want to see input first, BUT, if you're logged in to the recovery console, I was thinking that perhaps
```
sudo aptitude purge gdm
and then
sudo aptitude install gdm
```
Might work.  Though I'm not completely certain about that.

---

### Post by Shadou00 on 2007-06-22
> **NeoLithium said:**
> Hmmm, this is just another shot in the dark by me, you might want to see input first, BUT, if you're logged in to the recovery console, I was thinking that perhaps
```
sudo aptitude purge gdm
and then
sudo aptitude install gdm
```
Might work.  Though I'm not completely certain about that.

yes! that worked! thank you so much

---

### Post by NeoLithium on 2007-06-22
You're very welcome :)

---

### Post by danbar on 2007-06-24
How do I log in as administrator in gui ?

---

### Post by jorj on 2007-06-26
Hello there,

I had a very similar problem, but in my case, after leaving my computer to download something from the internet, I came back and was working really slow, then I pressed Ctrl + Alt + BackSpace and thus restarted X. However, now, every time I tried to login in, would insert my username and password, the screen would go black and then come back to the login screen again and again.

Tip: what had actually happened (twice within a couple of weeks which is why I am posting this) was that I didn't have any more memory on my system and X did not have enough memory to load. Literally, the 5gb allocated to Kubuntu were used completely and that is why it wouldn't log in.

Took me quite a while to figure that out, but it might happen to others as well, so this might be your case as well if none of the above worked? 

You can go and choose your session, choose "console login" at the login screen, then login, su as root, and type "startx" (without the "") and your session should start as root. from there you can edit pretty much everything and delete any data on your computer, in my case, i deleted my download.

There is therfore no need for you to reinstall, as long as you have access to root login and startx from there, you can probably fix it. 

Ultimately, although I wouldn't recommend it, once logged into root, create a new user account under user management in system settings (might be different in gnome, I'm using kde) and then copy/move all your /home/user1 data to /home/user2 just created. this way everything should be copied and you should have the same settings but hopefully without whatever interferes with your login.

Then again, I'm not so sure about this method so please bear that in mind.

Hope you fix it, (although if you're on holiday you might as well just use it as root and wait till you come back to fix it ;) ) just a thought :p

---

### Post by danielmendesleao on 2007-07-02
> **NeoLithium said:**
> Hmmm, this is just another shot in the dark by me, you might want to see input first, BUT, if you're logged in to the recovery console, I was thinking that perhaps
```
sudo aptitude purge gdm
and then
sudo aptitude install gdm
```
Might work.  Though I'm not completely certain about that.
Hey NeoLithium... thanks alot... worked for me too.
i was looking for an answer for this for 3 days now.
;)

---

### Post by Raineer on 2007-07-02
> **danbar said:**
> How do I log in as administrator in gui ?

You don't actually "log in" as root, but you can run commands that way.  Press Alt-F2 and type
```
gksudo 
```
followed by the command you want to run, this should prompt you for a password and run that instance of the program as root

---

