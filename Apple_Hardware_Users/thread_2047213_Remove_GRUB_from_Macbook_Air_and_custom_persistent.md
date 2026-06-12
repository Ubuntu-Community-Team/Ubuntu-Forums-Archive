---
title: "Remove GRUB from Macbook Air and custom persistent USB"
date: 2012-08-24
forum: Apple Hardware Users
---

### Post by kasperelkjaer on 2012-08-24
Hello everyone.

I will describe my problem as best as possible.

I have to during my study using some software that will not run on mac. It's called Engineering Equation Solver and are made for windows. This will run through Wine on Linux, but not through Crossover for Mac. I have tried.

So I got the brilliant idea to try and install directly onto a USB on the Macbook Air 2011, same way as if it was a HDD.
I put the bootloader to install on sdc (USB pen), which I think would be the right thing to do.
BUT ... I made the mistake that I made &#8203;&#8203;it to download updates also. I believe that it is this action that made trouble. And now when I start my Macintosh it boots into grub rescue console every time if usb pen is NOT in. And if it IS in, GRUB starts up normally and I have the usual GRUB menu, but I can not boot OS X, only ubuntu, even though it shows in the menu. This can be circumvented by pressing the alt-key during boot.

My theory is that the updates have ****** the Mac and made &#8203;&#8203;a mess with MBR and EFI / GUID.

My question to you is: How do I remove GRUB from your Macintosh again and restore it back to normal, so it does not go to grub rescue console?

--------------------------------

The solution to my problem with the software would be to create a bootable USB with Wine and relevant windows programs installed.

But how do I work this problem out? I've tried to make a "persistent" USB with Unetbootin, but it does not save the changes I make.

Best regards, Kasper

---

### Post by kasperelkjaer on 2012-08-25
Come on guys... Nobody can help?

How do I rebuild my EFI?

---

### Post by kasperelkjaer on 2012-08-25
I fixed it!

Following the following link:

[https://discussions.apple.com/docs/DOC-3604](https://discussions.apple.com/docs/DOC-3604)

---

