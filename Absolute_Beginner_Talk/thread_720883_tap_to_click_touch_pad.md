---
title: "tap to click touch pad"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by R13120(1&lt; on 2008-03-10
so i thought i had the solution but delayed trying the answer i was givin until later due to time constrains but heres the deal

I turned off the tap to click function before and it was as easy as going to to third tab of the mouse settings. but now there is no third tab

i tryed going through the package manager and installing the various configuration tools for Synaptics touchpad but still the third tab won't apear and the tap to click is driving me nuts

i type up papers and brush the pad and all the sudden i'm in the middle of the paragraph so please

if you can tell me how to kill the tap to click demon i'll be your best friend.

---

### Post by neurostu on 2008-03-10
open a terminal and type
```

aptitude search synaptics

```
and paste the results.

---

### Post by R13120(1&lt; on 2008-03-11
aptitude search synaptics
p gsynaptics - configuration tool for Synaptics touchpad
p ksynaptics - Synaptics TouchPad configuration tool for
p libsynaptics-dev - library to access the synaptics touch pad
p libsynaptics0 - library to access the synaptics touch pad
p qsynaptics - Synaptic TouchPad configuration tool
p xfree86-driver-synaptics - Synaptics TouchPad driver for X.Org/XFree8
v xorg-driver-synaptics -
i xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org server

---

### Post by neurostu on 2008-03-11
try installing gsynaptics
```

sudo apt-get install gnsynaptics

```
When I installed it I could configure my touchpad.

---

### Post by R13120(1&lt; on 2008-03-11
awesome thanks....
no n though lol just gsynaptics

---

### Post by HowardDrake on 2008-03-13
I tried that but I get 

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

How do I fix this?

---

### Post by neurostu on 2008-03-13
If you type:
```
aptitude search synaptics
```
you will see that there are a couple synaptics configuration tools. Try installing the different tools and see which ones work.

---

