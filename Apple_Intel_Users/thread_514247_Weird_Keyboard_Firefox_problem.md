---
title: "Weird Keyboard Firefox problem"
date: 2007-07-31
forum: Apple Intel Users
---

### Post by russo.mic on 2007-07-31
So, this just started a few days ago...

When I use my volume buttons (F5 and F6) with firefox open, firefox zooms the text bigger and smaller...

What the hell?  I don't really need the zoom, is there any way to disable it?  I can't seem to find anything on firefox forums or anything.  

Thanks in advance!

Russo

---

### Post by ronocdh on 2007-07-31
> **russo.mic said:**
> So, this just started a few days ago...

When I use my volume buttons (F5 and F6) with firefox open, firefox zooms the text bigger and smaller...

What the hell?  I don't really need the zoom, is there any way to disable it?  I can't seem to find anything on firefox forums or anything.  

Thanks in advance!

Russo
Try popping open "about:config" and searching for a zoom functionality. I have Web Developer installed, and it offers me the Z and X keys as zoom buttons. Maybe you have something else going on? At least, I don't believe that's a default functionality of Firefox....

---

### Post by russo.mic on 2007-07-31
Hmmm...I looked in there, what a rat's nest.  Hard to find anything, and the filter doesn't seem to work very well...

Anyway,  I didn't see anything of intrest.  Would lirc have anything to do with this?  this did start happening after an update as i'm thinking about it...

Russo

---

### Post by {{corona}} on 2007-07-31
do about:config in firefox and look under
 
**keyconfig.main.key_textZoomReduce**

and 

**keyconfig.main.xxx_key45_cmd_textZoomEnlarge**

there you should be able to change the keys bindings...

or you can also get the key modifier plugin called keyconfig and change it from there.

---

### Post by russo.mic on 2007-08-02
I don't seem to have those values in about:config...

Hmmm....

Just posting results: So, I just disabled lirc, and I was right.  first off, it wasn't just firefox, it was everything.  Nautilus, whatever.  zoom in and out.  Disabling lirc stops all the wierd behaviour.  

Time to learn a bit more about lirc I suppose.

Russo

---

### Post by Azathoth_ on 2007-08-02
Do you use the lircrc and inputlirc i posted some days ago???
It's normal then:
open a terminal and try: killall irxevent

Then, try turning up and down volume on firefox...

---

### Post by cyberdork33 on 2007-08-02
> **russo.mic said:**
> I don't seem to have those values in about:config...

me either, just for completeness

---

