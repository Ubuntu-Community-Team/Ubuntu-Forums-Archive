---
title: "Why gstreamer Totem?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by fjm03 on 2006-06-27
Why does 6.06 install gstreamer totem as a default?

I'd like to watch movies utilzing proprietary codec. At this point  I'm unwilling to uninstall gstreamer and replace it with xine because I don't understand the consequences.  Measure twice, cut once -  I'm a newbie to both linux and Ubuntu and have minimal skills with Terminal command syntax.

Is the process as simple as it appears utilizing Synaptic Package Manager or is there a catch 22, politcally or otherwise?

Thanks.

---

### Post by lawngn0mex on 2006-06-27
```

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

```

---

### Post by blackjack6.21.91 on 2006-06-27
I think most people find totem-xine to be less buggy than totem-gstreamer.  You can do what the guy ahead said and install some gstreamer codecs and see if that works for you.  But if you're not satisfied go ahead and get totem xine.  However, for general multimedia preparation, I would recommend BUMPS.  Go ahead and search for it on the forums if your interested.

---

### Post by lawngn0mex on 2006-06-27
I agree that totem-xine seems to work better in a lot of cases... I was just giving the quick and dirty fix as for most people... gstreamer does just fine, and it'll keep things congruent unless he changes everything over to xine.

---

### Post by az on 2006-06-27
[QUOTE=fjm03]Why does 6.06 install gstreamer totem as a default?

I'd like to watch movies utilzing proprietary codec. 

Thanks.[/QUOTE]
The proprietary codecs are not licenced for distribution.  They are pretty much stolen.

---

### Post by H.E. Pennypacker on 2006-07-06
> Why does 6.06 install gstreamer totem as a default?

Because it beat out other multimedia frameworks?  :)  

FJM, install Automatix or EasyUbuntu if you want to watch movies using proprietary codecs.

> 
Is the process as simple as it appears utilizing Synaptic Package Manager or is there a catch 22, politcally or otherwise?

Unfortunately, I believe Automatix/EasyUbuntu can only be installed via the terminal.  This is one of Ubuntu's downsides, but I guess there's nothing that can be done other than someone creating a .DEB package.  This means that, as far as I know, Automatix/EasyUbuntu are not availabe via Synaptic.

So, yes, it is more difficult, although others will tell you otherwise.

> 
Is the process as simple as it appears utilizing Synaptic Package Manager or is there a catch 22, politcally or otherwise?

[QUOTE=lawngn0mex]```

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

```[/QUOTE]

Lawn, you can see that the OP (original poster) said he is not that familiar with the terminal.  How's he going to know what sudo apt-get is?  

You could tell him to download those two packages (gstreamer plugs, ugly/bad) from Synaptic, instead of exposing him to all the text shown in the terminal.

---

