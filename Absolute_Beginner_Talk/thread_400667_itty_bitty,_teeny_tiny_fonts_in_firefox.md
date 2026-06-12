---
title: "itty bitty, teeny tiny fonts in firefox"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by rolypolycat on 2007-04-03
Hello!

I just installed ubuntu edgy eft from the iso on the downloads page. Everything is fine, except for the fonts in firefox.  Every web page I look at always loads-no exceptions- with tiny little fonts that are hardly readable. It's like the entire webpage is still in proportion, just shrunk to nothing. They're about the size of the normal "fine print" one finds at the bottom of a typical webpage. I have to hit Ctrl + at least 2, sometiimes 3 or more times for every webpage, just so I can read it. Needless to say, it makes websurfing very frustrating when I have to enlarge each page by hand.
I changed the font size in Preferences to 16 and 14; I switched to Bitstream Vera Sans; sans serif and monospace are 14 each; I made the minimum font size 14, and unchecked the button that lets web pages choose their fonts over mine; still no luck.  The system fonts are large and just the way i like them; it's only firefox that has the problems. In the SimplyMepis distro, the firefox fonts were normal, and I don't recall Breezy Badger having any firefox problems When I was trying it. Could it be a bug in this version of Ubuntu?
I appreciate any help anyone can give me. Thanks in advance!

---

### Post by Bachstelze on 2007-04-03
Set your fonts preferences in FF properly, in Edit > Preferences > Contents, click the Advanced button, [here](http://img153.imageshack.us/img153/3770/fffontsnq4.png)'s what it should look like. Also, it sometimes helps to do :

```
sudo apt-get install msttcorefonts gsfonts-x11
```

---

### Post by finferflu on 2007-04-03
> **HymnToLife said:**
> Set your fonts preferences in FF properly, in Edit > Preferences > Contents, click the Advanced button, [here](http://img153.imageshack.us/img153/3770/fffontsnq4.png)'s what it should look like. Also, it sometimes helps to do :

```
sudo apt-get install msttcorefonts gsfonts-x11
```
Yes, that's the solution, and you should adjust the Minimum font size to see any result ;)

---

### Post by FrancoNero on 2007-08-27
> **HymnToLife said:**
> Set your fonts preferences in FF properly, in Edit > Preferences > Contents, click the Advanced button, [here](http://img153.imageshack.us/img153/3770/fffontsnq4.png)'s what it should look like. 

thanks for that screenshot. I followed that screenshot (but chose 15 instead of 16. as a reference I used NYtimes' website, because lots of text) and DISABLED that sites could chose their own font....

not sure about thos font types you picked though, are those the ubuntu/ff defaults or those resemling WinXP the closest?

---

### Post by brainiac86 on 2008-03-01
Hey all,

I came to this post with a similar but different problem. Not only were my site fonts tiny, but the UI fonts were tiny too (ie. the menus, etc.)

I eventually found the fix here: [http://kmandla.wordpress.com/2008/01/13/howto-beat-firefoxs-ui-fonts-into-submission/](http://kmandla.wordpress.com/2008/01/13/howto-beat-firefoxs-ui-fonts-into-submission/)

Basically, this problem happens because Firefox can't interpret you xorg.conf file correctly.

The fix is:

[LIST=1]
[*]Open firefox.
[*]Go to the address "about:config"
[*]In the "Filter" box type "dpi"
[*]Set this to something like "75"
[*]Restart firefox
[/LIST]

If the fonts look good, you're done. If they're too big, set the DPI to a bigger number, if they're still too small set the DPI to a smaller number.

This fix increased both the website fonts and the UI fonts.

Cheers!

---

