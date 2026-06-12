---
title: "Messed up boot splash screen"
date: 2007-01-06
forum: Apple PPC Users
---

### Post by gamgee911 on 2007-01-06
This is more of a cosmetic problem but on my PowerBook G4, when I boot Ubuntu 6.10 I get an ugly boot splash screen with the Ubuntu logo in inverted colors.  Is there a way to fix this? :-k   Thanks.

---

### Post by kidders on 2007-01-06
Hi there,

I have this problem too. I've also noticed an error message early in the boot process along the lines of "Cannot allocate resource region X of device XXXX:XX....". I can't help wondering if they're somehow related.

I hadn't been particularly bothered about it, but now that you've asked, I must see if I can pin it down.

---

### Post by calum on 2007-01-09
> **kidders said:**
> Hi there,

I have this problem too. I've also noticed an error message early in the boot process along the lines of "Cannot allocate resource region X of device XXXX:XX....". I can't help wondering if they're somehow related.

I hadn't been particularly bothered about it, but now that you've asked, I must see if I can pin it down.

FWIW, I don't think that error is related, I get it too but my boot splash screen is fine.

---

### Post by 0graham0 on 2007-07-14
i got the same problem (messed up colors on the boot splash screen (plus it looks almost like splotches of multi colored tv snow in places...)...after that everything (login, desktop, apps) looks fine. Like kidders, i get a "PCI...cannot allocate resorce region 2 error" on boot...anyone have any ideas, or can point me to a post on customizing your boot splash screen?

thanks

---

### Post by gamgee911 on 2007-07-19
As far as I can understand, having installed on some of my other Macs is its because of the non-NVIDIA support for ppc processors.  I could be wrong, but that's my understanding of the messed up screen.  Ati graphics cards seem to load the image just fine.  so wait till nouveau works - someday.

---

### Post by 0graham0 on 2007-07-20
Sounds about right...i'll try not to be too obsessive compulsive until that day comes...

---

### Post by vbbasti on 2007-10-09
To get this working you have to recompile the kernel with nvidia_fb support. After this, bootsplash looks fine and brightness-control works too.
To get this working out of the box please subscribe to the follwed bug report: [https://bugs.launchpad.net/ubuntu/+bug/137001]("https://bugs.launchpad.net/ubuntu/+bug/137001")
If you have an other solution without recompiling the kernel, please take some time and write me an answer.

Greetings Basti

---

### Post by rhetoric on 2007-10-09
I'm guessing the error messages you're seeing have something to do with the unsupported landline modem? Just a guess. I get it too. 2 messages.

---

### Post by chimaera on 2007-10-10
> **vbbasti said:**
> To get this working you have to recompile the kernel with nvidia_fb support. 


actually, you don't. see bug #21478 [1]. the latest posts suggest working solutions. 

[1] [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478)

---

### Post by gamgee911 on 2007-10-20
Thanks, works beautifully for me!

---

### Post by gspawn69 on 2007-10-23
I have a similar problem, but the majority of my boot screen looks fine, but the part of the screen with the progress bar is messed up. FYI, i'm using the boot splash with the blue techno look and the giant handprint on the right. The blue box next to it with the "Now loading Linux, the most advanced operating system in the world..." is totally blacked out. Everything else is fine though.

I tried using the fix on the link above, but it didn't work for me. I didn't have a yaboot.conf file in the /etc directory, and when I tried to type the "sudo ybin -v" it told me I got a bash message saying ybin couldn't be found.

Also, I just upgraded to Gutsy. I had a similar problem to this when I upgraded to Edgy, but upgrading to Feisty fixed it. There always seems to be some kind of issue with usplash. :P

---

### Post by chimaera on 2007-11-10
> **gspawn69 said:**
> 
I tried using the fix on the link above, but it didn't work for me. I didn't have a yaboot.conf file in the /etc directory, and when I tried to type the "sudo ybin -v" it told me I got a bash message saying ybin couldn't be found.

any chance you're running an intel-based mac and not a ppc?

---

