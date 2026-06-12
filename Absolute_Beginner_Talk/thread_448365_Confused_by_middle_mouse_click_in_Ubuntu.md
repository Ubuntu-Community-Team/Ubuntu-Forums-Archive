---
title: "Confused by middle mouse click in Ubuntu"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-05-19
This is a small thing that's been driving me up the wall...

In Windoze, I had Firefox set up using the Autocopy extension to copy highlighted text, and then when I wanted to paste it, I would click my middle mouse button.

That's where I'm coming from. Highlight = Copy. Middle-click = Paste. And only in Firefox.

Now, in Ubuntu, I try to use my middle-click to paste things, and it seems to work in all programs, not just Firefox. Except it doesn't always paste what I expect it to paste. So, things must work differently.

Someone in another thread said in passing something about in Unix they set it up so that you use middle-click to Copy *and* Paste. That made me think that could be what's causing the confusion in my mind.

I disabled Autocopy in Firefox in case that conflicts with the normal middle-click behaviour, which would be even more confusing.

But I still can't quite figure out how it works.

Could someone please explain to me how to copy and paste using the middle mouse button? Please explain as though you were teaching a four year old, because I have to un-learn my old ways as well as learn new ones.

Thanks!
Trisha

---

### Post by jordanmthomas on 2007-05-19
Middle clicking pastes the last text you selected with your mouse.

Copy and paste kinda sucks.  If you close the program you copied (as in Ctrl-c) you lose the data in the buffer.  However, what is in your ctrl-c copy is not necessarily the same as the middle click buffer.

...like that made any sense...
I can try and explain again if what I said didn't make a lick of sense.  Basically, you have two different copy and pastes....selecting text is one way of copying, and ctrl-c is another, totally unrelated to the first.

---

### Post by trishacupra on 2007-05-19
Hmmmm. Is there a way to prevent middle-click from copying stuff in text boxes? Like, if I want to copy and paste something from a web page into the search bar or location bar, if I copy by highlighting something, then select what's in the bar to delete it, it then copies what's in the bar and I can't paste what I wanted to. I would have to delete what's in the bar first, so it's blank when I go to paste in it, right?

Can this stuff be configured in a control panel somewhere?

---

### Post by jordanmthomas on 2007-05-19
I don't think there's an easy way to turn it off.  It's not Gnome that does it..it's the X Windows System.  

To make firefox's address bar work by clicking and then middle clicking, you can do this though:

Open a new tab, "about:config", change browser.urlbar.clickSelectsAll to true.

I don't know how to turn it off completely or for the search bar though, maybe you'll have better luck.  ;)

---

### Post by Zootropo on 2007-05-19
> **jordanmthomas said:**
> Copy and paste kinda sucks.  If you close the program you copied (as in Ctrl-c) you lose the data in the buffer.  However, what is in your ctrl-c copy is not necessarily the same as the middle click buffer.

Actually that's a great thing, because you are not using more memory just to store the things you want to copy. You only have a pointer to the zone of memory you just copied and, of course, if the program closes that memory is cleaned.

If you want to be able to retain the data you copied once the program closes, you can use klipper or glipper.

More info (spanish): [http://mundogeek.net/archivos/2007/05/09/glipper-el-portapapeles-en-linux/](http://mundogeek.net/archivos/2007/05/09/glipper-el-portapapeles-en-linux/)

---

### Post by jordanmthomas on 2007-05-19
I agree it's a good thing...it just sucks for people who aren't used to it.  I never use copy and paste and just use the middle click.

---

### Post by bumpkin on 2007-06-03
I personally would like to find a way to turn it off as I use the middle mouse button to scroll and the mouse I have (an old microsoft mouse) has a sensitive middle button and I wind up accidentally copying text when I scroll. More than once I've screwed up a python script as I scroll through the file. 

I would like to turn it off and only scroll using the middle mouse button. Hope someone can enlighten me as to how to turn it off.

---

### Post by moeFinley on 2007-06-05
> **bumpkin said:**
> I would like to turn it off and only scroll using the middle mouse button. Hope someone can enlighten me as to how to turn it off.

I'd like to be able to do this too.  I have a latop and the best way to scroll is to use the middle mouse button.  If anyone knows how it can be done or even if it's possible I'd be very greatfull!  Thanks  :D

---

### Post by Nekiruhs on 2007-06-05
As a previous poster said, Its pretty hard to configure/disable the middle mouse click thing because its not part of gnome, kde, xfce. Its part of the X Window System.

---

### Post by Rocket2DMn on 2007-06-05
It can be very useful in a terminal.

---

