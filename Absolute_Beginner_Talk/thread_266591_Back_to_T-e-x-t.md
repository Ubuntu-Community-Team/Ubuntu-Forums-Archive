---
title: "Back to T-e-x-t"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-09-27
Well, I seem to have a strange problem with my install
During boot, all seems to be fine with the splash till it reaches the line
"Checking all filesystems"
Then is suddenly switches to text mode..and eerything is normal after 
that..Iniatially I thought it was errors in Win drive..but it happens
for no reason at all..

Can someone throw some light??

---

### Post by Perfect Storm on 2006-09-27
So you don't have any Desktop? (as I understand it?)
If so what happen if you type
```
startx
```

---

### Post by Metacarpal on 2006-09-27
> **hellmet said:**
> Well, I seem to have a strange problem with my install
During boot, all seems to be fine with the splash till it reaches the line
"Checking all filesystems"
Then is suddenly switches to text mode..and eerything is normal after 
that..Iniatially I thought it was errors in Win drive..but it happens
for no reason at all..

Can someone throw some light??

Once every 30 or so boots, it automatically checks the filesystem on the drive Ubuntu is installed on.  When it does this, it switches to a text display.  It should have a progress bar, and when it hits 100%, it should continue booting and go to your graphical login.

Depending on the drive size, the check may take a while.  It can also start automatically if the computer isn't shut down properly.

Is that what you see happening?  If so, just wait it out.

Edit: If Ubuntu is running that check on every single boot, there may be a problem with the shutdown process.  If so, do you always choose shutdown/turn off computer when you're logging off, or do you just switch off the power after logging out?

---

### Post by hellmet on 2006-09-28
I do go to the GUI ..
It does not check the filesystem...but it definitely moves to text mode..
Cud that be errors in the Windows file system??

I always turn it off using Turn Off or Restart..

---

### Post by CatKiller on 2006-09-28
The screen will switch to the text layout if a particular stage is taking a long time - which is why it happens for the 30-times-mounted disk check that people have seen most frequently - although I've seen it for other stages too - when I hadn't got my network card set up properly, for example. In and of itself it isn't a problem, but it may be indicating a deeper problem with the bootup routine if its happening every time. Without more details, it'll be impossible for anyone to diagnose what that problem might be.

---

### Post by hellmet on 2006-09-28
what kind of details shud I provide??
I'll try to get them

---

### Post by CatKiller on 2006-09-28
I don't know, I'm afraid. I've already passed on the tiny amount that I know about the Ubuntu boot process.

If Ubuntu starts OK anyway, does it matter? Otherwise, you could start a new thread with a title like "Delay during startup" and list as many symptoms as you can.

---

### Post by Metacarpal on 2006-09-28
> **hellmet said:**
> what kind of details shud I provide??
I'll try to get them

What's the last status message in the usplash screen before it goes to text?

---

### Post by Brunellus on 2006-09-28
If it's only scrolling the boot messages in text, I'm not sure what the problem is.  Personally, I prefer this...usplash never really did it for me.

---

### Post by hellmet on 2006-09-28
"Checking all filesystems"...

the reason I am asking this is coz I want to put a custom Boot Splash..
i am tired of the default one...

I love SuSe's Splash..
but I don't like the actual OS tho

---

### Post by Brunellus on 2006-09-28
the system will fsck if something shut down suddenly.  Did you just pull the plug on a running system without shutting it down cleanly?

---

### Post by CatKiller on 2006-09-28
> **hellmet said:**
> "Checking all filesystems"...

the reason I am asking this is coz I want to put a custom Boot Splash..
i am tired of the default one...

So was it an attempt to do this that caused the text to be displayed rather than the default splash screen?

Anyway, you could look at the [USplash Customization HOWTO]("https://help.ubuntu.com/community/USplashCustomizationHowto") on the wiki for guidance.

---

### Post by hellmet on 2006-09-28
no no..I want to add a custom splash..but if this thing keeps going back
to text after only a few seconds of Splash..then its gonna be of no use..
I was OK with this text till I wanted to get myself a new nice looking splash..

---

### Post by Metacarpal on 2006-09-28
Did you make any changes to your system before this started happening - tweaks, updates, new software, etc?

---

### Post by hellmet on 2006-09-29
well, its been the same during previous installs also..
no matter how new or how old the install is , its always been like this

---

### Post by Metacarpal on 2006-09-29
So it does that on a fresh install too?

Oooh.  Sounds like it might be early-stage hard drive failure. :(  That or, hopefully, Ubuntu is just having a hard time identifying your particular hard drive.

---

### Post by CatKiller on 2006-09-29
> **Metacarpal said:**
> So it does that on a fresh install too?

Oooh.  Sounds like it might be early-stage hard drive failure. :( 

Or IDE controller. Or a flaky cable. Or something else on the same cable... there are many hardware problems that could interfere with hard drive detection.

---

