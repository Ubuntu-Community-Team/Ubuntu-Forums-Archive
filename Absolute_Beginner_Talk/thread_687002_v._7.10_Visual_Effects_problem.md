---
title: "v. 7.10 Visual Effects problem"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by obliviousdream on 2008-02-03
Okay, I've looked at the threads, and couldn't find my problem. If you know of  post where there's an answer, or could just answer here, I'd be really grateful. ^_^

Okay, when I try to activate the Visual effects, it gives me a message saying: "Failed to execute child process "compiz" (No such file or directory)"

Could someone please help?

---

### Post by overdrank on 2008-02-03
> **obliviousdream said:**
> Okay, I've looked at the threads, and couldn't find my problem. If you know of  post where there's an answer, or could just answer here, I'd be really grateful. ^_^

Okay, when I try to activate the Visual effects, it gives me a message saying: "Failed to execute child process "compiz" (No such file or directory)"

Could someone please help?

HI and welcome, what is the model of the graphics card and have you installed the drivers?

---

### Post by obliviousdream on 2008-02-03
Uhm...How do I find that out?&#65288;Sorry...Never had to check...)

---

### Post by overdrank on 2008-02-03
> **obliviousdream said:**
> Uhm...How do I find that out?&#65288;Sorry...Never had to check...)

Hi and you can use the command ```
lspci
``` in the terminal located under applications, accessories. And look for VGA and this will identify your graphics. You may look under system, administration, restricted drivers to see if you card requires drivers.

---

### Post by obliviousdream on 2008-02-03
00:02.0 VGA Compatible Controller: Intel corporation Mobile 915GM/PM/GMS/910GML Express Graphics Controller (rev 03)

That's what it says for VGA, and I don't think I have the Restriced Drivers option. I checked, and it wasn't in Administration.

And hi ^_^

---

### Post by icechen1 on 2008-02-03
> **obliviousdream said:**
> 00:02.0 VGA Compatible Controller: Intel corporation Mobile 915GM/PM/GMS/910GML Express Graphics Controller (rev 03)

That's what it says for VGA, and I don't think I have the Restriced Drivers option. I checked, and it wasn't in Administration.

And hi ^_^

I have that card and compiz worked ''perfectly''.Maybe compiz is corrupt when you installed Ubuntu,if so go to Synaptics and reinstall all packages with Compiz in it(use search).Hope this helps.

---

### Post by overdrank on 2008-02-03
> **obliviousdream said:**
> 00:02.0 VGA Compatible Controller: Intel corporation Mobile 915GM/PM/GMS/910GML Express Graphics Controller (rev 03)

That's what it says for VGA, and I don't think I have the Restriced Drivers option. I checked, and it wasn't in Administration.

And hi ^_^

Ok for me I use the i810 driver for the graphics and also installed the 915 resolution from synaptic manager. To verify what driver is being used you can use this command ```
cat /etc/X11/xorg.conf
``` and it will be listed under the device section. The 915 resolution can be installed via synaptic manager located under system, administration.

---

### Post by icechen1 on 2008-02-03
> **overdrank said:**
> Ok for me I use the i810 driver for the graphics and also installed the 915 resolution from synaptic manager. To verify what driver is being used you can use this command ```
cat /etc/X11/xorg.conf
``` and it will be listed under the device section. The 915 resolution can be installed via synaptic manager located under system, administration.

the ''intel'' driver is better,sets resolution automaticly.

---

### Post by obliviousdream on 2008-02-03
None of them were installed...>_>

Hmm, well, I'm installing the now, so we'll see if it ends up working. I hope so.

I'm using the i810

---

### Post by overdrank on 2008-02-03
> **icechen1 said:**
> the ''intel'' driver is better

Whatever works for the OP :)

---

### Post by obliviousdream on 2008-02-03
Yay! It works now! ^_^

Thanks to both of you!

---

### Post by andrewyip on 2008-06-03
i'm having the same problem but my card is:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
and it has required drivers that are already enabled:
"NVIDIA accelerated graphics driver (latest cards)"

---

