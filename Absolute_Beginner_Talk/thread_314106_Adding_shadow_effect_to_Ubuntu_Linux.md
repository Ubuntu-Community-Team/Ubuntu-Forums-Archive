---
title: "Adding shadow effect to Ubuntu Linux"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by internetworld7 on 2006-12-07
Hello Linux community :D 

I'm loving the improvements of this 6.10 version! I'm very new to Linux and I was curious if I could add or enable a simple shadow effect to open widows and applications, similar to what you would see on Mac OSX or Windows Vista. I just thought a shadow background would really make this awesome. :p

---

### Post by 23meg on 2006-12-07
You can have that with Beryl and/or Compiz. If you mean just shadows around window borders, the composite extension + xcompmgr will also do.

---

### Post by internetworld7 on 2006-12-07
> **23meg said:**
> You can have that with Beryl and/or Compiz. If you mean just shadows around window borders, the composite extension + xcompmgr will also do.

Sorry, I'm still learning the Linux OS and much of the terminology is still like Greek to me. What is Beryl and Compiz? What is xcompmgr and how do I find these programs? Do I have to install them from a seperate source or are they already included in Ubuntu? :-k

Oh and yes, I just would like shadows around the window borders.

---

### Post by 23meg on 2006-12-07
> Sorry, I'm still learning the Linux OS and much of the terminology is still like Greek to me. What is Beryl and Compiz?When you see a term you're unfamiliar with, just look it up in Wikipedia.

[http://en.wikipedia.org/wiki/Beryl_%28window_manager%29](http://en.wikipedia.org/wiki/Beryl_%28window_manager%29)
[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

xcompmgr is a simpler compositing manager, but it isn't very stable and hasn't seen any development in a long time; you're probably better off with Compiz or Beryl. They too aren't stable, but they provide lots of more eye candy as well as other advantages. Check them out first. 

> Do I have to install them from a seperate source or are they already included in Ubuntu?
You have to install them separately. Start [here]("http://www.ubuntuforums.org/showthread.php?t=272104").

---

### Post by loell on 2006-12-07
if you like to install xcompmgr

just do this in the command line

```
sudo aptitude install xcompmgr
```

to autostart xcompmgr during gnome start up

go to

"system" menu --> preferences --> sessions

add this to "start up"

```
xcompmgr -f -F -c -I 1 -C
```

---

### Post by klato on 2006-12-07
> **internetworld7 said:**
> Hello Linux community :D 

I'm loving the improvements of this 6.10 version! I'm very new to Linux and I was curious if I could add or enable a simple shadow effect to open widows and applications, similar to what you would see on Mac OSX or Windows Vista. I just thought a shadow background would really make this awesome. :p

xcompmgr is quite slow (for me at least, barely usable), while Compiz is quite speedy and usable, with Beryl being slightly slower.

So in order I'd try:

Compiz, Beryl, xcompmgr

That being said, I think Beryl is probably the easiest to configure =)

---

### Post by loell on 2006-12-07
xcompmgr is just for fading and shadow effect , its quite fast for me , with one line configuration than compiz or beryl.

ofcourse desktop effects is well, useless.

---

### Post by Lord Darth Vader on 2006-12-10
If xcompmgr is slow for you, try this command line:
(before that make sure you have killed any running xcompmgr)

xcompmgr -cC -t-8 -l-8 -r5 -o0.85 

OR

xcompmgr -c -t-8 -l-8 -r9 -o0.95 

I personally prefer the second one though you can find your favorite by playing with options.
Have a look at my desktop: [http://ubuntuforums.org/gallery/showphoto.php?photo=4200&cat=2]("http://ubuntuforums.org/gallery/showphoto.php?photo=4200&cat=2")

---

