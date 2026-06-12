---
title: "[SOLVED] xine*?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-29
i'm trying to install xine* in the terminal but following message is coming:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kaffeine-xine: Depends: kaffeine but it is not going to be installed
  libxine-xvdr: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is to be installed
  libxineliboutput-fbfe: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is to be installed
  libxineliboutput-sxfe: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is to be installed
  xineliboutput-fbfe: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is to be installed
  xineliboutput-sxfe: Depends: libxine1 (< 1.1.8) but 1.1.10-1~gutsy1 is to be installed
E: Broken packages

```


NEED HELP. I don't what that means.:confused:

---

### Post by Joeb454 on 2008-03-29
Try running this from a terminal: ```
sudo aptitude install libxine1-ffmpeg
```

And do you now have the codecs you want/need? :)

_EDIT:_ Updated command to run, thanks **forestpixie** :)

---

### Post by bhadotia on 2008-03-29
after running the command the following message came:


```
Couldn't find any package whose name or description matched "libxine-ffmpeg"

```

what to do now?

---

### Post by Joeb454 on 2008-03-29
EDIT:

Pretty useless post now...:lolflag:

---

### Post by forestpixie on 2008-03-29
try libxine1-ffmpeg - it's changed

```
sudo apt-get install libxine1-ffmpeg
```

Edit - Joeb454 - changed to libxine1 with gutsy

---

### Post by Joeb454 on 2008-03-29
Thanks **forestpixie** :D I thought it had a 1 somewhere, though I thought it was at the end. Just updating my other post now :)

---

### Post by bhadotia on 2008-03-29
hi forestpixie,joeb454,
 the following message came:
```
libxine1-ffmpeg is already the newest version.

```

---

### Post by forestpixie on 2008-03-29
You would not believe how long it took me to sort that when I went to Gutsy - shouted, screamed and even promised the pc I would reinstall win, still didn't find it until I installed exaile and swore at that :)

If only I could get exaile to remember where it stopped in a playlist I'd have another go with that. I get really fed up listening to the same song again and again...

---

### Post by forestpixie on 2008-03-29
bhadotia - why are you trying to install it then - what is it that is not working?

---

### Post by bhadotia on 2008-03-29
i was just trying to make my system complete.:(

---

### Post by Joeb454 on 2008-03-29
You could also try ```
sudo aptitude install libxine1-all-plugins
``` :) Just found that one myself :D

---

### Post by forestpixie on 2008-03-29
So it doesn't need it then - only install what you need, when you install something it will pull in what it needs  - until you start installing from source, then it can be fun.

If you're trying to make you're system complete - there are 25000 different packages available on my synaptic without src repos - you're not going for them all are you :biggrin:

You don't need to do the windows "install all the codecs you can find" thing here - I did that at the start - installed every single one I could find and didn't need them, but didn't realise till about 6 or 7 reinstalls/upgrades and installs over the last year and a bit.

---

### Post by forestpixie on 2008-03-29
> **Joeb454 said:**
> You could also try ```
sudo aptitude install libxine1-all-plugins
``` :) Just found that one myself :D

OOOh good one that :)

---

### Post by bhadotia on 2008-03-29
well thanks guys (for tolerating me - that is).:popcorn:

---

### Post by Joeb454 on 2008-03-29
No worries :) Did you try installing that last package I mentioned?

---

### Post by bhadotia on 2008-03-29
yeah and thanks that installed all the codecs i'll ever need:lolflag:

---

### Post by Joeb454 on 2008-03-29
Lol glad to hear it :D

---

