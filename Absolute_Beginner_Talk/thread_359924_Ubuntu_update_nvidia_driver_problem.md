---
title: "Ubuntu update nvidia driver problem"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by eduardoeltortuga on 2007-02-12
After I updated Ubuntu my x server failed to start. I searched the forums and tried many different suggestions. X server still fails to start after reconfiguring. I installed envy so that I could get the new drivers for the new kernel but that didn't work. I'm using the old kernel for now. I thought envy would get my new drivers.
     After I reconfigure the x server and type startx I get the message "Failed to load the NVIDIA kernel module". Everything was working fine before the update. I even got beryl to work! 
                                                               Ubunto all!  Thanks for any help!

---

### Post by EvilMarshmallow on 2007-02-12
You have to reinstall nVidia drivers after a kernel update.  I had the same problem.  Find the .run file that matches up with your card and re-run it as if you have a new card you're installing.

The Envy script is getting there, but if you have a card he hasn't supported yet or some other kind of strange setup, it may not work for you.  The surest way is to go to nvidia.com and find the driver yourself.

If you go to "Step 1" in the readme for each driver, it has a link to an appendix that lists which cards that particular driver version supports.  Find the latest one with your card and download the .run file.

---

### Post by IanW on 2007-02-12
I found that I had to ```
sudo aptitude install linux-restricted-modules-generic
```which hadn't been updated with the kernel.

---

### Post by eduardoeltortuga on 2007-02-12
thanks for the help! I'll keep trying until I get it!

---

### Post by EvilMarshmallow on 2007-02-12
Post back if you need more help, I just did this & it's fresh in my mind!

---

### Post by eduardoeltortuga on 2007-02-14
Background: Last update broke stuff. Spent 2 weeks searching and reading. Many others same problems. Tried envy. No go. New Nvidia drivers from Nvidia. Reconfigured x server. Reboot. GUI back up! beryl works only partially:confused: Next boot let's me log in then freezes at splash screen. Won't go to desk top. Once upon a time, got beryl to work 100% Too cool:)  Stuck at splash screen with no beryl:(  Advice? I can start xserver in recovery mode with beryl semi-functional.

---

### Post by EvilMarshmallow on 2007-02-14
Sounds like you might have the wrong version of the video driver?  What video card do you have, and which driver did you download?

In your apps menu there is probably an NVidia settings widget.  What shows on there?  Do you see direct rendering enabled?  Does it have settings on there that look right?

---

### Post by eduardoeltortuga on 2007-02-14
Thanks for your reply. I'm off to work, so I'll give it a looksy when I get home:)

---

### Post by eduardoeltortuga on 2007-02-17
I reinstalled Ubuntu and installed the new Nvidia drivers. Everything works great now! Beryl is 99% functional. I can't find the window preview any longer. There is no extra tab in the beryl manager anymore. Maybe when the new one comes out.  Anyway, thanks for the help!  Ubuntu to all and to all a good night.

---

### Post by Psyphre on 2007-02-17
hey eduardo. I too had this exact problem with updating nvidia drivers. Would you mind explaining how you did it successfully? Im super noob, so it would be nice if you could explain in very easy terms. Thank you!

edit: its ok, i got it working in the end!

---

