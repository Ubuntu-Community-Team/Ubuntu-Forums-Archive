---
title: "Shift-backspace logs me out"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Diversion on 2007-05-06
I'm having the problem that I keep getting logged out when I accidently press shift-backspace
I've looked under key bindings but it says log out is disabled as a shortcut.

Any help?

---

### Post by macdo on 2007-05-06
That's not a bug :-)
Shift-Backspace restarts the X Server. 

Here are instructions to change the key bindings:

[http://princ3.wordpress.com/2006/10/04/disable-shift-backspace-logout-in-xgl-and-enable-altgr/]("http://princ3.wordpress.com/2006/10/04/disable-shift-backspace-logout-in-xgl-and-enable-altgr/")

You occasionally really need that combination...

macdo

---

### Post by Diversion on 2007-05-06
Thank you, i tend to press it when using Amsn or when trying to type a message here.

---

### Post by Diversion on 2007-05-08
Worked like a charm when I used it, but I keep having to put it in every time I log in. what do I need to do to keep it disabled? I followed all the instructions in the guide you gave, but that didn't keep it from coming back..

---

### Post by orb9220 on 2007-05-08
And as stated in the article

> And because i am a lazy person and dont want to type that over and over again to load it on startup i put both in my ~/.Xmodmap file:

echo &#8216;keycode 22 = BackSpace BackSpace&#8216; >> ~/.Xmodmap
echo &#8216;keycode 113 = Mode_switch&#8217; >> ~/.Xmodmap


Did you?

 i am a lazy person and dont want to type that over and over again to load it on startup i put both in my ~/.Xmodmap file:

echo &#8216;keycode 22 = BackSpace BackSpace&#8216; >> ~/.Xmodmap
echo &#8216;keycode 113 = Mode_switch&#8217; >> ~/.Xmodmap

---

### Post by Diversion on 2007-06-12
Did that, and when I look in my Xmodmap it's in there as following:

‘keycode 22 = BackSpace BackSpace‘
‘keycode 113 = Mode_switch’

problem is I get this error when opening ~/.Xmodmap with gedit:
/home/diversion/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant

Could this be the reason it ain't working?

---

