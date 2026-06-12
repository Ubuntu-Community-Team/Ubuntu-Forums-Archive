---
title: "Error booting from live CD"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by jook on 2007-05-04
Recently hen trying to boot from my live ubuntu cd (v6.06) It hasn't been getting all the way. I get to the bootscreen - circles logo, and a progress bar going back and forth - and it takes a while there, which is to be expected. Then the progress bar fills up, and the screen would go away.
Now, usually at this point I'd just get a black screen with a blinking white cursor at the top left, but last time it said some tings which might be useful to figure out what's going on.


     *Activating swap                                                                     [ ok ]
mount: function not implemented
     *Checking file systems...
fsck 1.39 (may 2006)
                                                                                                      [ ok ]
_


Nothing has changed on my system since it used to work, that ought to affect anything. Especially since booting the live cd ought to haeve very little to do with my system. What's going on here? Should I just try burning a new ubuntu disk?

(edited for typos)

---

### Post by Rotaj on 2007-05-04
When starting from the live disk, sellect the option to check the cd for errors.
If the disc has errors, burn a new disc at a slower speed, 10-12x max.

---

### Post by jook on 2007-05-06
I booted to the ubuntu CD and selected Check for Errors. It did a couple things, then said it was going to do the actual work and it might take a while, so I went off to eat. When I came back, the screen was all black. Moved the mouse, nothing happend. Pressed some keys, a bunch of lines of white text showed up on black screen. The end of the list was something along the lines of "checking HDD 1 something something..." followed by an error. Failed to initialize maybe? I didnt think to write it down. These two lines repeated several times, though. nothing i did seemed to help/affect anything (there was a text prompt to type in, sort of...), so I hit the reboot key on my tower, swapped to my super grub disk before the bios tried to boot, and now I'm in XP again. Anyway, what does that sort of error mean? Should I try making a new ubuntu CD? Would doing a Feisty Fawn one help me any? Or is there even any reason to make a new one of the older version, if I'm going to make a new disk at all?

(edited for typos)

---

