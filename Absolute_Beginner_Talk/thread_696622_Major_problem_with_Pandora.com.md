---
title: "Major problem with Pandora.com"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by mattaklysm on 2008-02-14
I'm somewhat new to the linux thing, but I absolutely love it. However I believe that I have run into a bit of a snag with running my beloved Pandora.com. 

To first start this thread off, allow me to explain that I've already uninstalled flash and reinstalled it again with a purge function. Here is the command that I used: 

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

After that I went and cleaned up any kind of .jar files or any other files that held any form of significance with being a "temporary internet file", i think one would call them; so as Flash would not revert back to my former settings. Still, when i try to load Pandora.com, the page actually comes in - with its lovely blue-gray background - yet this obnoxious big blank screen sits in the center of the page. From there I cannot navigate around Pandora.



If there are any 1337 Linux users that could help out a common Linux peasant such as myself, much obliged and I would be forever in your debt. For I am an absolute junky of Pandora.com, AND I NEED MY FIX!!!!!

thanks again,
Pandora Junky Matt

---

### Post by Squizz on 2008-02-14
If you're using 64 bit Ubuntu - then [this thread]("http://ubuntuforums.org/showthread.php?t=476924") is almost certainly what you need.

If you're using i386 - then [this one]("http://laiconic.quotaless.com/tutorial3.html") is probably what you need.

---

### Post by emarkd on 2008-02-14
So what exactly is the problem?  I assume your flash still doesn't work.  How about removing flash again using the first part of that command, then visit Pandora.com and Firefox should prompt you and handle the installation for you.

I think...

---

### Post by mattaklysm on 2008-02-14
> **Squizz said:**
> If you're using 64 bit Ubuntu - then [this thread]("http://ubuntuforums.org/showthread.php?t=476924") is almost certainly what you need.

thanks!

But I'm actually using the 32 bit gutsy gibbon. I'm using a dinosaur of a computer

---

### Post by jan quark on 2008-02-14
> After that I went and cleaned up any kind of .jar files or any other files that held any form of significance with being a "temporary internet file", i think one would call them;

I would be very cautious with deleting anything manually, just as a remark

and make sure the gnash-mozilla-plugin is not installed on your system
check system > administration > synaptic and search for gnash

together with flash they might cause compatibility issues, just a guess

---

### Post by emarkd on 2008-02-14
> **mattaklysm said:**
> thanks!

But I'm actually using the 32 bit gutsy gibbon. I'm using a dinosaur of a computer

i386 is 32-bit (as is i686).  Many of us still use 32-bit.  The thread he pointed you to may work, but if I were you I'd try letting Firefox handle it first.  Seems easy enough...

---

### Post by emarkd on 2008-02-14
As an aside, I had never used Pandora.com until this thread, but it's awesome!  And it'll work fine for you in Ubuntu after you get your flash issue resolved.  Thanks.

---

### Post by mattaklysm on 2008-02-14
> **emarkd said:**
> So what exactly is the problem?  I assume your flash still doesn't work.  How about removing flash again using the first part of that command, then visit Pandora.com and Firefox should prompt you and handle the installation for you.

I think...

hermmmm, hopefuly your Mods are nice about double-posts but i'm desperate....

actually i already let firefox take over the very first time to try and reinstall my flash plugins and i got the same exact results.

---

### Post by emarkd on 2008-02-14
Did you try removing gnash as suggested above?

---

### Post by mattaklysm on 2008-02-14
sorry, but this is all that I saw. I was afraid to start removing all the applications entitled gnash. here's a screen shot.

---

### Post by emarkd on 2008-02-14
Yeah, you need to get rid of both of those. In fact, I'm sure one depends on the other, so Synaptic would probably make you remove them both at once.

Afterwards, you may have to remove flashplayer and let Firefox reinstall it yet again.  Not sure though...

---

### Post by mattaklysm on 2008-02-14
> **emarkd said:**
> Yeah, you need to get rid of both of those. In fact, I'm sure one depends on the other, so Synaptic would probably make you remove them both at once.

Afterwards, you may have to remove flashplayer and let Firefox reinstall it yet again.  Not sure though...

alright. here goes. i'll purge flash again, get rid of gnash and let firefox install the NON-gnash version.

---

### Post by mattaklysm on 2008-02-14
> **emarkd said:**
> Yeah, you need to get rid of both of those. In fact, I'm sure one depends on the other, so Synaptic would probably make you remove them both at once.

Afterwards, you may have to remove flashplayer and let Firefox reinstall it yet again.  Not sure though...

It worked!

Big huge Thanks to jan quark and emarkd!!

You guys Rock! Gave you a thanks!

---

