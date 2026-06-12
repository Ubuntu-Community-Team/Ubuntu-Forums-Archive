---
title: "Mouse not moving in ubuntu under Microsoft vitual pc"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by justice on 2007-07-10
Hi,
I am completely new in Ubuntu.recently i installed "Ubuntu 7.04" on my latop in "Microsoft Virtual PC". I am running Microsoft vista home premium and my laptops mouse pad is "Synaptics PS / 2 port pointing device". after the installation everything is ok but mouse not moving.I tried my best to sort this out but would not able to da so.....Any one please able to help me about in this matter...
Thanks

---

### Post by quinnten83 on 2007-07-10
That is a problem with virtual pc itself. you have to press alt (right alt and some other key) to activate it. There is also an option for automatic capture, but that will not always work with all configurations, and i believe it doesn't work if the guest OS isn't an MS variant.
Check the documentation of VP2007 for more info. It is in there, or doe a google search.

---

### Post by NorthernLights on 2007-07-12
Actually mouse support under virtual PC with Feisty Fawn (and Debian testing) IS broken. But the fix is easy :
[CENTER]Add "i8042.noloop" to the kernel options in grub[/CENTER]

That's all :)

---

### Post by cpudoctor on 2007-08-21
Total newbie question...how do I do that?  Specifically because I've got about 15 min. of time on linux so far.  Sorry for the stupid question!

---

### Post by Sasky on 2007-08-25
At the "Ubuntu" loader page where you are prompted to:

"Start or Install Ubuntu"
"Start in Safe Graphics Mode:
etc.
etc.
etc.


Just hit F6 for "Additional Options"  then type:     i8042.noloop
Then hit enter...

---

