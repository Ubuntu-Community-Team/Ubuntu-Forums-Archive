---
title: "The white screen of death?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Revmann on 2007-05-06
I went ahead and tried Feisty again after having a video issue with it in one of the pre-release versions. I am running an ATI X1900. I got it loaded and working. I pressed the enable desktop effects button. The whole screen went bright white and I can't see anything. No text or anything shows, just this white screen. Upon rebooting, I come back to this white screen time after time. Is there a way to fix this short of reinstalling?

---

### Post by taurus on 2007-05-06
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Revmann on 2007-05-06
I don't think the command was specific enough. I entered it, but it acted like it needed to know more. When I rebooted, it still did the same thing.

---

### Post by dwblas on 2007-05-06
You probably have to sudo
> sudo dpkg-reconfigure xserver-xorg and enter root's password

---

### Post by taurus on 2007-05-06
> **dwblas said:**
> You probably have to sudo
and enter root's password

You don't need sudo if you boot into recovery mode.

---

### Post by Revmann on 2007-05-06
My bad. I put extra spaces in there and it didn't like it. I went back with the spaces removed and it worked. Thanks for the help.

The only problem is that when it worked, i didn't know what i was doing and screwed it up even more. I went ahead and reinstalled since all I had done with Ubuntu was just update it. I didn't have much to lose :p

---

### Post by Derspankster on 2007-05-06
> **dwblas said:**
> You probably have to sudo
and enter root's password

Does no good. I accidentally enabled Feisty's "Desktop Effects" and now have nothing but a white screen and cursor. I've reconfigured X a couple of times but it makes no difference.

---

### Post by neodarksaver on 2007-05-06
You will get out of the white screen after 40 secs i think. It's automatic.

---

### Post by Derspankster on 2007-05-06
> **neodarksaver said:**
> You will get out of the white screen after 40 secs i think. It's automatic.
It doesn't appear to be automatic after any length of time.

---

### Post by Derspankster on 2007-05-08
> **Derspankster said:**
> It doesn't appear to be automatic after any length of time.
Here's how I fixed things on my laptop running a crappy SIS video card. Boot into terminal or command line and run dpkg-reconfigure xserver-xorg.  Remove glx from Section Module by arrow keying down to it and pressing your spacebar. That will remove the check from glx. Finish the rest of the screens and restart your system. The white screen should be gone.

---

