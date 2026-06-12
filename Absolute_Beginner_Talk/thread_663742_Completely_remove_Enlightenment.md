---
title: "Completely remove Enlightenment?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2008-01-10
I want to try gOS and after I installed it, Enlightenment keeps my old settings.

So I'm trying to remove it, and then install gOS, but still Enlightenment remembers my (deleted) settings.

I removed it like this:
```
sudo apt-get remove enlightenment* --purge
```
and autoremove all the libs
```
sudo apt-get autoremove
```

Then I delete the .Enlightenment folder in my /home.

After all this, I finally type in:
```
locate enlightenment
``` 

And it does't list anything like it else off cause did before I removed it.
Yes! Must be removed now..  then I go to apt-get the greenos like the howto told me.

When the install is complete, I logout, pick Enlightenment, login and BANG! It still remember my old settings and don't show the GreenOS?
:(

How do I completely remove everything that has to do with Enlightenment, so I can try gOS?

---

### Post by LaRoza on 2008-01-10
Remove the configuration directory in your home directory. Press Ctrl + H to see the hidden files.

---

### Post by aktiwers on 2008-01-10
Isn't that /home/aktiwers/.enlightenment

?

Because I already did that?

EDIT:
Ahhh Thanks! I found it.. there also was a folder called ".e".. I think it was it. Now off to remove it all and reinstall gOS again :)

---

### Post by aktiwers on 2008-01-10
It doesn't at all look like the screenshot here?
[http://www.thinkgos.com/](http://www.thinkgos.com/)

All I can see is they changed the theme?
Not even the dock is there?

---

### Post by fudoki on 2008-01-10
Keep in mind that Enlightenment is THE GUI in gOS, and so far as I know is the ONLY GUI in gOS, so don't try to remove Enlightenment from gOS or you will really have a mess on your hands...

Good luck!

---

### Post by aktiwers on 2008-01-10
> **fudoki said:**
> Keep in mind that Enlightenment is THE GUI in gOS, and so far as I know is the ONLY GUI in gOS, so don't try to remove Enlightenment from gOS or you will really have a mess on your hands...

Good luck!

Yeah I know that..  what I want to do is to install Enlightenment on Google with all the same configs, themes and so on, on Ubuntu. But my old configs keeps getting in the way somehow.

---

### Post by zvacet on 2008-01-10
Do you have **.e** folder ?If you do delete it.

---

