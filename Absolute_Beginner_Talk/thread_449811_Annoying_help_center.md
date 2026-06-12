---
title: "Annoying help center"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by loupy on 2007-05-20
I just did a fresh install of 7.04 and everytime I log in the Ubuntu Help Center automatically starts.  How can I disable this?  I've searched everywhere and have not found an answer - please help!

---

### Post by jvc26 on 2007-05-20
Um - perhaps System -> Preferences -> Sessions -> Startup manager and remove it from the list if its there.
Il

---

### Post by loupy on 2007-05-20
Ummm - I already searched there, gconf, google, and these forums prior to posting - it does not appear anywhere I can find.  I try to resolve my problems by searching before posting for numerous reasons but the #1 reason is responses with attitude like yours.

What's happened to this forum?  It used to be a real friendly place a year and a half ago, where people were glad to help others.  I sure hope you are the exception and not the norm.

---

### Post by overdrank on 2007-05-20
> **loupy said:**
> Ummm - I already searched there, gconf, google, and these forums prior to posting - it does not appear anywhere I can find.  I try to resolve my problems by searching before posting for numerous reasons but the #1 reason is responses with attitude like yours.

What's happened to this forum?  It used to be a real friendly place a year and a half ago, where people were glad to help others.  I sure hope you are the exception and not the norm.

Hi and welcome but I have to ask what is so bad about this response

Um - perhaps System -> Preferences -> Sessions -> Startup manager and remove it from the list if its there.
Il

??:(

---

### Post by loupy on 2007-05-20
The "um - perhaps" is what got me.  I am not new to linux, but thought this was probably something simple so posted it in the Beginner section.  If this indeed is the section to welcome newcomers and converts from M$ (or other OS) - I think it would've been more appropriate to begin it with "Have you tried ...."  it's a semantical issue and as voice inflections are not carried over in posts it is easy to misconstrue what one may be saying (and I may have misconstrued his intention as well and if I did for that I apologize).

---

### Post by overdrank on 2007-05-20
> **loupy said:**
> The "um - perhaps" is what got me.  I am not new to linux, but thought this was probably something simple so posted it in the Beginner section.  If this indeed is the section to welcome newcomers and converts from M$ (or other OS) - I think it would've been more appropriate to begin it with "Have you tried ...."  it's a semantical issue and as voice inflections are not carried over in posts it is easy to misconstrue what one may be saying (and I may have misconstrued his intention as well and if I did for that I apologize).

Point taken. :popcorn:

---

### Post by RomeReactor on 2007-05-20
Hi. loupy, the Help Center is a program named Yelp: are you sure it's not in "System-->Preferences-->Sessions-->Startup Programs"?

---

### Post by loupy on 2007-05-20
RomeReactor - I checked again just to be sure and it's not there :( .  I'm at a loss as I have looked everywhere I can think of for the reference to yelp and cannot find it.

---

### Post by RomeReactor on 2007-05-20
That *is* odd; in "Sessions-->Session Options", is the "Automatically save changes to session" option checked? If it is, uncheck it and restart Ubuntu and see if it still pops up after you login. At the moment, that's all I can think of, sorry.

---

### Post by loupy on 2007-05-20
I thought of that as well and just retried it - I'm about to pull out my last remaining hairs :D

---

### Post by mocha on 2007-06-13
I have this same problem on a fresh install of Feisty.  The help center and a Nautilus window of my home directory comes up after boot up.   I can't figure this out.

---

### Post by cofko on 2008-04-12
Hi, just to resolve this thread (I'm using Ubuntu 7.10):

fix it with Sessions; it is not shown in tab Startup Programs, but in next tab Current Session . Remove yelp and then in the next tab Session Options click "Remember currently running applications" . 

This takes the configuration in tab Current Session and stores it in {user}/.gnome2/session , which Session manager uses it to restore the saved session . 

For Nautilus browser i removed nautilus the same way but then I had to add it back like in this post [http://ubuntuforums.org/showthread.php?t=313471]("http://ubuntuforums.org/showthread.php?t=313471")
 and click again on  "Remember currently running applications" .

As I understand it, not all applications can be set to startup with sessions . For those that don't work  (like wine) you have to set it manually in tab Startup Programs .

---

### Post by loupy on 2008-04-15
I found out that the issue (for me anyways) is in the keyboard shortcuts.  For some reason the mousepad disable/enable button on my laptop is configured by default to launch the help browser.

You can disable it by going to System - Preferences - Keyboard Shortcuts - Desktop.

Click on Help Launch Browser and hit the delete key to disable it.

---

