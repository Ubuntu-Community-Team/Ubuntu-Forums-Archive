---
title: "Screen Brightness Adjustment Stopped Working"
date: 2012-03-28
forum: Apple Hardware Users
---

### Post by rcrampton on 2012-03-28
My screen brightness function keys used to work just fine. I hooked up an external monitor and used both the built-in "displays" application and then the "nvidia xserver settings" application to change my settings.

I have since then used the nvidia app to try to reset everything back to a single display.

Only problem is that my display function keys no longer control the brightness. The icon and brightness scale appear on the screen when I hit the keys and the scale goes up and down.

I did not backup my xorg.conf settings file (oops).

I'm running an Intel Macbook Pro 5.4, Ubuntu 3.0.0-16, 32bit.

Any help is appreciated!

---

### Post by dnova on 2012-03-30
I don't have a solution, but I can report a similar problem, which started after I installed the last round of kernal updates last night. The nvidia tools (nvclock) still works to adjust the brightness, but every few minutes (or less) the brightness resets to 100% on its own. 

Any thoughts on how to fix this?

---

### Post by Caltac on 2012-03-31
I had a similar problem on my Macbook pro 7,1. My brightness keys literally had no effect on the brightness whatsoever.

I installed the Mactel source and downloaded the package nvidia-bl-dkms, and after a reboot my brightness keys worked perfectly.

To install the Mactel source, run
```
 sudo add-apt-repository ppa:mactel-support 
```Then update, and run
```
 sudo apt-get install nvidia-bl-dkms 
```Hope this helps.

---

