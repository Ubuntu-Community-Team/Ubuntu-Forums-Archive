---
title: "[SOLVED] unable to install beryl-manager"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by jskandhari on 2007-12-26
gtk+- 2.0 
gthread
these are the pakages which it says not found what to do

---

### Post by GSF1200S on 2007-12-26
> **jskandhari said:**
> gtk+- 2.0 
gthread
these are the pakages which it says not found what to do

What version of Ubuntu are you running? If you are on 7.10, or even 7.04, you should have no problems using Compiz Fusion, which is better than Beryl (alot more stable IMHO)...

---

### Post by ~LoKe on 2007-12-26
Beryl merged back in with Compiz to form Compiz Fusion.  There is **no** reason to install Beryl.

---

### Post by jskandhari on 2007-12-26
alright
i didnt knew that i am new user to ubuntu and i am using 7.10 version
and 
now can you please guide me through how to go about it
i have now idea

---

### Post by GSF1200S on 2007-12-26
> **jskandhari said:**
> alright
i didnt knew that i am new user to ubuntu and i am using 7.10 version
and 
now can you please guide me through how to go about it
i have now idea

You have 3D drivers running, right? Post the results of: (in a terminal)

```
glxinfo
```

You should be able to enable desktop affects via the Desktop Affects section in System>Preferences (please correct me if im wrong; im on kde). If you want to have advanced effects and controls, then just use synaptic to install the 'Advanced Desktop Effects Settings'

**EDIT** If glxinfo returns 'Direct-Rendering: No,' then please post the results of:

> lspci

so we can tell what video card you have...

---

### Post by Sef on 2007-12-26
ATI and NVidia and other companies have different drivers that do 3D.  They are located in the System > Administration > Restricted Drivers Manager.    

To install Compiz-Fusion, go to synaptic and do a search Compiz-Fusion.

---

### Post by Hospadar on 2007-12-26
In general, you go to System->Preferences->Appearance->Visual Effects to enable compiz.  If you want access to the extra settings (the desktop cube, burning windows and the like) you'll need to install compizconfig-settings-manager from synaptic (then go to System->Preferences->Advanced Desktop Settings)  Usually the easiest way to install your 3d drivers is to go to Settings->Administration->Restricted Drivers Manager (if you have an nvidia card or integrated intel chipset especially)

---

### Post by jskandhari on 2007-12-27
got it done and all configured and yes i have nvidia geo force 8400gs

---

