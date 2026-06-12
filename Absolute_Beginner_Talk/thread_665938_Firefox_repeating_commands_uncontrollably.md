---
title: "Firefox repeating commands uncontrollably"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Offthedeepend on 2008-01-12
So I have this strange problem with firefox: I use short cut keys quite a lot and occasionally (not every time) when I use backspace or alt-leftarrow to return to a previous page, firefox continues repeating the command, scrolling back through all previous pages to the home page, and I can't stop it.  It's also occurred when I use ctrl-n to open a new window, and firefox kept opening new windows until it crashed the system.  

Anyone else had this experience or know what might be causing it?  It doesn't seem to be a sticky keyboard key.  Not sure if it is a firefox bug, it doesn't happen when I run firefox through windows, only when in ubuntu.  

I have a dual boot set up: WinXP and Ubuntu 7.10, but fairly new  to linux so not sure what extra info might help to diagnose this.

---

### Post by p_quarles on 2008-01-12
Okay, it doesn't happen in Windows, but does it happen in any other Ubuntu applications? Try using keyboard shortcuts in another app, and see if you can replicate the problem.

---

### Post by RomeReactor on 2008-01-12
Hi. You may want to run Firefox from the terminal to see if it leaves any messages there that could help diagnose the problem; open a terminal (Applications->Accessories->Terminal) and write or paste:
```
firefox %u
```
And please post any messages left in the terminal If Firefox keeps having this issue.

---

### Post by Offthedeepend on 2008-01-12
It hasn't happened with any other applications (although I most frequently ues shortcut keys in firefox).  

When I run from the terminal it opens fine.  No errors in the terminal yet, just in the browser itself: 'firefox can not find the server at www.%u.com"

---

### Post by p_quarles on 2008-01-12
> **Offthedeepend said:**
> It hasn't happened with any other applications (although I most frequently ues shortcut keys in firefox).  
Well, give it a shot, just to see what happens.

Here's my thinking: Ubuntu has built-in accessibility options, one of which (sticky keys) can be set to ignore keys that are pressed for long durations. This is designed primarily for people with neurological conditions, or who otherwise have slower reflexes. The effect you're seeing is definitely *not* how it's supposed to behave, but I'm just wondering if you're perhaps experiencing a bug related to one of those accessibility settings.

---

### Post by Wiebelhaus on 2008-01-12
I've seen this happen when using a KVM switch , if your using a KVM just hit any random key like the space bar and it'll stop.

---

### Post by RomeReactor on 2008-01-12
> **Offthedeepend said:**
> When I run from the terminal it opens fine.  No errors in the terminal yet, just in the browser itself: 'firefox can not find the server at www.%u.com"

Sorry about that; run it without the **%u**:
```
firefox
```
Try to replicate the problem and see if anything is left in the terminal.

---

### Post by Offthedeepend on 2008-01-12
> **sx66gns said:**
> I've seen this happen when using a KVM switch , if your using a KVM just hit any random key like the space bar and it'll stop.

Sorry - what's a KVM?

---

### Post by Linuxratty on 2008-01-12
With the last version of Firefox,Ive had this happen in Linux and in Windows.
In my case,Firefox would add several bookmarks of whatever page it was screwing up on. 
 i was told it was a problem with Firefox and the scroll button.

---

### Post by Offthedeepend on 2008-01-12
I'm on a Dell laptop with touchpad, so not the scroll button.  It happens when I use the keyboard shortcuts, not the touchpad.  

Can't stop the process with space bar, esc etc.    

It also happens when I have multiple tabs open, and use ctrl-w to close one, it closes them all one after each other.  

But of course, now when I'm trying to repeat the problem to see if anything turns up in the terminal, it's working fine..   Will post back if I get any error msgs next time it happens.  

Could also remove and re-install I guess.

---

### Post by Linuxratty on 2008-01-12
Ok, let us know then..

---

### Post by Wiebelhaus on 2008-01-13
> **Offthedeepend said:**
> Sorry - what's a KVM?




Keyborad Video Mouse , Allows you to run multiple computers from a single Keyboard , monitor & mouse. google search "KVM Switch" for pictures.

---

### Post by knattlhuber on 2008-02-19
> **Offthedeepend said:**
> So I have this strange problem with firefox: I use short cut keys quite a lot and occasionally (not every time) when I use backspace or alt-leftarrow to return to a previous page, firefox continues repeating the command, scrolling back through all previous pages to the home page, and I can't stop it.  It's also occurred when I use ctrl-n to open a new window, and firefox kept opening new windows until it crashed the system.  

Anyone else had this experience or know what might be causing it?  It doesn't seem to be a sticky keyboard key.  Not sure if it is a firefox bug, it doesn't happen when I run firefox through windows, only when in ubuntu.  

I have a dual boot set up: WinXP and Ubuntu 7.10, but fairly new  to linux so not sure what extra info might help to diagnose this.

I'm experiencing the same problem, both in Firefox (mostly with Ctrl + w) and in Evolution (with the Del key). The latter is especially unnerving as it may move 200 messages from Inbox to Trash faster than you can say 'Crap'.

Did you ever find out what caused your problem?

---

