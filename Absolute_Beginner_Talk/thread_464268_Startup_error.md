---
title: "Startup error"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by perrybergmann on 2007-06-04
--------------------------------------------------------------------------------

I have no idea why it's happening, but I had the exact same error, and here's how I fixed it:

At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. Append 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot. Dapper should then boot normally. 

To make these changes permanent, do the following:

I did this, but the options are as follows:

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic(recovery mode)
ubuntu, kernel 2.6.20-15-generic
ubuntu, kernel 2.6.20-15-generic(recovery mode)

Which of these do I need to edit to change this around?

---

### Post by southernman on 2007-06-04
My first thought would be to simply uncomment the "16" flavor by adding "#" (no quotes of course) to the begining of these two lines:


> Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic(recovery mode)
So they now look like:

> #Ubuntu, Kernel 2.6.20-16-generic
#Ubuntu, kernel 2.6.20-16-generic(recovery mode)

You could also edit your **see below** and change the grub option to enter the menu from 3 seconds to something a little slower (10 or so), where you can then select the kernel flavor you prefer.

HTH's in some way.

[edited] Sorry, the correct path to the grub menu file is /boot/grub/menu.lst~ [/edited]

---

### Post by sailor2001 on 2007-06-04
in terminal:  sudo gedit /boot/grub/menu.lst   and change default grub to 3 from 0

---

### Post by southernman on 2007-06-04
> **sailor2001 said:**
> in terminal:  sudo gedit /boot/grub/menu.lst   and change default grub to 3 from 0
The better method of running gui apps as root is gksudo.

If you change it to 0 then grub loads the 1st in this list without you having time to hit the esc key and select which one you prefer.

---

### Post by Rui Pais on 2007-06-04
> **perrybergmann said:**
> --------------------------------------------------------------------------------

I have no idea why it's happening, but I had the exact same error, and here's how I fixed it:

At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. Append 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot. Dapper should then boot normally. 

To make these changes permanent, do the following:

I did this, but the options are as follows:

Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic(recovery mode)
ubuntu, kernel 2.6.20-15-generic
ubuntu, kernel 2.6.20-15-generic(recovery mode)

Which of these do I need to edit to change this around?

Seems none of those. 
You mention dapper and 2.6.15-25 kernel and those above are the feisty kernels...
something is wrong, you need to give more info. 

> **southernman said:**
> The better method of running gui apps as root is gksudo.

If you change it to 0 then grub loads the 1st in this list without you having time to hit the esc key and select which one you prefer.

no, default is to set the default kernel (line) to boot. The option that reduce (or made nule) the menu time is: timeout.

---

### Post by southernman on 2007-06-04
I stand corrected. Thanks for clarifing this Rui Pais.

---

### Post by perrybergmann on 2007-06-04
I was qouting that from another board. I found that while researching my problem and that was the closest I could find to my exact problem. The four opitons that I listed are the ones thar are given to me as I am running feisty.

---

### Post by Rui Pais on 2007-06-04
> **southernman said:**
> I stand corrected. Thanks for clarifing this Rui Pais.
no prob :)

> **perrybergmann said:**
> I was qouting that from another board. I found that while researching my problem and that was the closest I could find to my exact problem. The four opitons that I listed are the ones thar are given to me as I am running feisty.

sorry your 1st post is confuse (use the buttons above the frame where one types to post to add quotes and code... make it easy to others read.)

If add that option to kernel line solves your problem you must had it to all kernel you use, or at least to the last, that presumably is the one you use now. 
You can make those options automatically added on future kernel by edit on menu.lst the option:
# defoptions
as an example:
```
# defoptions=quiet splash
```
could  became:
```
# defoptions=quiet splash noapic
```
And: DO NOT ADD OR REMOVE ANY # SIGN TO BEGIN OF LINE! 
(Just keep the one that exist now)

---

### Post by perrybergmann on 2007-06-04
thank you.

---

