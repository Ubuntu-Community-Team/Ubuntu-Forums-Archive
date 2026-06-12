---
title: "Divx movies won't play"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by cnico88 on 2008-03-05
I tried both mpeg and avi and they won't play in the regular media player. They open up and then close. I downloaded VLC and it just opens the file then closes. I have no clue to what's happening. Do I need extra codecs? I though VLC should handle divx just fine. Thanks

---

### Post by chewearn on 2008-03-06
Have you try this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by oedha on 2008-03-06
or...perhaps :==> [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by cnico88 on 2008-03-06
a user form another forum suggested this: "It might be compiz-fusion related - movies won't run under Compiz unless you install the i810 driver instead of the stock intel driver that you'll be running by default."

now my question is how do I upgrade the i810 driver? Thanks for the help guys.

---

### Post by smurphy_it on 2008-03-06
The i810 driver would be an intel driver which should be in the repositories.  On a pos MS machine at the moment so not so easy to look up.

In a terminal you could try sudo apt-get install i810

If you don't have an intel video card, I wouldn't bother.... you just need the right codecs installed to watch divx, xvid and avi.  While u r at it, you might want to install the DVD codecs for viewing dvd's if you haven't already.

---

### Post by cnico88 on 2008-03-06
> **smurphy_it said:**
> The i810 driver would be an intel driver which should be in the repositories.  On a pos MS machine at the moment so not so easy to look up.

In a terminal you could try sudo apt-get install i810

If you don't have an intel video card, I wouldn't bother.... you just need the right codecs installed to watch divx, xvid and avi.  While u r at it, you might want to install the DVD codecs for viewing dvd's if you haven't already.

I tried that command and it doesn't work, please get back to me when you get home, I would really appreciate it. Thanks

---

### Post by smurphy_it on 2008-03-07
I don't see an i810 video driver in the repositories.  The only i810 listed is one for toggling output between your laptop display and an external display like a crt or lcd.

The i915 is the Intel driver for Intel 800 and 900 series of video cards.  I still don't see how this would affect video playback, but if you wanted to install it, in a terminal just type
[COLOR="Orange"][I]
sudo apt-get install 915resolution[/I][/COLOR]

Or use your favorite package manager (like synaptic for example).
If you are using ubuntu, it's System, Administration, synaptic package manager

---

