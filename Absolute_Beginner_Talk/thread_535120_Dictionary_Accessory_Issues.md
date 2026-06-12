---
title: "Dictionary Accessory Issues"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Xaviar on 2007-08-26
The Dictionary Accessory is American.  I think an inbuilt on-line dictionary is a great idea but, being Australian, I have no use for an American dictionary.  My options are either to accept incorrect spelling (which I'd rather my children not have access to since I am already trying to undo the damage caused by their school enforcing a Microsoft-only policy in their computer systems) or to un-install the dictionary along with the other very useful items which have been inexplicably linked to it.  Is there a solution?  Is there a way to set the dictionary to English or, failing that, a way to delete it from the system without harming the disc analyser & screen-shot accessories?

---

### Post by K.Mandla on 2007-08-26
Hey, what do you mean an incorrect spelling? Those aren't incorrect! :lol:

I do have one idea for you: You could reconfigure the locales on your computer, and perhaps the dictionary will correct itself. :???:

Try this. 

```
sudo dpkg-reconfigure locales
```
No guarantees, though. Mostly because I haven't worked with Gnome or the dictionary applet in about a year. :oops:

Locales are independent of time zone, so you shouldn't have an issue in that sense. Hope that helps.

---

### Post by Xaviar on 2007-08-29
Thanks for the suggestion but, no luck, my locales are already all set up properly.  It looks like I am supposed to locate an on-line English dictionary and enter the address in the Preferences menu of the Gnome Dictionary.  I've tried a few with no success so I've just un-installed it (and it's mates) instead.  I'll look around for a decent dictionary application to take it's place and find other programmes to use for disc analysis & screen-shots as well I guess.  Happen to know of anything which would fit the bill?  Thanks for responding though.  Cheers.

---

### Post by hyper_ch on 2007-08-29
waht dictionary do you actually mean?

---

### Post by s26c.sayan on 2007-08-29
[Stardict]("http://stardict.sourceforge.net/") is my favorite dictionary application. It is offline and allows to 'install' a huge array of freely available dictionaries! You might want to take a look.

[Ksnapshot]("http://en.wikipedia.org/wiki/KSnapshot") is a really cool screenshot app. Some other screenshot apps are listed  [here]("http://www.linux.com/articles/57772").

---

### Post by Xaviar on 2007-09-02
> **hyper_ch said:**
> waht dictionary do you actually mean?  
I've un-installed it now but it was the on-line dictionary accessory which appeared in the Accessories menu and was associated (in Synaptic) with the screen-shot & disc analysis tools.

> **s26c.sayan said:**
> [Stardict]("http://stardict.sourceforge.net/") is my favorite dictionary application. It is offline and allows to 'install' a huge array of freely available dictionaries! You might want to take a look.

[Ksnapshot]("http://en.wikipedia.org/wiki/KSnapshot") is a really cool screenshot app. Some other screenshot apps are listed  [here]("http://www.linux.com/articles/57772").

Thanks, I will check those out.

---

