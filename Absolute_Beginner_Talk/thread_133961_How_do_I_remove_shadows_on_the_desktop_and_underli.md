---
title: "How do I remove shadows on the desktop and underlines on file names in konqueror."
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-21
**[color="red"]*If you aren't in the mood to hear a pointless, bizarre rant (of me venting my frustrations), please do scroll down to the question below the next red sentence. Thank you.*[/color]**

 Okay, I've been using linux, and I love it, even through many of it's imperfections. My only problem is visuals. I'm not a command line guy. That's just not who I am. I used to be all into programming, but now I've learn to appreciate the pretty, simple GUI stuff as I don't have time or energy to remember and look up stuff anymore. The only thing I even use the command line for anymore these days is wireless and Regular expressions (grep, sed, the whole shebang, I love RegExs, most useful thing ever. I've built a friggin' shell script that automates the creation of a database of all my music files. See how useful linux is for me? Yes, these things have their windows equivalents, but it's just not as easy.) 

Okay, I am REALLY getting off topic. That was really, really bad. I'm normally not that off-topic so fast. The point is, I want to use KDE or gnome, because they're simpler to use. Simpler than IceWM, and Fluxbox, and XFCE. When I want to get where I want to, there are plenty of apps and ways to do it in KDE and Gnome, and they work. I like using them. The only problem is that Gnome makes me feel like I'm staring into a box, and the whole menu system, while intuitive, is just not as simple or easy to shift around as KDE's "one-menu-for-just-about-everything" mentality. So I use KDE. But the problem with both Gnome and KDE for me is this: The graphics are so busy that it makes me dizzy. Ugh, that sentence alone is making me sick to my stomach. I'm running off linux right now. I've gotten to the point where I can just work off linux and get all the tasks I would normally need to get done done for hours without having to switch off windows. But whenever I look at my desktop, I just feel like- "Ugh, I think I'm gonna barf" Whenever visuals come up when I'm talking linux or something - whenever KDE or Gnome comes up - I just say the same thing - they're ALL TOO BUSY. You know why people like reading text off a piece of paper and not off wood? Paper's easier to read. Simple, easy contrast. Not busy at all. You have content and background. You know why in museums they have simple, clean white designs? Not just to draw attention to the art - but otherwise it would just be overwhelming - the eye would have to take in too many things at once. And that's what it's like with KDE.

 I look at the desktop, or in a folder, and there are these really complicated overdone, did-I-mention-overly-complicated icons for every document, image, and other file, and every folder is looking just about way too 3d for me. I have only EVER seen transparent 3d folder icons on linux, and never on windows or macintosh - _and for good reason_. When you're looking at the computer screen, you are not looking for folder art. It doesn't help - it distracts the eye and wastes time every time you look at it, and it makes the screen, once again, too **busy** I {I know, I know, I should change icon themes, but the default icon set isn't the whole problem, just representational for my dislike of the entire general approach KDE and linux normally has to a good looking desktop - throw as much pointlessly fancy stuff as you can in there ;) . The fonts - the see-through-yet-reflective-surface on everything - the soft, fuzzy feel that windows normally have. Everytime I reinstall linux, I have to spend hours adjusting just so I don't feel like passing out after every session on my computer. It's not that I don't like linux, I just don't like the default settings. At all. They make me sick to my stomach. Thank god for KDE's customization abilities, eh? :???: 

For me - simple is better, less is more, etc. And I have been able to, through the meticulous expenditure of way too much time, implement that idea in most of my desktop, so my desktop isn't a jumbling clutter of dozens of different shiny objects all over the place. Yet there have been a few things I have been unable to change, one of them being my screen's brightness - which is perpetually annoying my eyes - I'm on a sony vaio VGN-FS630W, and have tried out the ubuntu packages for a sony vaio for adjusting brightness, hasn't worked... I really have to ask someone about that, lest my eyes burn out soon :-k . Second is shadows and underlines under words.

 **[color="red"]Okay, so here's the actual questions I came here to ask (and sorry, the title's inaccurate, can't change it to the right thing... that konqueror thing I fixed a while ago...):[/color]**

 1) How do I remove the shadows shown under every filename on the desktop? I've really looked around and I can't find how to do it. Those shadows under the text are really driving me nuts... I know they provide the only contrast under a white background - but that's something I'm willing to give up (if there was a way to change desktop filename text's color at whim, I'd like to know that too, so I could deal with the contrast problem instead of giving up light backgrounds), it's just that I find those shadows incredibly distracting and irritating. Is there any way I can remove them?

 2) Okay, this is bizarre, but... I often find myself very aggravated that the amount of filename showed in the top line of the file name in konqueror or the desktop is much shorter than it could be, and I have to continually truncate my thoughts and move to the next line every time I want to do anything? Is there any way to lengthen the amount of characters shown per line? 

Thanks for any help....

---

### Post by welsh_spud on 2006-02-21
I don't know about shadows, but you can change font colours by opening up Konqueror, then going to Settings > Configure Konqueror > Appearance. You can change the font colour from the small box in the middle.

---

### Post by pestilence on 2006-02-23
You can disable the shadows by right clicking on the desktop and selecting from the menu:
**Configure desktop** --> **Background** --> (Find a button somewhere at the right named Advanced Options) **Advanced Options** --> There is a check box named "**Enable shadow**" if you unclick this one it will stop producing shadows for desktop text.

---

### Post by aysiu on 2006-02-23
See the attached screenshot--it answers both of your problems.

That said, you may want to consider ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` It's an easy way to customize KDE to be as minimalist as possible.

---

