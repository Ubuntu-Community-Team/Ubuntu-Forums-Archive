---
title: "[SOLVED] &amp;quot;Enable Alsa sequencer first by editing /etc/default/timidity&amp;quot;?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by lanchongzi on 2007-09-16
Hi there 

I have a fresh install of Ubuntu Ultimate 1.4
did the updates
used envy ( which comes with it ) and installed the Invidia drivers
and all the other stuff
installed Google earth, eva, skype, audacious, qcomix
then did a restart and it won't let me into the new Kernel *.*.16 I think
instead it says: "Enable Alsa sequencer first by editing /etc/default/timidity"

and that my InVidia is not configured correctly


????????????????????????????????????????


now I choose the old Kernel from the GRUB menu

how to proceed?
and what is that timidity ???


thank you in advance

---

### Post by por100pre1 on 2007-09-16
Timidity is a MIDI software synthesizer. That Timidity issue is very common, I don't think it's related. Try using the previous kernel first. Let us know if it works or not.

EDIT: This looks like a xorg.conf issue...

---

### Post by lanchongzi on 2007-09-16
I am using the previous Kernel and it works just fine

how to check "xorg.conf"

it also said so in that friendly little blue box that told me to rather go and hunt ducks then playing with computers :)

but i still don't understand.....:(

i read in another post that the new Kernel won't fit with the old NVidia drivers - so now I am going through the envy GUI again 

let's see what happens

---

### Post by lanchongzi on 2007-09-16
didn't work :(

it still says that the nvidia is not configured correctly :(

shouldn't i be changing "nvidia" to "nv"???

but where???

---

### Post by Bachstelze on 2007-09-16
Removed all the question marks from the thread title, one is enough.

---

### Post by por100pre1 on 2007-09-16
Try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and choose nv

---

### Post by lanchongzi on 2007-09-17
hihi Hymntolife you are right

that was just how it looked in my brain while encountering this problem :)

---

### Post by lanchongzi on 2007-09-17
por100pre1

should I do this in the previous kernel or in the recovery mode of the new - not working kernel? ( actually I didn't try if the recovery mode works or not )


so i did it in the previous kernel just now

"lanchongzi@lanchongzi-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
Password:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070917124208
lanchongzi@lanchongzi-desktop:~$                                                                           "

was that what should have happened?

---

### Post by lanchongzi on 2007-09-17
Thanks to you pro100pre1


That did it

I did it in the previous Kernel and it worked perfectly for the new one


Thanks a lot

---

