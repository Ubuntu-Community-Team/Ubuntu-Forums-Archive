---
title: "Videos not playing on Youtube since new Firefox update today"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-03
I was able to play videos on the Youtube website just fine until today, when the Ubuntu updater did a series of updates related with the Firefox Web Browser. Now when I click to play any Youtube video, the video freezes on the first frame. The video seems to download in full (after it has downloaded I can scroll through it with the scrollbar). But it won't play. It neither plays as it downloads, nor will it play after it has downloaded. What can I do to get the videos to be able to play again? Is there some way to uninstall today's Firefox update?

---

### Post by overdrank on 2007-06-03
> **swarup said:**
> I was able to play videos on the Youtube website just fine until today, when the Ubuntu updater did a series of updates related with the Firefox Web Browser. Now when I click to play any Youtube video, the video freezes on the first frame. The video seems to download in full (after it has downloaded I can scroll through it with the scrollbar). But it won't play. It neither plays as it downloads, nor will it play after it has downloaded. What can I do to get the videos to be able to play again? Is there some way to uninstall today's Firefox update?

Hi did firefox ask to be restarted after updates? If you have not restarted try that and I hope this helps. :popcorn:

---

### Post by irish_flu on 2007-06-03
If I had to make a guess, it's a problem with Adobe Flash (Youtube uses Flash for its videos).  You might try removing and reinstalling it (but like I said, I'm sort of guessing here):

```

sudo apt-get remove flashplugin-nonfree

```
```

sudo apt-get install flashplugin-nonfree

```

You might also try going to this page:
[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

If Flash is installed properly, it should say something like "Adobe Flash is installed" and show you a version number.

---

### Post by swarup on 2007-06-03
> **overdrank said:**
> Hi did firefox ask to be restarted after updates? If you have not restarted try that and I hope this helps. :popcorn:

It did ask to be restarted and I did restart it. I did not shut down the whole computer and then reboot it, but I did close and reopen firefox. But it didn't make any difference. Am I the only person having this problem?

---

### Post by swarup on 2007-06-03
> **irish_flu said:**
> If I had to make a guess, it's a problem with Adobe Flash (Youtube uses Flash for its videos).  You might try removing and reinstalling it (but like I said, I'm sort of guessing here):

```

sudo apt-get remove flashplugin-nonfree

```
```

sudo apt-get install flashplugin-nonfree

```

You might also try going to this page:
[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

If Flash is installed properly, it should say something like "Adobe Flash is installed" and show you a version number.

Thanks. I went to the macromedia website you referenced, and it says there:

 "You have version 9,0,31,0 installed".

Does that mean that it is correctly installed, so there is no need to remove and reinstall it?

---

### Post by Mike_88 on 2007-06-03
> **swarup said:**
> Am I the only person having this problem?
I'm suffering from this problem as well.  Flash was working fine until I upgraded the kernel the other day, now it keeps freezing on me.  I too have 9.0 r31 installed.

---

### Post by HeavyMetalMessiah on 2007-06-03
The flash plugin just needs to be reinstalled.  Just go to any page with flash content and it should give you a prompt to install the plugin.

This is what worked for me anyway.

---

### Post by swarup on 2007-06-03
irish_flu had suggested that I remove and reinstall the flash plugin-- he said he was guessing, but this sounded like a reasonable approach. Would others also agree that this should be done. I would like to hear from someone else about it before moving ahead, as I want to know that by doing so I will not be creating a bigger problem than I am attempting to solve.

---

### Post by marianwmetal on 2007-12-02
**Well, it'a actually simpler...at least for me...I have been using the Synaptics Package Manager in order to remove all plugins (flash and all other) from firefox plugins folder. Just do a search with something like firefox plugins and mark for removal what you need to. Then search for the mplayer plugin for mozilla, mark it for installation (this will add all the other required libraries) and apply the changes. After that you only need to restart firefox in order to be able to play the embbed movies. In the firefox plugins folder should then be only the mplayer plugins and another one like flashplugin-alternative.so that can handle very well the flash thingies. And that's it. Just make you you have already enabled all the software sources :)) **

---

