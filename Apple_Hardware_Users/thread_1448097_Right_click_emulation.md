---
title: "Right click emulation"
date: 2010-04-06
forum: Apple Hardware Users
---

### Post by mikeym on 2010-04-06
Hi there,

I've been asking around about how to get a right click emulation (ctrl+mouse1) working on my single button 1GHz G4 7455 and I was wondering if anyone here had any ideas about how to go about it?

---

### Post by linuxopjemac on 2010-04-06
You could install mouseemu
```
sudo apt-get install mouseemu
```
see [here]("http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=67")

also interesting:
[http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0](http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0)

---

### Post by nakedninja on 2010-04-07
Right, so I got mouseemu, I put all of that text into the config file, I saved, quit and poof, nothing.  
What am I doing wrong, I'm new so obviously I'm doing it wrong, I'm just not sure what.  My current mouseemu reads as so

    # Defaults for mouseemu initscript (/etc/init.d/mouseemu)
    # These are the default values on PowerPC. On all other architectures
    # middle and right click are disabled by default.
    # Key codes can be found in include/linux/input.h in the kernel headers
    # or by using `showkey` in a console.

    #MID_CLICK="-middle 0 87"         # F11 with no modifier
    #MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
    #RIGHT_CLICK="-right 0 88"        # F12 with no modifier
    RIGHT_CLICK="-right 0 126"        # Right Apple Key with no modifier
    #SCROLL="-scroll 56"              # Alt key
    #TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

now I figure I should be able to just press the right apple key and it should work?  Or apple and click, but nothing.
Some help would be great, thanks.

---

### Post by linuxopjemac on 2010-04-08
it should work...after a reboot....you could try F12. are you sure that mouseemu is running in the background?

```
ps -ax grep mouseemu
```

---

### Post by nakedninja on 2010-04-08
I'll give that a try later when I get back to the 'puter, thanks mate.  
My F12 button for some reason is still set to eject, infact most of the apple specific keys along the top still work like that, brightness, volume etc.
 
How would I go about making sure mouseemu runs all the time?

---

### Post by linuxopjemac on 2010-04-08
If you install it, it should always start at boot. I have to check this out myself, I don't know.

---

