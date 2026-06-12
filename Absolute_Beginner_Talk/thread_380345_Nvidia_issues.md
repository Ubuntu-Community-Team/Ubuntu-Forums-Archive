---
title: "Nvidia issues"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by progrockusa on 2007-03-09
Hello i'm having trouble with Nvidia drivers. i don't see the logo anymore when i start the system up.
i've tried various install and uninstall walkthroughs. i think my biggest mistake was installing easyubuntu and installing some nvidia driver off it when i shouldn't have.
so now when i go to xserver and set it up to use the nvidia driver rather than the nv, it fails to work and tells me something about versions numbers not matching.
any help would be appreciated

---

### Post by progrockusa on 2007-03-09
bump

---

### Post by o_fortuna on 2007-03-09
This should work:

Open up System--Administration--Software Properties. Delete anything under the Third-Party Software tab (easy ubuntu might have added something). Close the window, and open up System--Administration--Synaptic Package Manager. Press reload in the top-left corner, then scroll down looking for linux-restricted-modules. Mark it for complete removal by clicking the box.

After this is completed, go back and install linux-restricted-modules and nvidia-glx. When that's done, open up a terminal (Applications--Accessories--Terminal) and type in
```
sudo nvidia-xconfig
```
Then log out and press Ctrl+Alt+Backspace. This will restart your xserver.
Hope that helps.

---

### Post by progrockusa on 2007-03-09
ok here is more detail as to what happens when i try to use the nvidia driver in my current setup

API Mismatch: the nvidia kernel module has the version 1.0-7184, but this x module has the version 1.0-8776

so i can see where the issue is but i don't know how to resolve this. 
anyone ever had this happen please hollar . ty

---

### Post by progrockusa on 2007-03-09
> **o_fortuna said:**
> This should work:

Open up System--Administration--Software Properties. Delete anything under the Third-Party Software tab (easy ubuntu might have added something). Close the window, and open up System--Administration--Synaptic Package Manager. Press reload in the top-left corner, then scroll down looking for linux-restricted-modules. Mark it for complete removal by clicking the box.

After this is completed, go back and install linux-restricted-modules and nvidia-glx. When that's done, open up a terminal (Applications--Accessories--Terminal) and type in
```
sudo nvidia-xconfig
```
Then log out and press Ctrl+Alt+Backspace. This will restart your xserver.
Hope that helps.

followed your directions and the same thing
API mismatch

---

### Post by progrockusa on 2007-03-09
does anyone know what causes the API mismatch??

---

### Post by r4ik on 2007-03-09
Try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by r4ik on 2007-03-09
No but read,

[http://ubuntuforums.org/showthread.php?t=215495](http://ubuntuforums.org/showthread.php?t=215495)

Good luck !

---

### Post by progrockusa on 2007-03-09
k but how the hell do i install it
nvm i think i got it

---

### Post by r4ik on 2007-03-09
Oke.

---

### Post by progrockusa on 2007-03-09
great!! i can now see the nvidia logo before the login :) envy saved the day .. tyvm . now.. if i can get beryl to work i'll be amazed lol

---

### Post by r4ik on 2007-03-09
Beryl is not very stable yet anywayz,

Good luck !

---

### Post by garybrlow on 2007-03-10
Envy installs the official NVIDIA drivers. Follow the edgy beryl howto on [www.beryl-project.org](www.beryl-project.org). Beryl works fine on Dapper, Edgy, and Feisty. Currently running it on a Celeron 2.0 Ghz with 256MB RAM with an Asus Ge Force FX5200 128MB card. The Nvidia Official Drivers have been updated to 9755 btw.


Cheers!!!


GaryBrlow :biggrin:

---

