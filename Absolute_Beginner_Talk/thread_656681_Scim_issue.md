---
title: "Scim issue"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by andyho on 2008-01-02
I've had a skim issue since I re-installed it.. Now it opens with EVERYTHING! If I close it at boot up and then open a terminal, it restarts.. close it, open firefox, reopens again.. Over and over. Any idea on how I can get it set to only switch to a different language if I specify it to? I have the hot keys set, but they don't seem to work either. Thanks for any help!!

---

### Post by Harpoon on 2008-01-02
First, this drove me nuts as well, and I found it so annoying I uninstalled it.  I use it infrequently, so I can bear with the install/uninstall routine.  However, you might try going to System->Administration->BootUp-Manager and deselecting the checkbox (if it appears there), and choosing stop and apply now.  That will disable it so it doesn't pop up (I am assuming it will show up in the menu.  If that is not correct, sorry).  Anyway, if that works, and you need to use it, go bak to the menu, select it and let it start the proccess again.

BTW, you might want to edit the title of the post to read SCIM, rather than skim :)

Good luck with this.  I am off to a no internet location so it will be a while before I can check back.

---

### Post by Sef on 2008-01-07
What do you use to activate scim?  Check and see what activates it.

---

### Post by andyho on 2008-01-08
Sef - thx for closing the other thread and renaming this one for me! :) That's the thing.. I never designated anything to open it! At startup it always asks me what I want to open it with, but I always close it because I don't necessarily want it "attached" to any one prog. I use it in OO, Kopete, Gimp, and Firefox. I just want to figure out how I can set it to open just when I need it, even if it just runs in the background. Kinda like in Windows I could just go down to the language bar and designate when I wanted a different language. Make sense?? Thanks again!!

---

### Post by andyho on 2008-01-17
bump

---

### Post by vambo on 2008-01-17
Usually <shift> <space> switches it on/off.

---

### Post by Brian96 on 2008-02-01
> **andyho said:**
> Sef - thx for closing the other thread and renaming this one for me! :) That's the thing.. I never designated anything to open it! At startup it always asks me what I want to open it with, but I always close it because I don't necessarily want it "attached" to any one prog. I use it in OO, Kopete, Gimp, and Firefox. I just want to figure out how I can set it to open just when I need it, even if it just runs in the background. Kinda like in Windows I could just go down to the language bar and designate when I wanted a different language. Make sense?? Thanks again!!

I found this when I was searching on another problem (my problem is scim-launcher is suddenly hogging all my memory when I open ANY program and hosing up my system).

Anyway, I haven't played around with this, but I think the issue is that the HOWTOs we follow to get scim working (particularly using a non-English language in an English session) get the scim daemon running all the time. I wonder if we could disable this option (not really sure how, though) and then create a custom launcher for the scim daemon to put in our panel or menu.

---

### Post by Brian96 on 2008-02-01
> **andyho said:**
> I've had a skim issue since I re-installed it.. Now it opens with EVERYTHING! If I close it at boot up and then open a terminal, it restarts.. close it, open firefox, reopens again.. Over and over. Any idea on how I can get it set to only switch to a different language if I specify it to? I have the hot keys set, but they don't seem to work either. Thanks for any help!!

As I re-read this, I wonder if you don't have other problems, such as some configuration issue. Do you mean that the skim/scim language selector opens with every program, or that the icon shows up in your notification area and you don't want to see it? If the latter, there is a setting in the Global Settings menu in the scim/skim dialogue. If the former, I'm not really sure what is going on.

---

### Post by andyho on 2008-03-25
> **Brian96 said:**
> As I re-read this, I wonder if you don't have other problems, such as some configuration issue. Do you mean that the skim/scim language selector opens with every program, or that the icon shows up in your notification area and you don't want to see it? If the latter, there is a setting in the Global Settings menu in the scim/skim dialogue. If the former, I'm not really sure what is going on.

Wow! I kinda forgot about this thread but I'm actually kinda having the same issue still. I tried the how-to with the uim, but things just still aren't entirely configured correctly, I'm sure... I CAN switch through languages now. Only with keyboard shortcuts, which is fine.. but it kinda would be nice to have some type of indicator so I can SEE what is selected without just typing and seeing if I got the right shortcut! LOL! Now I do get scim at startup still, but I did designate it to open with OO so it pops up for a sec, and then disappears. I did read that scim always runs, so there isn't exactly an on/off, other than switching the language.

Before what was happening though is it would automatically switch languages on me whenever a program would open. ANY program!! And then I couldn't get it to switch back to English for whatever reason! At least that's fixed!!

I think now what my problem could be is that I just have conflicting things installed! I know there's scim, anthy, uim.. at the very least on here. I'm still relatively new to the whole linux scene... but I'm definitely to that point where I want to learn the things to get things functioning better, rather than looking pretty!! LOL!

Thanks for the info though!!! :)

---

