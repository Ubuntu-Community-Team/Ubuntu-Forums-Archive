---
title: "Installing New Video Card Help"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-06-21
Hello all,

   Well I have installed Ubuntu, Kubuntu and Xubuntu on a few different machines to get a feel for the install and wireless fixes. Now I have a problem.

   I want to install a machine for my own use and have a HP Pavilion 512w. Yesterday I added another 256MB Ram for a total of 512 MB, added a new 160 GB Hard disk and bought an Nvidia 550 /256mb ram.

   The RAM and HD are no problem, but when I add the video card, I cannot run the live CD. The BIOS does not give me the option to disable the onboard video although it has the option to select the type of video card you have installed (PCI or AGP) I have the PCI version because the MB does not have an AGP port.

   If I remove the Video card and only use the on board video, I can boot and install the live CD. With the new video card, I get to the point where it start gdm and then the screen goes black, but no video, there is some scrambled video on the onboard card though.

   It is almost like the live CD is trying to use the Nvidia drivers on the on board video.

   I would REALLY like to use this card, can someone help me please? Please?

Regards,

Joe Hildreth

---

### Post by wjhildreth on 2007-06-21
And I almost forgot, HP does not have any BIOS updates on their website for this machine.

Regards,

Joe

---

### Post by phr0ze on 2007-06-21
Often these systems have a jumper on the motherboard to disable the onboard video card. What is the mobo model number and we may be able to look it up for you.

---

### Post by wjhildreth on 2007-06-21
I am at work and the machine is at home. When I get home I will look for the number and post here. Thanks.

Joe

---

### Post by phr0ze on 2007-06-21
I hadn't realized it was a pre-built machine. Dont worry about the motherboard model number. Just look to see if you have a jumper on the motherboard which indicates some ability to turn off video. It would normally be around the CPU.  Also, if it doesn't see if in the BIOS where you specify video memory if you can set the memory to 0 or disable. Who knows at this point. I did some research on the HP and there doesn't seem to be much hope in disabling the video card.

Hopefully someone here will know how to handle the two video cards so they can exist peacefully. Perhaps install ubuntu with just the onboard, then add the other card after.

---

### Post by wjhildreth on 2007-06-21
Thanks for the help.

I will look and see if there is a jumper on the mobo. The best the BIOS offers is to set the video ram at either 512K or 1M. There is not an option in the bios to disable the on board video.  :-(

I have Ubuntu installed now with the onboard video, does anyone know how I can add the Nvidia card (sort of like a dual system) but just use the Nvidia for the desktop? I hope that sounds right.

Regards,

Joe

---

### Post by wjhildreth on 2007-06-21
Well, there was no jumper on the motherboard, but I installed the card, started in recover mode???

Ran the xorg -config and tested the file. It gave me a gui with an X pointer so I copied it over to the /etc/X11/ folder and rebooted.

Well all is working fine, although I am wondering, if I am not using the on board video, should I remove it from the config file? or does it matter.

BERYL is just TOOOOOO KEWL!!!

Thanks Ubuntu Team for all your work! And to the members who keep helping me out.

Regards,

Joe

---

