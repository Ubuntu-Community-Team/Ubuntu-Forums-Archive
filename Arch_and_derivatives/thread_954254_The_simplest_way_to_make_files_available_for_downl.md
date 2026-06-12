---
title: "The simplest way to make files available for download on my website?"
date: 2008-10-21
forum: Arch and derivatives
---

### Post by handy on 2008-10-21
It is my intention to keep the previous version of the kernel available on my website.  Every now & then it will be very helpful to someone, when they need it & can't get it anywhere.

Could someone please give me instructions on how you do this?

I have set up FileZilla, & can access my space, I have made the simplest of pages, & I have permission from my ISP, so long as I don't make money out of it I won't have to pay for the bandwidth.

Thanks in advance.

---

### Post by -grubby on 2008-10-21
upload the kernel and link to it now, I guess?

---

### Post by Bucky Ball on 2008-10-21
No instructions but neat, good on ya!

---

### Post by handy on 2008-10-21
> **nathangrubb said:**
> upload the kernel and link to it now, I guess?

I hope it is as easy as that, so the server & browser handles the rest without me having to use any code?

Anyway I just put the page up & the picture displays but no text! :lolflag:

I haven't done this stuff for so many years, & I wasn't particularly good at it when I did do it. :)

I really don't like reading technical books, for some reason searching on the web & reading off a screen is so much more comfortable to me these days.

Anyway, I'll get this site up & the kernel & link to it & see if I can download it.  Though I'll link to something smaller to test with.

---

### Post by Bucky Ball on 2008-10-21
Yep, just put it up there, check you site to make sure it is there and test to see that it downloads and that is it. Filezilla is a killer; just plop it in the right file on your server and you should be done.

---

### Post by handy on 2008-10-21
> **Bucky Ball said:**
> Yep, just put it up there, check you site to make sure it is there and test to see that it downloads and that is it. Filezilla is a killer; just plop it in the right file on your server and you should be done.

I've got it up, & it downloads fine, I put it up with a Mac, & I'm currently on Arch testing it.

I used the same tiny binary called backlight (which gives Mac LCD owners brightness control) & a dummy call to backlight from the link for the kernel, for the time being, until I get permissions sorted out in my mind.

What permission should I put on these binaries?

I'm too tired to think at the moment, so I just ask questions & follow blindly... :lolflag:

**[Edit/]** Removed address as a better solution can be found here:

***_[http://ubuntuforums.org/showthread.php?t=954481](http://ubuntuforums.org/showthread.php?t=954481)_***

---

### Post by mips on 2008-10-21
Hi handy,

Could you not use AUR for this? This way it's there for everyone to see searching AUR.

---

### Post by handy on 2008-10-21
> **mips said:**
> Hi handy,

Could you not use AUR for this? This way it's there for everyone to see searching AUR.

Why aren't there kernels in AUR?

I thought that for some reason they don't want them there.  Do you think that perhaps it is just that no body wants the job of maintaining them.

By the way, what should the permissions be for files that I want to serve?

---

### Post by mips on 2008-10-21
> **handy said:**
> 1. Why aren't there kernels in AUR?

2. I thought that for some reason they don't want them there.  Do you think that perhaps it is just that no body wants the job of maintaining them.

3. By the way, what should the permissions be for files that I want to serve?

1. No idea.

2. I was referrring more to the backlight app then the kernel

3. On a FTP server they are usually set to -rw-r--r--
This way only root can Read/Write and all others can only Read.

---

### Post by handy on 2008-10-21
> **mips said:**
> 1. No idea.

2. I was referrring more to the backlight app then the kernel

3. On a FTP server they are usually set to -rw-r--r--
This way only root can Read/Write and all others can only Read.

Thanks for the permission info'.

I expect I will put backlight in AUR, I just have to spend the time & learn how to do it.  It really should be there.

I'll talk to Misfit138 about this kernel business & AUR.  For all of the obvious reasons.

---

### Post by handy on 2008-10-21
***[Edit:]** I have removed the links for old kernel from here, the following instructions are a much better solution:*

***_[http://ubuntuforums.org/showthread.php?t=954481](http://ubuntuforums.org/showthread.php?t=954481)_***

[/Edit:]

It is my intention to get backlight into AUR at least. :-)

I know I'm shutting the gate after the horse has bolted on the current kernel bug, but next time there will still be a large number of people caught out without a backup in their cache & no easy way to get a copy of the superseded kernel.

---

### Post by mips on 2008-10-21
> **handy said:**
> 
I know I'm shutting the gate after the horse has bolted on the current kernel bug, but next time there will still be a large number of people caught out without a backup in their cache & no easy way to get a copy of the superseded kernel.

I have not bothered updating in a while so I'm missing this bug although I would have been fine as I dont clear my cache that often. Sure it takes up space but I dont mind. After reinstalling KDEmod4 a few times in the earlier days I came to appreciate this things called 'cache' living on my HD :)

---

### Post by handy on 2008-10-21
> **mips said:**
> I have not bothered updating in a while so I'm missing this bug although I would have been fine as I dont clear my cache that often. Sure it takes up space but I dont mind. After reinstalling KDEmod4 a few times in the earlier days I came to appreciate this things called 'cache' living on my HD :)

I don't clear it either, I may in future, but I will manually go through & pick what stays & what goes.

Did you see my post on accessing old kernels, it is gold imho. :lolflag:

I now know why kernels are not in AUR, & I no longer need to work towards serving them myself.

***_[http://ubuntuforums.org/showthread.php?t=954481](http://ubuntuforums.org/showthread.php?t=954481)_***

---

### Post by mips on 2008-10-21
> **handy said:**
> 
I now know why kernels are not in AUR, & I no longer need to work towards serving them myself.

***_[http://ubuntuforums.org/showthread.php?t=954481](http://ubuntuforums.org/showthread.php?t=954481)_***

Thanks, clears that up for me. I'm just wandering about some stuff I have seen in AUR as it seems like duplicates of what is in the repositories, maybe they did not read the same link you did :lolflag:

---

