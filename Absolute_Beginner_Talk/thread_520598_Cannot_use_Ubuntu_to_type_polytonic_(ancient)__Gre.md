---
title: "Cannot use Ubuntu to type polytonic (ancient)  Greek anymore"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by tico on 2007-08-08
Well,

I was a very happy Ubuntu user till some days ago (even if it doesn't recognize my Canon Lide 500F scanner - at least for the time being). I don't remember how, but I had set up Ubuntu to type polytonic Greek perfectly. But my Ubuntu was a bit "slow", since I had installed KDE and Xfce4. So I've decided to make a clean install of Xubuntu. I've tried many times (installing and reinstalling) to configure polytonic Greek again, but no success. So I've decided to make a new clean install of Gnome (some users say that Ubuntu is optimized to run with Gnome). I still cannot type polytonic Greek (I'm using Openoffice). Here is what I've tried:

1. installed language support for Greek (sudo aptitude update && sudo aptitude install language-support-el)

Doesn't work.

2. in terminal, I've done: export GTK_IM_MODULE-xim

I could type some symbols (tilde, subscript iota, grave and acute accents), but could never type breathings (dasía/psíli - spiritus asper/lenis). It simply doesn't work.

Since I could type it properly before, could someone give some help to solve this problem? I need to type a lot of polytonic Greek and have spent the last four days trying to fix this. I'd like to continue to use Ubuntu, but I need to fix this.

Thanks a lot.

---

### Post by simosx on 2007-08-08
I blogged about this at
[http://simos.info/blog/archives/639](http://simos.info/blog/archives/639)

I hope it helps.

---

### Post by Al3xK3aton on 2007-08-08
Open up an art application, and draw out the symbols you need. Just copy these symbols into everything you need them in.

---

### Post by simosx on 2007-08-08
It's a bit more complicated than using an art application to write Greek Polytonic.

---

### Post by Al3xK3aton on 2007-08-08
Why can't you draw Greek polytonic with an art application? Do you not know how to draw?

---

### Post by tico on 2007-08-08
> **simosx said:**
> I blogged about this at
[http://simos.info/blog/archives/639](http://simos.info/blog/archives/639)

I hope it helps.

I'll try this later and will post the result here. Thanks for helping.

to Al3xK3aton,

Thanks for your answer, but it would be easier (even if not practical, and therefore not useful, to do this through "insert special character". But since I need to type a lot of polytonic Greek, this is out of question. And I could type it one week ago, in my ancient Ubuntu install.

Thanks.

---

### Post by Al3xK3aton on 2007-08-08
If it worked before, then just roll back to a backup you had of when it worked.

---

### Post by oilchangeguy on 2007-08-08
the user has two threads on the same subject:
[http://ubuntuforums.org/showthread.php?t=519117](http://ubuntuforums.org/showthread.php?t=519117)
can a mod please merge them?

---

### Post by tico on 2007-08-10
simosx,

Thanks for your help. I've read your blog and tried two of your tips. Here are the results:

Tip one: You can edit /usr/share/X11/locale/compose.dir so that for your locale, the compose file is the Greek one, /usr/share/X11/locale/el_GR.UTF-8/Compose.

RESULT: polytonic Greek works fine, but accents for other languages that use the Latin alphabet (characters like á, é, ê, ã, õ etc.) don't work.

Tip two: You can edit the Greek compose file, take the Greek Polytonic section and update the Greek Polytonic section of en_US.UTF-8/Compose.

Worked perfectly.

[COLOR="Red"]**BUT there's another solution a little bit easier, I think**[/COLOR]. This solution was kindly given to me by Jan Willem Stumpel ([http://www.jw-stumpel.nl/](http://www.jw-stumpel.nl/)) and is similar (but easier) to the second tip. Here's his answer/solution:

I cleared all the problems with the breathing signs by becoming root and
editing the /usr/share/X11/locale/en_US.UTF-8/Compose file. I
replaced everywhere

   U10000313 by U0313
   U10000314 by U0314

and restarted X. [end of quotation]

This works fine. Just replace U10000313 by U0313 and U10000314 by U0314 in the Compose file and it will work.

What do you think of this way, simosx? Let me know.

Thanks once more for you help.


After having updated to Hardy beta, I couldn't type dasia and psili (spiritus) anymore. So I've needed to make the following change (I've found this in Ubuntu's bugs.launchpad.net, Bug #21637):

> It seems to be a bug in the greek layout file in /etc/X11/xkb/symbols/gr. Following the hint in [http://www.jw-stumpel.nl/stestu.html#T6.5.3](http://www.jw-stumpel.nl/stestu.html#T6.5.3) I changed the lines
key <AC10> { [ dead_acute, dead_horn ] };
key <AC11> { [ dead_grave, dead_ogonek ] };
 to
key <AC10> { [ dead_acute, U0313 ] };
key <AC11> { [ dead_grave, U0314 ] };
and writing psili and dasia is working again.

It works fine again.

---

### Post by simosx on 2007-08-10
tico,
Many thanks for the feedback.
The choice you took (from jw-stumpel.nl) works and is good, and you get good precomposed characters for Greek Polytonic as you did before. However, this area is bound to change in subsequent versions of Linux.

My personal interest is to solve the problem "upstream" (where the compose files come from, at X.org) so that it works by default in all distributions.

The compose file (en_US.UTF-8/Compose) can be fixed so that everyone is happy. However, there is no definite maintainer as far as I know. Which is sad because most tasks is simple text processing.

---

### Post by eborigene on 2007-11-10
> **tico said:**
> simosx,

Thanks for your help. I've read your blog and tried two of your tips. Here are the results:

Tip one: You can edit /usr/share/X11/locale/compose.dir so that for your locale, the compose file is the Greek one, /usr/share/X11/locale/el_GR.UTF-8/Compose.

RESULT: polytonic Greek works fine, but accents for other languages that use the Latin alphabet (characters like á, é, ê, ã, õ etc.) don't work.

Tip two: You can edit the Greek compose file, take the Greek Polytonic section and update the Greek Polytonic section of en_US.UTF-8/Compose.

Worked perfectly.

[COLOR="Red"]**BUT there's another solution a little bit easier, I think**[/COLOR]. This solution was kindly given to me by Jan Willem Stumpel ([http://www.jw-stumpel.nl/](http://www.jw-stumpel.nl/)) and is similar (but easier) to the second tip. Here's his answer/solution:

I cleared all the problems with the breathing signs by becoming root and
editing the /usr/share/X11/locale/en_US.UTF-8/Compose file. I
replaced everywhere

   U10000313 by U0313
   U10000314 by U0314

and restarted X. [end of quotation]

This works fine. Just replace U10000313 by U0313 and U10000314 by U0314 in the Compose file and it will work.

What do you think of this way, simosx? Let me know.

Thanks once more for you help.

Actually in my compose file U10000313 **is already replaced** by U0313, Still I can't write polytonic in gedit.
By the way what is the <Multi-key> mentioned in the Compose file (sorry if this question is too naif)
Thanks
eborigene

---

### Post by simosx on 2007-11-11
> **eborigene said:**
> Actually in my compose file U10000313 **is already replaced** by U0313, Still I can't write polytonic in gedit.
By the way what is the <Multi-key> mentioned in the Compose file (sorry if this question is too naif)
Thanks
eborigene

Multi-key (also called "Compose key") is the name of a special key that can be used for special compose sequences. If you use GNOME, go to the Keyboard Preferences, at the Layout Options, and you can enable it. Typical value is Right-Menu. By default it is not active.

To fix polytonic for now, see 
[http://www.jw-stumpel.nl/stestu](http://www.jw-stumpel.nl/stestu)
I hope it gets sorted before the next Ubuntu. 
From the page above you need to do two things, 1) set GTK_IM_MODULE to "xim" and 2) make a small change to the configuration files (if required).

---

### Post by eborigene on 2007-11-14
I have tried to but without success. To set GTK_IM to Xim I suppose it is enough to right clik the mouse and choose the X input method (in gedit). As to the configuration files I don't know wich one(s) you mean.
I have tried other methods the only one working so far is the OpenOffice extension Thessalonika (though I don't know how to type an apostrophe). I have tried Cgreek to write with emacs but didn't manage to install it.
Thank you very much
eborigene

---

### Post by nightfrost on 2008-02-02
Just wanted to hop on this thread. I've been having problems with having polytonic greek characters working properly since I started using linux a few years back. 

I don't understand why the X guys don't just fix this. I mean it's not terribly hard to fix upstream, is it?

---

### Post by Cipher Highwind on 2008-03-21
Has anyone gotten this to work on 7,1?  I'm having the same problem, but know nothing about Linux.  Is there a walkthrough that is known to work?

---

### Post by simosx on 2008-03-24
> **Cipher Highwind said:**
> Has anyone gotten this to work on 7,1?  I'm having the same problem, but know nothing about Linux.  Is there a walkthrough that is known to work?

Other people (new to Linux) reported that the page
[http://simos.info/blog/2007/08/08/cannot-write-greek-polytonic-in-linux/](http://simos.info/blog/2007/08/08/cannot-write-greek-polytonic-in-linux/)
helped them in getting Ubuntu 7.10 working with Greek Polytonic.

Greek Polytonic will work out-of-the-box in Ubuntu 8.10 :guitar:

---

### Post by nightfrost on 2008-03-24
> **simosx said:**
> 
Greek Polytonic will work out-of-the-box in Ubuntu 8.10 :guitar:

Glad to hear! What exactly will accomplish this? Changes upstream, or ubuntu-specifics? 

A bit off topic, I get the feeling that most everything is kind of shaking now, what with the state of xorg/kde4/gvfs/NM 0.7, etc. It's like big things are happening everywhere and they're not quite done. Hopefully everything will be settled and dandy by the time of 8.10 (if the peak oil hasn't hit us hard by then!).

---

### Post by simosx on 2008-03-30
> **nightfrost said:**
> Glad to hear! What exactly will accomplish this? Changes upstream, or ubuntu-specifics?

It is an upstream feature that solves the problem to the core. In the GTK+ library, at GNOME. 

> **nightfrost said:**
> A bit off topic, I get the feeling that most everything is kind of shaking now, what with the state of xorg/kde4/gvfs/NM 0.7, etc. It's like big things are happening everywhere and they're not quite done. Hopefully everything will be settled and dandy by the time of 8.10 (if the peak oil hasn't hit us hard by then!).

All fronts are progressing which is good. Apart from programming, there is need for testing. If you have interest in testing the new functionality (writing Greek Polytonic out of the box in Ubuntu now), you can read on at 
[http://simos.info/blog/archives/661](http://simos.info/blog/archives/661)

---

