---
title: "What is X"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-06-29
What is X and how do you restart it? Every so often while reading I see someone say you have to restart X. So what is it and why do you have to restart it and how do you restart it?

I tried searching the forums and even the wiki and didn't come up with an answer.

Thank you

---

### Post by Maggot on 2006-06-29
X is the graphical server. Its actually pretty complicated if you look into what it exactly is but for simplicity sake (and the average user) its the 'windows' like environment you use.

---

### Post by Jucato on 2006-06-29
How to restart X? Ctrl+Alt+Backspace. Just make sure that you don't have anything important application running, because restarting X will automtically shutdown/restart all graphical apps, including GNOME.

Why restart X? Because you installed/modified something that can only be applied if X is refreshed, meaning restarted. Of course you could just restart your whole computer, but why bother, when you only need to restart X. This isn't Windows :D

What is X? Like what Maggot said, it's the graphical server or graphical engine. What it basically does is manage anything graphical (I know I'm going in circles), from displaying graphics (pixels, resolutions, lines, circles, etc), managing graphical output devices (monitors), and managing how input devices will affect graphics (mouse, keyboard, etc).

Maybe a wikipedia entry would be more understandable: [http://en.wikipedia.org/wiki/X_server](http://en.wikipedia.org/wiki/X_server)

---

### Post by az on 2006-06-29
Ubuntu is not one big program ruinning, it is a bunch of applications.  Some of them are stacked.

So the relationship firefox would have with the rest of the operating system is like this:

- Firefox is on the top of the stack.  It is one application that needs to display something.
- Metacity is the window manager.  It magages windows.  It decides where they apprear and what how to organise their behaviour and characteristics.
- Gnome desktop, including the display manager.  Among other things, it allows you to log into sessions on top of X.  Thanks Fenyx for pointing that out! (I forgot this and just editted it in...)
- Xorg is the X server.  It does the work of taking what is supposed to appear on screen and making it appear.
- The kernel manages memory and other ressources.  Xorg is a running process like all the others.  The kernel manages running the proesses.

It is relevant because there are many applications that do not require a graphical display to work.  You can listen to music, burn a cd, read your emails, filter spam - all without running X or even having it installed.  The graphical system is optional.

---

### Post by nudnik on 2006-06-29
You forgot to mention the X server bites. :D  (I am so helpful)

---

### Post by H.E. Pennypacker on 2006-06-29
azz, why are we subjected to all this stuff?  Most users probably don't care about all this stuff, and don't want to know.  

With every different set of instructions, you have to restart this and that.  It'd be a lot easier if one button that said "restart" would cover everything.  Well, that button would restart the computer, but its better than having to find out what all these different parts of  Linux are.  It takes less time to restart your computer than having to read what X, Gnome, Metacity, and everything else is.  

Windows never tells you to restart this and that.  It will just tell you to restart the computer, which is a pain, but probably not as much of a main as reading things.

---

### Post by Jucato on 2006-06-29
@azz: you forgot to put GNOME in between Metacity and the Xserver or alongside Metacity...

@H.E. Pennypacker: because that's the way Linux is built, that's the way Linux works. The reason why Windows doesn't need separate "restart" procedures is because in Windows, the kernel, graphical engine, desktop environment, and window manager is one big chunk of software. There's no clear and distinct separation between them. It is also the primary reason why when an application takes over the system and crashes, you would sometimes need to reboot in order to get a working system back. In Linux, you only need to terminate the offending part, whether it be a single application, or just the X server.

True, new users/beginners to Linux would probably be confused about these different parts in the beginning, but that's not an excuse to keep them in the dark for long. They don't need to acquire an in-depth technical know-how in order to understand how to restart X or why, or what layers or abstractions there are (kernel, X, DE, WM, etc). Some simple explanations tend to satisfy most people. If they want more info, they are welcome to research and ask.

---

### Post by az on 2006-06-29
[QUOTE=H.E. Pennypacker]azz, why are we subjected to all this stuff?  Most users probably don't care about all this stuff, and don't want to know.  
[/QUOTE]

I can't think of a time that I installed a stable version of ubuntu that I needed to restart or reconfigure the X server.  It all just worked.  That's how it is supposed to be for everyone.

Now, if you want to play around with Xgl and other things you will end up doing that (command line stuff) because it is the best way to tweak the system - you use the command line and get down and dirty with the OS.

You don't have to (usually, but considering many linux hardware drivers are reverse-engineered, it's pretty impressive).  But you can if you want to.

Also remember that Unix has a great heritage as a server platform and uptime is an important factor.  Even windows servers need to be rebooted regularly.  Not so for linux servers.

---

### Post by az on 2006-06-29
[QUOTE=Fenyx]@azz: you forgot to put GNOME in between Metacity and the Xserver or alongside Metacity...

[/QUOTE]

I will train harder....

*bows*

---

### Post by Jucato on 2006-06-29
[QUOTE=azz]I will train harder....

*bows*[/QUOTE]

I hope you didn't take offense on my little correction. :D

You also need to restart X if
1. you need to install the non-free video drivers, like nvidia-glx
2. everything graphical freezes, and the only thing that works is the keyboard

But I think that's covered by "and other things you will end up doing..." :D

---

### Post by 23meg on 2006-06-29
> **H.E. Pennypacker]azz, why are we subjected to all this stuff?  Most users probably don't care about all this stuff, and don't want to know.  [/quote]Someone who cared but lacked the knowledge and wanted to know started this thread, in the beginner talk section.  > With every different set of instructions, you have to restart this and that. You either (rarely) have to restart your computer, (usually) restart X or (very very rarely) restart a certain service, none of which is hard to do or confusing. > It'd be a lot easier if one button that said "restart" would cover everything.  Well, that button would restart the computer, but its better than having to find out what all these different parts of  Linux are. You're given a system where you almost never have to totally restart your computer, where all you have to do is restart a certain piece of software (X) with a simple key combination, and you're complaining about this... When you're required to restart X, and don't care to know what X is, just hit Ctrl+Alt+Backspace. If you care, look it up in Wikipedia or start a thread to ask about it, like the original poster did. > It takes less time to restart your computer than having to read what X, Gnome, Metacity, and everything else is.  You don't have to know what they are, thanks to the people who know what they are and developed them for you and support them for you said:**
> Windows never tells you to restart this and that.  It will just tell you to restart the computer, which is a pain, but probably not as much of a main as reading things.For anyone literate, reading a few lines about the very basics of how your operating system works never hurts and is never very hard to do. If it's a pain, you shouldn't be using a computer, simple as that; you can't anyway.

I wouldn't do hang gliding without learning some of the basics of aerodynamics, but I don't have to write a thesis on aerodynamics in order to be able to hang glide, thanks to a few quick lessons from my instructor. I wouldn't handle a weapon without knowing what the security lock does. I wouldn't attempt putting out a fire without knowing that fire is hot.

I don't mean to sound harsh, this is just exactly what I think about this matter and I can't put it any other way so please don't take offense.

---

### Post by nudnik on 2006-06-29
Azz wrote: 

"Now, if you want to play around with Xgl and other things you will end up doing that (command line stuff) because it is the best way to tweak the system - you use the command line and get down and dirty with the OS."

Yes, Xgl we like, verily, it biteth not. O:)

---

### Post by H.E. Pennypacker on 2006-06-30
23meg, I was only pointing out that Linux users are introduced to possibly more than they may want to know.  As for myself, I do a lot of reading, and I don't mind reading up on X, and my point was to have everything simplified by making it one thing.

You are right that most changes don't require restarting of anything.  I was only talking about those instructions that did require restart.  As you said, however, Linux is better in that you don't have to restart the entire system. That's definitely a plus.

The issue is whether beginners should have to learn about X, Gnome, etc.  I am not saying they shouldn't have to become developers (meaning they would have to know a lot).  All I am saying is whether they should be subjected to this at all.  I assume you don't go to your doctor's office so that he/she can give you a 600-page book on how to cure yourself.  They boil things down so that we may understand their language.  Like I said, it's all about boiling things down.

---

### Post by Jucato on 2006-06-30
[QUOTE=H.E. Pennypacker]23meg, I was only pointing out that Linux users are introduced to possibly more than they may want to know.[/QUOTE]
What users sometimes don't *want* to know are the things that they sometimes *need* to know. 

> The issue is whether beginners should have to learn about X, Gnome, etc.  I am not saying they shouldn't have to become developers (meaning they would have to know a lot).  All I am saying is whether they should be subjected to this at all.  I assume you don't go to your doctor's office so that he/she can give you a 600-page book on how to cure yourself.  They boil things down so that we may understand their language.  Like I said, it's all about boiling things down.
You don't have to study a 600-page book on how to cure yourself, otherwise you wouldn't need to go to the doctor. But then again, while it's not an absolute necessity (or sometimes it is), it pays to know your basic "first aid" stuff, right?

Windows has pretty much done a good job of shielding the regular user from details. But it has gone too far that the regular user usually ends up not knowing anything at all, except to point and click. While a regular user certainly doesn't need to know about how the X server communicates with the clients, or how GNOME communicates with the different apps, he/she certainly must know (or be taught) about certain *essential* parts of his/her system, that the OS has a kernel, X server, DE, and WM, some of which do not need to be restarted in order to solve a problem. 

Of course, people would have to communicate these facts on a level suited for the one asking the question. Also, when people ask for information, we don't tell them "Oh, all you need to know is that Ctrl+Alt+Backspace restarts X. Period. Anything else is bound to confuse a new user like you." (Of course, that's not what you literally meant). Besides, the OP did specifically ask for what X was, so it's only proper that we give him/her the information he/she asks for. Now, if he only asked how to restart the X server, then giving him more than what he needs to know at that time might be more confusing. It's on a case to case basis, really.

---

### Post by 23meg on 2006-06-30
> Linux users are introduced to possibly more than they may want to know.> All I am saying is whether they should be subjected to this at all.Examples? This thread isn't a valid example of your case. And how is it any different for equally underinformed Windows users when they run into problems and ask for help? Doesn't a Windows user get introduced to lots of terms they may not know when they have to fix something beyond their reach? Does the average Windows user know what HKEY_LOCAL_MACHINE in the registry is, or how System Restore works and where it stores its backups? 

The only difference might be that Linux users are more eager to help and since everything in Linux distros is modular, open and well documented, can give some extra info that may help put things in context. Here azz's reply does exactly that; the OP didn't ask for info about how X and GNOME relate and interact, but the assumption here is that a new Ubuntu user can't practically understand what X is without knowing how it relates to a desktop environment. If we were not to give them any extra info but only and only info regarding what X is, it would have to be a RTFM kind of reply.
> 
I assume you don't go to your doctor's office so that he/she can give you a 600-page book on how to cure yourself. They boil things down so that we may understand their language. Like I said, it's all about boiling things down.The folks here are very good at boiling things down for beginners. If this weren't the case, the first and only reply to this thread would be ```
man x 
```

---

