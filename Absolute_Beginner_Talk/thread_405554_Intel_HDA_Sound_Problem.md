---
title: "Intel HDA Sound Problem"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by xyntek on 2007-04-09
I have a Lenovo 3000 n100 with a Realtec id 682 sound card and Ubuntu 6.10 with latest update and kernel. I have the problem of no sound with the Intel HDA. I tryed the method of adding the line to the options files and nothing, and if I install a new alsa mixer driver and libs and all those stuff, my Ubuntu crash in the boot. I have being a week fighting with this and reinstalling my Ubuntu like 2 times peer day, please help me, thanks!!!

---

### Post by xyntek on 2007-04-09
Ok, I managed to install the latest driver, but still don have sound, any help please?

---

### Post by smoothone on 2007-04-10
The latest kernel update (2.6.20-14) killed my sound. Hp dv2120. This sucks, guess we have to wait for a kernel upgrade!:mad:

---

### Post by treesurf on 2007-04-11
Yup, the latest update did kill sound for my hda intel as well.

---

### Post by fhco on 2007-04-11
Argh, same here! Does anyone know why the update killed the sound? Is there a temporary fix, or will they be releasing some kind of fix shortly?

This is a pretty inconvenient time to not have sound at all on my only working laptop. :(

---

### Post by Bachstelze on 2007-04-11
Was it an update of the kernel or of something else that broke your sound ? Do you have sound whn booting the old kernel ?

---

### Post by fhco on 2007-04-11
I just installed a couple updates to the "kernel headers." It then asked me for a restart, and when I got back into my desktop I get errors all over the place when I do anything that requires access to the sound card, saying that a sound card cannot be located.

Is there a way to view previously installed updates? If so, I can post which specific updates were installed. Also, I am not sure how to boot into the old kernel.



Well I am glad that this is happening to a lot of folks, not just a few of us. Hopefully that means a fix will be available quickly. :)

---

### Post by Ripfox on 2007-04-11
Todays update made my sound card dissapear...I'm not going to complain, just looking for a solution. This is VERY widespread it seems...

HDA INTEL

---

### Post by deadowl on 2007-04-11
> **ripfox said:**
> Todays update made my sound card dissapear...I'm not going to complain, just looking for a solution. This is VERY widespread it seems...

HDA INTEL

Load the old kernel: No More Internet
Load the new kernel: No More Sound

What am I supposed to do...? 

I TRUSTED YOU UBUNTU!!!!

:'(

---

### Post by Bachstelze on 2007-04-11
Easy : switch to Gentoo :)

More seriously, what kind of "Internet" do you have ?

---

### Post by mikewhatever on 2007-04-11
Same sound issue on HP Pavilion 5000 after 2.6.17-11-generic kernel update. Just finished reinstalling the driver, and the sound is back.

---

### Post by Ripfox on 2007-04-11
Reinstalling alsa?  It doesn't even SEE my sound card anymore...how do you boot to an older kernel?](*,) ](*,) ](*,)

---

### Post by fhco on 2007-04-12
**uncensored's** post from page one of this thread fixed the issue on my computer:
[http://ubuntuforums.org/showthread.php?t=406676](http://ubuntuforums.org/showthread.php?t=406676)

---

