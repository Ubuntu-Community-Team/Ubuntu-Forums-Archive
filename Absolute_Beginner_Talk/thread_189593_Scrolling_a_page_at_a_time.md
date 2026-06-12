---
title: "Scrolling a page at a time"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by royirby on 2006-06-05
So.. I've read a load of threads on getting the extra mouse buttons to emulate browser forward/backward functions... but one of the things I've been doing for years in windows is having the scroll wheel emulate the page-up / page-dn keys (scrolling a page at a time).

I've got a basic intellimouse w/ NO extra buttons (left, middle, scroll, so 5 buttons to X).

Any ideas on how to fix this little problem?

tia.

---

### Post by royirby on 2006-06-13
<boink!>

---

### Post by aysiu on 2006-06-13
So what do you want to have happen?

You have a mouse that has two buttons. How is it that you want to scroll...?

---

### Post by royirby on 2006-06-13
I have MS Wireless Optical usb mouse connected thru a ps2-usb adaptor (also thru a ps2 kvm).  It's a basic 2 button wheel mouse (no side buttons).  I can certainly move the mouse to a usb port if necessary, but would prefer to keep it ps2 to keep the kvm in play.

I just want to get the wheel setup to emulate a pageup / pagedown instead of line-by-line or smooth scrolling.... regardless of the app... firefox, nautilus, etc.

So far, this is my main stumbling block in the Windows->Ubuntu migration... everything else has gone quite smoothly.

---

### Post by Denis on 2006-06-13
As a starting point. I think it is possible to let mouse buttons emulate page up and down. 

On the forum you will find lots of threads on how to emulate alt-left with your mouse (to go back in nautilus). I think the same method can be used to map "page up" to button x. 

check out this thread e.g.: [http://ubuntuforums.org/showthread.php?t=195659&highlight=back+forward+nautilus](http://ubuntuforums.org/showthread.php?t=195659&highlight=back+forward+nautilus)

---

### Post by aysiu on 2006-06-13
So it does have a scroll wheel? It looks something like this?

In KDE, you have the option to scroll as many as 12 lines at a time per click of the scroll wheel, but it doesn't have a page-up/page-down feature.

I'm pretty sure it can't be changed in Gnome without a helper application.

The question is--what is the helper application? Let me poke around and see if I can find anything.

**Edit**: Through Google and Synaptic, I'm not finding much. The most promising package in Synaptic is *mouseemu*. You might want to see what that does.

---

### Post by royirby on 2006-06-13
It's not quite THAT old-skool, but button-and-wheel-wise, yeah, like that.  ;)

From what I've read, I'll likely need some middleware to intercept the button events in question (wheel up, wheel down, wheel button) and replace them w/ keyboard events (page up, page down, and dbl-click).

I'll check out that link Denis.  It's likely one I've already skimmed over (i've been searching/reading here for a while).

--
yes, it looks like I should be able to use xbkvd to get the pageup/pagedn functionality... I'll give it a try tonite.... next will be getting the wheel-press to do a double-click.

---

