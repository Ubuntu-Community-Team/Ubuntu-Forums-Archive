---
title: "Kmix not working in Gutsy"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by jbrown96 on 2007-10-15
I have a HP dv1000. The volume controls worked properly in Feisty, but they don't work anymore in Gutsy beta. 
Kmix is controlling the "headphone" output, which work fine. It shows volume increasing and decreasing like it should. However, it doesn't do anything to the actual volume. 
I did some searching and found that PCM probably controls the speaker volume, which it does. I can control the volume with it. The problem is that I cannot get my volume buttons to control the PCM. I tried right clicking on Kmix and changing the "master channel" to PCM, but it does nothing.
Is there anyway that I can get Kmix to control the PCM?

Update:
After messing with Kmix some more, the mute button now controls PCM (by changing the light above the slider from green to unlit). Volume up and down still control Headphone.

---

### Post by EngDrewman on 2007-10-15
I'm having the same problem

---

### Post by jbrown96 on 2007-10-18
Not a problem anymore. Updates from Tuesday or Wednesday fixed the problem. However, there is no display about volume level when it is changed. Oh well, it's not important.

---

### Post by EngDrewman on 2007-10-18
The updates didn't solve my problem :(

---

### Post by ubuntunewb75 on 2007-10-19
Not working for me also, it simply says "Kmix is not running"

---

### Post by Rul on 2007-10-26
I have the same problem, anyone has an idea about this?

---

### Post by Rul on 2007-10-27
Well, I have been able to obtain some partial success with this...

In the kmix window, in preferences you have the option of configuring the global shortcuts of kmix. There you can create shortcuts to control the master volume. I use the volume keys of my laptop as global shortcuts, and after restarting kde it worked, although now I don't see the small dialog that shows me the change in volume.

So, as I said not a complete solution but at least my keys work now.

---

### Post by EngDrewman on 2007-12-21
Don't know if u guy are still following this thread, but I think I've got it figured out. There is a service that is disabled by default that needs to be enabled. Be sure you have the service **alsa-utils** enabled. Did the trick for me.

---

### Post by phpGuyLV on 2008-03-11
kmik volumn volume control quit stopped stop not working problem.

-Right-click on the kmix panel icon
-Select Master Channel
-Change to PCM 
-if not, try Master or another one.

---

### Post by rubioxtu on 2008-06-02
> **phpGuyLV said:**
> kmik volumn volume control quit stopped stop not working problem.

-Right-click on the kmix panel icon
-Select Master Channel
-Change to PCM 
-if not, try Master or another one.

It worked for me thanks
I reselected Master as Master Channel and everything works fine again with mouse wheel (still don't know why it stopped working before)

---

