---
title: "Ubuntu installed, trying to setup Windows Boot Loader"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by uploadjoe on 2007-03-10
I have Ubuntu installed on my laptop (/dev/sda2) I can't seem to figure out how to copy in the info I need for the window boot loader in to the Fat 32 partition (/dev/sda4). I can't seem to do it from the live cd.

I was kind of following these [directions]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3")

but when I try what the directions say it doesn't work. Do I have to make a rescue CD?

Any help getting things set up would be great.

-- Jeremy

---

### Post by dhughes on 2007-03-10
So Windows is installed on sda1, Ubuntu is on sda2 and you don't want to use GRUB you want to use the Windows bootloader but that has to be installed, or you're trying to put it, onto sda4? 

 I'm not really sure, maybe someone else knows

  btw isn't sda4 your Swap partition?

---

