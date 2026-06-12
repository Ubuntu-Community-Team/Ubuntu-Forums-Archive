---
title: "How can I tell what driver is being used."
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by steven8 on 2006-11-14
How can I tell what driver is being used for my toshiba usb modem?  Ubuntu saw it right out of the box, but how can I tell what driver is being used?

Thanks.

---

### Post by steven8 on 2006-11-14
Okay, in the device manager, I see the line:

info.linux.driver strlist rndis_host

Am I getting close?

---

### Post by steven8 on 2006-11-14
I need to know this.  If anyone has an idea, please let me know.  I didn't install a driver, and Toshiba says it doesn't have Linux support, so Ubuntu used one of it's own drivers to make it work ootb.

How can I find out he name of the driver?

---

### Post by ReaderRat on 2006-11-14
Try this:
```
sudo lspci | grep VGA
```

---

### Post by steven8 on 2006-11-14
Hmm, will that work for a usb modem?  The pci and vga throw me off.

---

### Post by ReaderRat on 2006-11-14
> **steven8 said:**
> Hmm, will that work for a usb modem?  The pci and vga throw me off.
Sorry, I misread your post (only got one eye)...
I don't know if this will also list drivers...
```
sudo lshw | less
```

---

### Post by steven8 on 2006-11-14
Thanks.  I'll give it a go in the morning and let you know.

---

### Post by steven8 on 2006-11-15
worked like a charm!!  Thank you.

I am using driver=rndis_host

Now, one more question, would this driver be found as a physical file on my HDD, or is it just part of the Kernel?

---

### Post by skymt on 2006-11-15
> **steven8 said:**
> worked like a charm!!  Thank you.

I am using driver=rndis_host

Now, one more question, would this driver be found as a physical file on my HDD, or is it just part of the Kernel?

It's a kernel module, at "/lib/modules/*kernel-name*/kernel/drivers/usb/net/rndis_host.ko". However, if you're thinking of transferring this to another distro, I can tell you now that it won't work. Kernel modules need to be compiled for a specific kernel.

---

### Post by steven8 on 2006-11-15
Okey-dokey.  That was the reason.  I have tried a bunch of other distros, but none of them (not one) has been able to make my usb modem work.  Only Ubuntu.  I really enjoy seeing the different OS's, but you can't get the full experience if your devices won't work.  All I hear from the Kanotix forum is how usb modems are junk and I should get a different one.  What it tells me is that I am meant to use Ubuntu!!

Thanks.

---

### Post by skymt on 2006-11-15
Or, you can install Kanotix, get the kernel source package from Kanotix FTP, and compile rndis_host yourself. That can get sort of tricky though, so unless you have a good reason to use Kanotix, you may want to just stick with Ubuntu.

---

### Post by steven8 on 2006-11-15
Actually, I am going to be setting up a new computer once I get some memory for it, and I wanted it to be Linux only.  I've been searching to find a distro that is as close to the widnows experience as I can for my wife to accept it.

It is unimportant now, as she told me today that she doesn't care what I do with the new computer, as long as she can surf the net and play her online games.

I think we can do that with Ubuntu, don't you?  Besides, I like Ubuntu best to begin with!!

Thanks!

---

