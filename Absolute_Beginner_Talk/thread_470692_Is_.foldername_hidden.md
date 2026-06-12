---
title: "Is .foldername hidden?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Corvinis on 2007-06-11
Hey peeps,

I'm trying to open a subfolder starting with .config in ubuntu..... however I can't see the folder even if I turn hidden files on..... if the "." in front of a folder means hidden anyway (Tried opening it with gksudo via terminal btw)

According to the package the folder is supposed to be there.... Does someone have a clue as to why it's not showing?

Greets,

Corvinis

---

### Post by Outrunner on 2007-06-11
Well, did you try

```
nautilus .config/
```

---

### Post by freebeer on 2007-06-11
.foldername will be normally hidden.

I just did a test to be sure... went to Places -> home folder.  Hit CRTL-H and all the hidden folders were now visible.

---

### Post by Corvinis on 2007-06-11
Isn't nautilus .config/ the same as just navigating towards the folder? Or does a direct path help in this case? I did try it with gksudo in front..... 

Cheers

---

### Post by Outrunner on 2007-06-11
> **Corvinis said:**
> Isn't nautilus .config/ the same as just navigating towards the folder? Or does a direct path help in this case? I did try it with gksudo in front..... 

Cheers

Umm yes it is, but since you said you can't see the folder(use CTRL-H as mentioned above), I just thought I'd give you this command. Does it not work?

---

### Post by Tundro Walker on 2007-06-11
Ubuntu (and Linux/Unix in general) use a leading period to denote a "hidden" file/folder.  These, as you guessed, are mostly config files/folders.

In Nautilus, you can "show hidden files" by either pressing CTRL+H, or going to "VIEW" menu and checking the box next to "show hidden files".

In normal circumstances, you don't really want to see them.  That way you don't accidentally click on one and screw it up.  But when tweaking your machine out (or if you're like some and just always like to see what's on your machine), then it's good to see them.  If you have non-technical users sharing your machine, I'd make sure they never see the hidden files.  You don't want them screwing with something they don't know about, much less even seeing it, which would prompt paranoid questions that don't really need to be answered in the first place.

> You: "Ok, so what happened before your computer started acting up?"

Them: "Well, I clicked on my "home" folder and there were like all these "." files and folders.  I don't remember making them, so I got rid of them.  They looked really technical.  I figured I had some kinda virus and it was creating those things to spread across my computer.  I also proactively purged them from the rest of my folders, too."

You: (hand on face, sighing)

---

### Post by Corvinis on 2007-06-11
Lol I'll give the CTRL + H a try then ;) 

Thanks for the lively explanation mate :P

Greetings & Have a good one,

Corvinis

BTW: It's my own server so.... noone touches my preeciouss!!!!! *GOLEM GOLEM!*

Offtopic: Damn! I spilled 'em beans!

---

### Post by Tomosaur on 2007-06-11
.foldername = hidden file, so you should technically be able to see the file if you enable the 'show hidden files' option.

---

