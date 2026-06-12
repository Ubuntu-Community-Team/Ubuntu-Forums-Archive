---
title: "Stuck on a blank screen"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by DarkRookie on 2007-11-20
I am trying to use the Live CD on my laptop. It worked fine on my desktop. I try starting it. After what appears to a list of things loaded I get a blank black screen with nothing on it.

---

### Post by phidia on 2007-11-20
Don't what make and model of laptop  you're using but there is a sticky on problems with HP's [here]("http://ubuntuforums.org/showthread.php?t=582220")
You may need to use the nopic option at boot. 
Provide your system specs please and someone mat have an answer.

---

### Post by DarkRookie on 2007-11-21
I do have a HP laptop. Says that Gusty won't work with them.
I was looking for Feisty. But that main site doesn't have it as I could find. And there is no bittorrent file that are working right now.

---

### Post by 3rr0r on 2007-11-21
google is your friend...

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by DarkRookie on 2007-11-21
tryed google.
Must have put some wrong search terms in or something

---

### Post by DarkRookie on 2007-11-22
even with version 7.04 i still have this problem
Could the problem be that I have Vista install on the harddrive?

---

### Post by spiderbatdad on 2007-11-22
[https://help.ubuntu.com/7.04/windows/C/](https://help.ubuntu.com/7.04/windows/C/)

There may be a problem. My friend was having some difficulty with his HP 9000 series
Try hitting f6 at boot and where you see quiet splash --   at the bottom of the screen, replace quiet splash with ```
nosplash noapic noacpi --
```

sometimes nolapic has to be used instead of noapic. This is what I have read in other threads

---

### Post by DarkRookie on 2007-11-23
Quiet Splash?
Haven't seen anything.
Or is it a boot time.

New to linux here

---

### Post by TNakos on 2007-11-23
use a alt CD... maybe that would work.....

---

### Post by DarkRookie on 2007-11-24
> **spiderbatdad said:**
> [https://help.ubuntu.com/7.04/windows/C/](https://help.ubuntu.com/7.04/windows/C/)

There may be a problem. My friend was having some difficulty with his HP 9000 series
Try hitting f6 at boot and where you see quiet splash --   at the bottom of the screen, replace quiet splash with ```
nosplash noapic noacpi --
```

sometimes nolapic has to be used instead of noapic. This is what I have read in other threads

thanks for the code
it worked 
saw where quiet splash was
thanks for the help

---

### Post by DarkRookie on 2007-12-14
the code did work
but i installed it and now have a blank screen again
i seen the the progress bar then blackness

---

