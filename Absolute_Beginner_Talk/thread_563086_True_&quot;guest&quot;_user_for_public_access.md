---
title: "True &quot;guest&quot; user for public access"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by michael37 on 2007-09-29
I need to create a very limited yet usable pubic access to my computer to allow guests Internet access (primarily, Firefox).  I have read several posts about "guest" users for Ubuntu, but they didn't answer the questions I was looking for.  I used to have this working with Windows XP, so this is really a migration question.

My requirements are:

[LIST=1]
[*]I (as myself) am logged in to this computer all the time.  Guests may access the computer at any time, with or without my knowledge.  I need a screensaver that will automatically lock the screen when I am idle and permit guest users using public entry without my supervision.
[*]I need to make guest user very obvious in the gnome login screen?
[*]I prefer to have guest user passwordless.  There is no security for this user anyway.  For example, Firefox preferences will be set up to prohibit remembering user passwords.
[*]I prefer to know what users tried to do on my computer.  Not necessarily to the degree of the keyboard logger, but general knowledge of which applications they ran and which files they accessed/created/wrote.
[*](know how to do) I need to disable guest login from ssh  or any other remote access
[*](know how to do) I need to disable guest user from sudo
[/LIST]

What's the best way to accomplish it?

---

### Post by Sef on 2007-09-30
> I (as myself) am logged in to this computer all the time. Guests may access the computer at any time, with or without my knowledge. I need a screensaver that will automatically lock the screen when I am idle and permit guest users using public entry without my supervision.

System > Preferences > Screensaver

> I need to make guest user very obvious in the gnome login screen?
> I prefer to have guest user passwordless. There is no security for this user anyway. For example, Firefox preferences will be set up to prohibit remembering user passwords.

For both:  System > Administration > Login Window 

> (know how to do) I need to disable guest user from sudo

New users do not have admin rights by default.

---

### Post by michael37 on 2007-09-30
> **Sef said:**
> System > Preferences > Screensaver
I would disagree that "switch user" button is an obvious choice.  Is there anything else available?   Can I make gnome-screensaver point to login screen instead of prompting me with a separate screen?

> **Sef said:**
> For both:  System > Administration > Login Window 
Took me five minutes to understand what you meant.  For everyone else, click on Local tab and switch from default "Human" to "Human list"

---

### Post by michael37 on 2007-09-30
[QUOTE=Sef][QUOTE=michael37]I prefer to have guest user passwordless. There is no security for this user anyway. For example, Firefox preferences will be set up to prohibit remembering user passwords.[/quote]
For both: System > Administration > Login Window[/quote]

I found nothing for passwordless access for guest in the Login Window.

In Users and Groups, I can't set empty password for guest.

---

