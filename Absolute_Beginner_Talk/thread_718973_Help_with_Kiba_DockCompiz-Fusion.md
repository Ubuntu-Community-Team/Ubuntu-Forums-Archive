---
title: "Help with Kiba Dock/Compiz-Fusion"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by biffinson on 2008-03-08
Just got ubuntu working last night and now i'm messing with compiz-fusion and kiba dock.

First, with compiz-fusion.. how do I get the four virtual desktops like on a mac, and how do i switch between them?

Second, I want a mac os x-esque dock, is the bst kiba dock?

If so, how do I install kiba dock?  The guides they have don't work with gutsy gibbon.

Thanks.

---

### Post by Inxsible on 2008-03-08
Have you installed the compiz fusion config manager ?

you can install it by ```
sudo aptitude install compizconfig-settings-manager
```I would suggest using Avant Window Navigator or AWN for your dock. Its far superior than Kiba. The last time I used Kiba, it was slow and used up a lot of memory

---

### Post by biffinson on 2008-03-08
I installed it, and ran it with compiz --replace in the terminal, but when i exit from the terminal everything gets messed up.. is there any way to make it so compzi is just always open?

---

### Post by RussellGee on 2008-03-08
Alt + F2 then type it.

Or you could install compiz-icon which would set everything by just clicking on the icon.

---

### Post by biffinson on 2008-03-08
is there no way to make it so it automatically just boots up when i log in?

---

### Post by Inxsible on 2008-03-08
> **biffinson said:**
> is there no way to make it so it automatically just boots up when i log in?
you can by adding it into the start up programs

System >>  Preferences >> Sessions

---

### Post by biffinson on 2008-03-08
Ok thanks, got it!

Now, I am trying to install the dock, but I can't seem to find any instructions.. do you mind helping with that :P

---

### Post by Inxsible on 2008-03-08
> **biffinson said:**
> Ok thanks, got it!

Now, I am trying to install the dock, but I can't seem to find any instructions.. do you mind helping with that :P


I am assuming, you are trying to install AWN. Here's the howto for AWN

[http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard](http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard)

---

### Post by biffinson on 2008-03-08
> **Inxsible said:**
> you can by adding it into the start up programs

System >>  Preferences >> Sessions


Sorry, but i'm having problems getting it run to startup.  On the sessions page where i add a program to start on bootup what would i enter in as the command?

Sorry, I am total noob.

---

### Post by Inxsible on 2008-03-08
> **biffinson said:**
> Sorry, but i'm having problems getting it run to startup.  On the sessions page where i add a program to start on bootup what would i enter in as the command?

Sorry, I am total noob.Command would be the same as you enter in a terminal. So in your case, for compiz fusion it should be
```
compiz --replace &
```But doesn't compiz start up automatically in Gutsy...?

which ubuntu version are you using?

---

### Post by biffinson on 2008-03-08
i'm using ubuntu gutsy gibbon and i put in that command you told me and compiz isn't running right now :(

Edit: it's not running afteri rebooted..

I put the compiz --replace & in my start up run thing so it would just always do that, and it worked, but every time i would open a terminal it would close compiz or just be loading the compiz stuff... :\

---

