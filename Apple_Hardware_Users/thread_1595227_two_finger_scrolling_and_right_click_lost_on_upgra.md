---
title: "two finger scrolling and right click lost on upgrade to maverick"
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by s_p_a_r_k_y on 2010-10-13
I just upgraded to maverick, but seems that the ability to right click with two fingers and middle click with 3 is lost as well as the ability to scroll on pages.

the gnome-mouse-properties has been simplified and lost some settings which use to exist. Any help here would be much appreciated!

---

### Post by spook on 2010-10-13
Install xserver-xorg-input-synaptics.  That will give you two finger right-click and two finger scrolling but I'm not sure about 3 finger click.

---

### Post by zachthejones on 2010-10-13
I had a similar issue, but it was that I lost my two-finger scrolling, while I can use two or three fingers to right-click, only three fingers will open a link (in a browser) in a new tab (I used to be able to do this with two fingers).

I'm dying here without my two-finger scrolling....well, not literally dying, but it is getting more annoying every minute.

I checked and I've got the latest version of xserver-xorg-input-synaptics - is there a program or something that will enable me to access my multi-touch settings?

---

### Post by JFK.NM on 2010-10-14
Same issue here Mactel 3.1 after upgrade to Maverick.

---

### Post by hiddencharms on 2010-10-14
I'm on a 4,1 Macbook and was having the same problem. Installing the xserver package above fixed it for me. Make sure the Mactel repository is updated (and enabled) as one of your SoftwareSources

---

