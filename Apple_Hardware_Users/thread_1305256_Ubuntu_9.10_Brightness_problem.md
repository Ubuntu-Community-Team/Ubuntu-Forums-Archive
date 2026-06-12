---
title: "Ubuntu 9.10 Brightness problem"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by beyondallcontrol on 2009-10-29
Was wondering how to get the brightness working. My laptop is Macbook 4,1 and the graphics is intel gma965 (x3100 is the other name I think)

---

### Post by v41 on 2009-10-30
> **beyondallcontrol said:**
> Was wondering how to get the brightness working. My laptop is Macbook 4,1 and the graphics is intel gma965 (x3100 is the other name I think)

This is a bug related to  kernel modesetting (KMS).  KMS was turned off by default in earlier linux kernels, but is turned on by default in the 2.6.31 kernel used in Karmic.

I don't know of a solution to the KMS bug, but a simple workaround is to turn off KMS via the nomodeset boot option.  Eg if you're still using grub (rather than the newer grub2), then alter /boot/grub/menu.lst as follows,

```

kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=...  ro quiet splash nomodeset

```The one minor disadvantage I've found with nomodeset is that waking up from sleep takes about
15 seconds longer than it used to.  But that's a small price to pay for restoring control of screen brightness:)

---

### Post by samutz885 on 2009-10-31
Thank you! That fixed the problem now I can enjoy my new Ubuntu

How do I put Solved next to the topic...

---

### Post by pizzacake on 2009-10-31
> **beyondallcontrol said:**
> Was wondering how to get the brightness working. My laptop is Macbook 4,1 and the graphics is intel gma965 (x3100 is the other name I think)

The brightness keys weren't working with Karmic 9.10 on my MacBook 1.1 Intel GMA 950.  All I had to get them working is install a daemon called pommed.

$ sudo apt-get install pommed

Select archive repositories in software sources otherwise pommed won't be found.  Now my brightness keys work perfectly and KMS is still active.

---

### Post by v41 on 2009-10-31
> **pizzacake said:**
> The brightness keys weren't working with Karmic 9.10 on my MacBook 1.1 Intel GMA 950.  All I had to get them working is install a daemon called pommed.

$ sudo apt-get install pommed

Select archive repositories in software sources otherwise pommed won't be found.  Now my brightness keys work perfectly and KMS is still active.
There are at least two separate bugs affecting brightness on the Macs.  

Non-functioning brightness keys are a long-standing problem.  Pommed solves the problem for some people, though not for me.  I use the xbacklight command, and bind it to the brightness keys using the keyboard-shortcut GUI.

The kernel-modesetting problem is new.  It was introduced with the 2.6.31 kernel in karmic.  This bug makes the screen go to 100% brightness, ie painfullly bright, and it is not solved by pommed or xbacklight.

---

### Post by samutz885 on 2009-11-01
Out of curiosity what's the point of KMS (kernel modesetting)?

Small note it also works with grub2 but the file is /boot/grub/grub.cfg

---

### Post by Said Bak on 2009-11-06
Hi everybody,

I just upgraded to Ubuntu 9.10 and had the same brightness problem. I'm on a HP laptop though. 

The "pommed" suggestion worked here to! :)

---

### Post by samh785 on 2009-11-06
> **samutz885 said:**
> How do I put Solved next to the topic...
Go to the top of this thread and click on *Thread Tools*. There should be an option at the bottom of the menu that drops down to mark the thread as solved. :D

---

