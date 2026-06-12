---
title: "black screen after power safe won't recover"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by bumpino on 2008-02-10
Hi there, first post, new to Ubuntu. Not sure if this is the right place for my post though.

My notebook screen goes to power save (or at least turns black) after some time without user interaction. So far that's not a problem but it won't recover. I can see and move the mouse pointer but the rest is black and it kinda makes operating the system hard. :-)

Now I don't know where to start with solving this problem. Is it a graphics driver issue, some general power saving problem? Is it window manager specific? Don't remember having this Problem with KDE, just now it's there with fluxbox.

Any hints on where to start looking?

---

### Post by mikkenzi on 2008-02-10
Hi:)
I'm new with this but just a question - does your keyboard work? Can you, for example, call a console with a combination of keys? 
I'm stupid, actually you won't be able to see it it it's all black... and that seems to me some kind of hardware issue - screen or graphics card problem.

---

### Post by kolvas on 2008-02-10
actually i had the same exact problem. i am using a laptop. i could see the pointer but no screen content. nothing i tried would make the desktop show itself. i have no graphics card/memory or other problems. i had to reboot holding down the power key.  one note: this happened when i had the lid opened for about 4-5 hours. when i close the lid, this problem doesn't seem to occur.

---

### Post by bumpino on 2008-02-10
> **mikkenzi said:**
> does your keyboard work? Can you, for example, call a console with a combination of keys? I'm stupid, actually you won't be able to see it it it's all black...

I can't see but I can tell by the system's reaction. Yes everything works, I'm just not able to see anything of it. :-)

> and that seems to me some kind of hardware issue - screen or graphics card problem.

Some hardware-software-interaction issue I'd say because it used to work under different circumstances.

---

### Post by bumpino on 2008-02-10
> **kolvas said:**
> one note: this happened when i had the lid opened for about 4-5 hours. when i close the lid, this problem doesn't seem to occur.

Thank you for the hint. Never actually tried to close the lid while the notbook was on but like in your case, the problem doesn't occur with the closed lid. Even better: when closing and reopening it, the formerly black screen gets activated again. Didn't really solve the whole problem but it's a simple workaround.

Uhhh, how did you get rid of the problem?

---

### Post by cknight on 2008-02-10
Well, this is a long shot, but if you think your keyboard is working, try binding this to a key combination in your keys file:

```
xset dpms force on
```

This should force your monitor to turn itself on if its in Energy saving mode.  But then again, mouse movement/keyboard interaction should do the same thing.  Worth a try anyway. 

Out of curiosity, if you change the above to 'off' instead of 'on' (which will put your monitor into an energy saving screen-off state), can you recover normally?

Good luck!

---

### Post by beercz on 2008-02-10
> **bumpino said:**
> Hi there, first post, new to Ubuntu. Not sure if this is the right place for my post though.

My notebook screen goes to power save (or at least turns black) after some time without user interaction. So far that's not a problem but it won't recover. I can see and move the mouse pointer but the rest is black and it kinda makes operating the system hard. :-)

Now I don't know where to start with solving this problem. Is it a graphics driver issue, some general power saving problem? Is it window manager specific? Don't remember having this Problem with KDE, just now it's there with fluxbox.

Any hints on where to start looking?
This may be a suspend issue.

On my HP Compaq nx7400 laptop when I resume from suspend, I have to turn up the brightness then I can continue.  Have you tried that?

There are known issues with hibernate and suspend with some laptops (mine included).

Have you tried searching the forums, and [launchpad]("https://answers.launchpad.net/ubuntu") (the bug tracking tool)?

---

### Post by bumpino on 2008-02-13
> **beercz said:**
> On my HP Compaq nx7400 laptop when I resume from suspend, I have to turn up the brightness then I can continue.  Have you tried that?
Brightness is on the highest level. I don't think it's a sleep or suspend issue because as far as I can see the notebook isn't sleeping, just the screen is turned off. Oh and I can manually send the notebook to sleep or suspend and fully recover.

> Have you tried searching the forums, and [launchpad]("https://answers.launchpad.net/ubuntu") (the bug tracking tool)?
Yes I did but I couldn't find anything of use for my specific problem

> **cknight said:**
> 
Well, this is a long shot, but if you think your keyboard is working, try binding this to a key combination in your keys file:

Code:

xset dpms force on


Thanks a lot for this one, it actually seems to work!

[QUOTE=cknight]
Out of curiosity, if you change the above to 'off' instead of 'on' (which will put your monitor into an energy saving screen-off state), can you recover normally?
[/QUOTE]
Yes in that case I can recover normally.

Well, thank you all. Forums and the people in them just rock! I consider my problem solved. (Unless someone just happens to have the perfect solution on how to make my screen visible by just pressing a key or moving the mouse.)

Cheers
bumpino

---

