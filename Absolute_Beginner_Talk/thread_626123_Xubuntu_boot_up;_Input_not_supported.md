---
title: "Xubuntu boot up; Input not supported"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-11-28
During boot up of Xubuntu I get a message on the screen which says Input not supported. This little msg is in a box that floats about the screen which is otherwise black. Loading is still taking place and if I leave it alone long enough the standard desktop appears and all is well.

Is there any way of correcting/removing what seems like a fault at the earlier stage?

Kindest Regards

Laidback

---

### Post by Arthur Archnix on 2007-11-28
It just says input not supported? Not anything about what kind of input?

I'd try two things. First I'd unplug everything but mouse and keyboard from computer and reboot. Then I'd plug things back in until the error message occurs.

Second, if I can't get rid of the error message that way I'd take a look in my xorg.conf file (/etc/X11/xorg.conf) and see if I've accidentally enabled wacom input or added some other strange input device I don't have.

Last, as soon as my computer boots and I get a terminal I switch to a terminal and type 
```
dmesg
```
and post that back here, oh and I'd be sure to wrap all that long output in "code" tags. ;)

---

### Post by laidback on 2007-11-29
Thanks for reply. I'll have a go at that.

---

### Post by mustava on 2008-02-01
Hi guys, I also get this message during boot of 7.10. 
I think its something to do with the fact I'm using a LCD monitor and its picking up something it doesn't like.
May be a good idea to plumb up a CRT but I don't have one any more, but if someone can do this it may answer this mystery.

Oops Mustava!

---

