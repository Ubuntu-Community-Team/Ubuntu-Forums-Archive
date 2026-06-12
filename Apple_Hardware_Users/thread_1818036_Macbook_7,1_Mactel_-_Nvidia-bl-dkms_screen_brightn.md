---
title: "Macbook 7,1: Mactel - Nvidia-bl-dkms screen brightness control issues"
date: 2011-08-04
forum: Apple Hardware Users
---

### Post by Grungekid on 2011-08-04
Hello there,

I have this MacBook and I have it fully up to date with the proprietary Nvidia graphics drivers. I have installed the nvidia-bl module from the mactel repository however my brightness control isn't working as it should. 

The issue is basically that the brightness only starts to lower from full from about the half way point on the onscreen prompt and also randomly resets to full when I perform certain actions. For example, if I load up a game or play a video etc. Stuff which appears to involve some part of the graphics drivers which isn't normally in use maybe?

Thanks for any help guys. My system is perfect other than these issues which can be quite annoying! :)

---

### Post by ajhager on 2011-08-16
I am having these exact same issues.  I believe the GPU has two speeds to save power. The jump in brightness seems to happen whenever it kicks into overdrive. Sometimes even a flash ad will set it off.

Be sure to post back if you find any solutions. Other than this, Ubuntu feels way more responsive (and is more attractive, oddly) than osx.

* Update *
Today I hooked up another monitor, and in the process I opened the Nvidia control panel. Under display configuration there is a button to save the config to your xorg.conf file. I clicked that, restarted, and now I'm no longer having the issues. I'm not sure exactly what fixed it, but it might be that the card is now explicitly given as the 320m in the configuration. Hope this helps!

---

