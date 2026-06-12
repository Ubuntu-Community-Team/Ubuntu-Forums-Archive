---
title: "Macbook Pro 7,1 Problems with kernel 3.*.*"
date: 2012-05-27
forum: Apple Hardware Users
---

### Post by Caltac on 2012-05-27
Hi everyone,

I recently attempted to install 12.04 LTS on my macbook pro. It was previously running 11.04 just fine, but when I updated my OS (and consequently updated my kernel) I was unable to boot into 12.04. I booted using the old(er) kernel (2.6.39-0) and it works just fine. But is there any way I could run 12.04 LTS with the 3.*.* kernel?

Caltac

---

### Post by icyisamu on 2012-05-30
> **Caltac said:**
> Hi everyone,

I recently attempted to install 12.04 LTS on my macbook pro. It was previously running 11.04 just fine, but when I updated my OS (and consequently updated my kernel) I was unable to boot into 12.04. I booted using the old(er) kernel (2.6.39-0) and it works just fine. But is there any way I could run 12.04 LTS with the 3.*.* kernel?

Caltac

Are you using 32-bit or 64-bit Ubuntu?

I am currently using 12.04 64-bit (fresh install) on my MacbookPro 7,1 without any major issues.

---

### Post by 2F4U on 2012-05-30
What graphics card do you have? Some graphics cards, in particular nVidia and ATI, require the nomodeset grub kernel parameter to be able to boot to the desktop. After this is done, you will then have a chance to install a proprietary graphics driver (depending on your card) and then you usually don't need that parameter.

---

### Post by Caltac on 2012-05-30
I tried the nomodeset parameter, nothing changed. I still arrived at a black screen with white text that looks something like this:
```

[63.932006] Stack:
[63.932006] Call Trace:
[63.932006] <IRQ>
[63.932006] Code: ff c8 5d c3 66 0f (and the pattern goes on like that for a while)

```

Also, I tried booting in recovery mode and I received this error message:
```

rcu_sched_state detected stall on CPU 1

```

Any ideas on what is going wrong?

---

### Post by Caltac on 2012-06-01
UPDATE:
I just tried an EFI boot from the 64-bit install DVD for 12.04.
I edited the boot options and added nouveau.noaccel=1 but that didn't change anything either. 
I have searched numerous pages of information but none of them seem to help my situation. 

Does anyone have any suggestions at all?

---

### Post by Caltac on 2012-06-01
> **icyisamu said:**
> Are you using 32-bit or 64-bit Ubuntu?

I am currently using 12.04 64-bit (fresh install) on my MacbookPro 7,1 without any major issues.
I tried to boot from an install DVD (I tried both 32-bit and 64-bit) but neither of them will let me even get to the install screen. I boot from the CD and I just get
```

[63.932006] Stack:
[63.932006] Call Trace:

```

---

### Post by Caltac on 2012-06-06
Well, I fixed it myself. It turns out it was much easier than I expected.....

I had 11.04 installed on my HD, so I opened a terminal and typed

```

sudo apt-get install grub

```And when I tried to boot from the 12.04 64-bit install disc, everything worked like a charm. I guess I didn't have grub correctly installed on my HD?

---

