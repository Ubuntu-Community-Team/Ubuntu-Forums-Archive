---
title: "Ubuntu 7.10 keyboard stops responding in some gui applications"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by brightdragon on 2007-11-26
I'm running Ubuntu 7.10 on a  Lenovo T60 with a Centrino Duo CPU and an ATI graphics card. I consistently meet an annoying problem that the keyboard stops responding in applications such as firefox, thunderbird, pidgin etc occasionally. I haven't been able to figure out what event sequence triggers it, but it shouldn't be random. It seems that the following can reproduce the problem:

launch thunderbird;
ctrl-N create a window to compose a new email (window #1);
write something such as the recipient's address, subject, etc.;
before closing window #1, ctrl-N creates another new email window (window #2);
alt-table switches to window #1 --- all windows of thunderbird stop responding to the keyboard. The weird thing is that the combination of "alt-F4" still works;
Mouse is working during the entire procedure and once I restart thunderbird, it works again.

It seems OK if I always keep no more than one new email window.

I've met this problem with thunderbird, firefox, pidgin, tomboy notes and other applications with a gui. I haven't met this problem with xterm or the desktop environment (I'm using gnome).

Did anyone meet a similar problem before? I'm not sure what kind of information will help to diagnose the problem. :confused:

Any help is appreciated. Thanks!

--BD

---

### Post by spiderbatdad on 2007-11-26
sounds like your saying: If drive over 75 mph my steering wheel starts vibrating, just kidding. I've noticed a rare keyboard freeze up during gui apps since changing from fiesty to gutsy, but i haven't been able (nor tried) to intentionally duplicate the effect. I too use a thinkpad. T-30 with ATI card. I'm looking forward to Hardy.

---

### Post by brightdragon on 2007-11-26
Thanks for your reply! It's good to know that I'm not alone. My laptop was also upgraded from feisty to gutsy. Seems I have to live with this "feature" for a while --- good thing that commandline works for me most of the time :)

---

### Post by soichih on 2007-12-03
I am having almost identical issue with 7.10 on my Dell latitude d620 laptop.

I don't have thunderbird installed, but similar issue occurs on Evolution. This also happens on Firefox, Pidgin, File Browser, and others.. When this issue occurs, I have to stop all instances of the same application. For example, when firefox freezes up its keyboard, I have to find all Firefox running and kill all instances. 

I can recreate this issue almost always by using del.iciou.us plug in for Firefox browser. When I click TAG icon and tag a webpage, the keyboard will locks up on Firefox.

Please let me know if you find a solution to this issue.. This is very very annoying!!

---

### Post by soichih on 2007-12-03
Sorry, here is the correct steps to recreate this issue.

On Firefox, install Del.icio.us Firefox plugin from yahoo.

Open Del.iciou.us sidepane, and right click on bookmarks that are already tagged. Select properties on the context menu, then change the tag. 

Repeat changing the tag on other pages until keyboard will be locked.


With above procedure, I can recreate the keyboard lock up 100% of the time.

---

### Post by Sims2789 on 2007-12-03
I have a T61 and have never had this problem. In System -> Preferences -> Keyboard, My layout is set to "U.S. English" and my model is set to "Generic 105-key (Intl) PC" without the quotation marks. I wouldn't be surprised if we have the same or very similar keyboard, since the main difference between our laptops lies in the case and the processor, but otherwise they're similar.

---

### Post by soichih on 2007-12-03
I have my keyboard layout set to Generic 105-key (Intl) PC as well but it still hoses.. I also tried "Dell latitude series laptop" but didn't fix the issue.

---

### Post by brightdragon on 2007-12-03
I have the same keyboard setting as Sims2789. But it doesn't solve the problem :(. Yeah, it's extremely annoying and frustrating.

---

### Post by soichih on 2007-12-18
This issue is caused by SCIM bug. When the lock up occurs, I can un-lock it if I shutdown the SCIM. Also, if SCIM is not running, the lock up will never occurs. 

Where can I submit a bug report for SCIM?

---

### Post by mikeize on 2007-12-27
try this:

[http://samiux.wordpress.com/2007/11/06/scim-bug-fix-for-ubuntu-710/](http://samiux.wordpress.com/2007/11/06/scim-bug-fix-for-ubuntu-710/)

-mike

---

### Post by jjatria on 2008-05-13
i've encountered the same problems, and it has happened on a lot of different applications.

- in firefox, yakuake, openoffice and some others i can't remember right now, without me having been able to reproduce it.
- in inkscape, most of the times after i selected text.
- it also happens on every open gui application i've tried if, while i'm typing, the kopete pop-up "new contact online" notification comes up.
- on every application, i can fix it by either switching to another keyboard layout, or, on most cases, by minimizing and maximizing the window. in yakuake, changing session tabs also fixes it.
- the only application where switching keyboard layouts doesn't work is kopete, in which i have to switch to another conversation tab, or minimize/maximize the conversation window altogether.

i'm running hardy with kde 3.5 on a dell inspiron e1505.
i have skim running, so this could definitely be a scim bug (in fact, that was what i thought at first). but if it is, it's one hell of an annoying bug.

---

### Post by jjatria on 2008-05-13
wow.
this comes as a surprise.

i tried the fix mikeize said and ... it worked!!
so far so good, at least, and i tried the dreaded kopete pop-up notification and, hey, i'm still writing!

thanks!

---

