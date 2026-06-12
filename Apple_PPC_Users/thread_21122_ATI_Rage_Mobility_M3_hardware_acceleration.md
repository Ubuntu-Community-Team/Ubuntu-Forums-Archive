---
title: "ATI Rage Mobility M3 hardware acceleration?"
date: 2005-03-20
forum: Apple PPC Users
---

### Post by lordmyth on 2005-03-20
I'm updating the Warthy cd installation on my iBook to Hoary, and I have a question: will the built in ATI Rage Mobility M3 chip ever get hardware acceleration?

-update finished, and when I run glxgears I get around 450 FPS... is this normal for a 500mhz G3 iBook?

---

### Post by DJ_Max on 2005-03-21
I'm not sure about the FPS, but I believe you should, with the correct settings get DRI to work. You'll have to look around, I remember there was a how-to about dri on ATI Rage's xx cards for macs.

---

### Post by lordmyth on 2005-03-21
How do I know if DRI isn't allready working?

---

### Post by DJ_Max on 2005-03-21
Do this
```
glxinfo | grep "direct rendering"
```

---

### Post by lordmyth on 2005-03-21
OK, it's allready working!

---

### Post by DJ_Max on 2005-03-21
[QUOTE=lordmyth]OK, it's allready working![/QUOTE]
 Ok, then there ya go. ;-)

---

### Post by paulicat on 2005-03-21
For comparisons sake I get 514 fps on glxgears on a p3 850 with a Rage Mobility M3.

---

### Post by ggeneraux on 2005-06-09
If the result from this below command is "No" then how do you go about turning on direct rendering?  I have a Dell Inspiron 4000 (sounds like the same processor as above, pIII 900 Mhz) with a ATI Rage Mobility M3 (8M ram) and get about 120 fps when I run 'glxgears'  


[QUOTE=DJ_Max]Do this
```
glxinfo | grep "direct rendering"
```[/QUOTE]

---

### Post by chascon on 2005-06-10
[QUOTE=][/QUOTE]
 there's a string on accel with Rage cards

---

