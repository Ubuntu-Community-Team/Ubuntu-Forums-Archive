---
title: "So is there a video driver for powerbook G4 IIs?"
date: 2009-05-19
forum: Apple Hardware Users
---

### Post by nintennuendo on 2009-05-19
No matter what distro i try none of them support the video, even though i can hook up an external monitor to clone and it works just fine.  do i have to enable the restricted driver? 

is there ANYTHING i can do?

---

### Post by stream303 on 2009-05-19
There are no proprietary restricted drivers with PPC.  The good news is that it is working with your external monitor.

What you have to do now is get around the Apple display quirk that doesn't like to play nice with Linux.

You didn't mention if you just got a black screen, or low-res graphics with your internal display.

At any rate, because this is Ubuntu, the first thing I'd do is bypass the splash screen.

At the second-stage of the yaboot boot: prompt, hit TAB to stop the countdown.  Then enter:

```
Linux nosplash
```

If that doesn't work, you could then try an additional parameter:

```
Linux nosplash video=ofonly
```

(Capital L for Linux btw...)

It could go beyond that however, requiring a custom /etc/X11/xorg.conf file to force the correct vertical and horizontal frequencies that your powerbook uses.

In addition, you may have to force the resolution, say 1024x768 mode as well.

Since I don't own a powerbook, perhaps another owner can help out.  In the meantime, you can see some generic instructions for xorg.conf in this thread that may help even though it is not powerbook specific:

[http://ubuntuforums.org/showthread.php?t=1162913](http://ubuntuforums.org/showthread.php?t=1162913)

---

### Post by nintennuendo on 2009-05-19
I should have clarified.  I insert a linux start up disk, get to a prompt if i want, if its the livecd it goes to the visuals.  at the prompt, no matter what i tell it to do, Linux nosplash, video=ofonly or any combination, eventually, after doing a standard load up, and when it should show some visuals like a gui, i get a really pretty explosion-esque screen, where gradually, everything fades to black.

What are all the commands I can try?  Are they case sensitive?

---

