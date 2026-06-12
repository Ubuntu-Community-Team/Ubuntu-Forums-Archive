---
title: "What would cause this black square behind my gdesklets?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-01-31
I can't seem to find this anywhere, but for some reason, my gdesklets all have a black square/rectangle area appearing behind the widget now that I can't make go away...maddening...what would cause that?  I have Beryl running, but I had Beryl running before I installed gdesklets, and they worked fine for a week or so...any ideas?  Thanks.

---

### Post by NewOldTimer on 2007-01-31
[IMG]http://file:///home/kenny/Desktop/Screenshot.png[/IMG]  hope the shot show's 1st time attaching a .png  



guess not sorry

---

### Post by NewOldTimer on 2007-01-31
[http://www.ubuntuforums.org/attachment.php?attachmentid=24264&stc=1&d=1170287900](http://www.ubuntuforums.org/attachment.php?attachmentid=24264&stc=1&d=1170287900)


I'm sorry can't figue out this sending stuff yet, anyways say's    "due to limitations of older X servers you might see blocks around desklets in float mode. this cannot be solved in a satisfying wat except for switching the X server to real translucency {Xorg 6.8 and above}"

---

### Post by ComplexNumber on 2007-01-31
> **kexodusc said:**
> I can't seem to find this anywhere, but for some reason, my gdesklets all have a black square/rectangle area appearing behind the widget now that I can't make go away...maddening...what would cause that?  I have Beryl running, but I had Beryl running before I installed gdesklets, and they worked fine for a week or so...any ideas?  Thanks.
just right click on the gdesklets and restart.

---

### Post by kexodusc on 2007-01-31
> **ComplexNumber said:**
> just right click on the gdesklets and restart.

Hi, and thanks, but restarting doesn't solve the problem.  I have Xorg 6.9.   These were working fine until sometime this week...hadn't loaded them up so i don't know when exactly. 
Thought maybe it might have been a setting somewhere, but that seems unlikely now.  I wonder if an update may have been responsible?

---

### Post by kexodusc on 2007-01-31
Or so it seems...

I right clicked the gdesklets icon to access "configuration", and simply unchecked a box that reads "Translucency (takes effect after restarting a display)".
This has solved the problem, but I'm not smart enough to understand why, exactly...:(
Oh well, smarts are overrated sometimes.

---

### Post by ComplexNumber on 2007-01-31
> **kexodusc said:**
> Hi, and thanks, but restarting doesn't solve the problem.  I have Xorg 6.9.   These were working fine until sometime this week...hadn't loaded them up so i don't know when exactly. 
Thought maybe it might have been a setting somewhere, but that seems unlikely now.  I wonder if an update may have been responsible?
sometimes, even when changing wallpaper (for example), the background of the gdesklets fails to update, and this leaves the colour of the old background behind (not the actual wallpaper, but the background colour behind the wallpaper). merely reselecting the wallpaper cures it.
what happens when you log out and then back in again?

---

### Post by kexodusc on 2007-02-01
> **ComplexNumber said:**
> sometimes, even when changing wallpaper (for example), the background of the gdesklets fails to update, and this leaves the colour of the old background behind (not the actual wallpaper, but the background colour behind the wallpaper). merely reselecting the wallpaper cures it.
what happens when you log out and then back in again?

When I log out log back in, restart, or even remove and reinstall gDesklets, that crazy black square remains.  Unless I uncheck the box I mentioned above.
No idea why, I'm afraid.

I dont' recall ever selecting that box, and only my wife and I use the machine, though she isn't one to dabble.  Maybe I did.  

At any rate, it seems fine now.  Just not sure what that checked box is doing exactly.  When searching this problem I found at least one other person with the same symptoms.  Maybe I'll fire him a PM.  

Thanks.

---

### Post by ComplexNumber on 2007-02-01
> Unless I uncheck the box I mentioned above.never really tried the trunsluscency thing on gdesklets.

---

### Post by jay_knight on 2007-02-28
I have the same problem, but the translucency checkbox does not solve the problem. DO you have any composite manager enables (such AIGLX or GLX)?

Does someone know how to fix this?

Thanks...
J.

---

### Post by Tomosaur on 2007-02-28
If you have recently updated your kernel, you may need to reinstall your graphics driver for little graphical effects to work again, although I'm not sure whether something this small requires it. If you do use self-installed drivers (ie, you installed them, they weren't there automatically), then just reinstall them.

---

### Post by jay_knight on 2007-03-01
thanks... tried that... didn't work...

It has something to do with the E17 background not being a true background. E17 should support 'true transparency', but I am unsure howto enable this. 

Someone?

---

