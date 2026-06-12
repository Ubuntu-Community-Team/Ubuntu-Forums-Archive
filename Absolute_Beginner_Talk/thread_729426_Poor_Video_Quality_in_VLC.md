---
title: "Poor Video Quality in VLC"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Ciansy on 2008-03-19
Hello,

I've recently installed Gutsy, using the alternative installation, on my computer with an AMD Athlon processor and ATI Radeon X1300 pro video card. I had to use the alternative installation due to problems with the card, but now everything's working fine except for playing DVDs with VLC (or any other movie player).

The picture quality is slightly poorer than it ought to be, while still being more or less watchable, but the real problem is a diagonal line that appears dead straight from top left to bottom right of the screen. This seems to turn up more the more action is appearing on screen, and can render it more or less unwatchable at times. Any help or advice here would be much appreciated. Thanks!

---

### Post by pedro_orange on 2008-03-20
I presume you've installed all the associated codecs etc?

```
sudo apt-get install ubuntu-restricted-extras
```

This sounds more like a graphics problem to me. My housemate has an ATI card and trying to get anything working with it is a total pain in his Ubuntu installation. (While it's easy with my nvidia installation)
I would say make sure your graphics are installed correctly. Check for guides around the net regarding your graphics card etc.

---

### Post by Tomatz on 2008-03-20
Try this:

Open vlc

open preferences

check advanced preferences (bottom rh)

then drop down video

select output modules

and change to X11


Then test your video :)

---

### Post by sayakb on 2008-03-20
X11 would rather make the video more pixelated. If you don't use compiz, you might try OpenGL output.

---

### Post by forrestcupp on 2008-03-20
How did you install your drivers for your ATI card?  If you didn't use the Restricted Drivers Manager, which driver version did you use?

The diagonal line has been a known problem with ATI cards.

---

### Post by Ciansy on 2008-04-13
Thanks for your help everyone. I'd a feeling that it was a common problem with ATI cards alright. I'm considering doing a few upgrades on my computer, so a different make of graphics card would be a high priority at this stage. I have indeed installed all the restricted extras, and I installed the drivers using Envy. I'm going to try the different output modules suggested the first chance I get.

---

