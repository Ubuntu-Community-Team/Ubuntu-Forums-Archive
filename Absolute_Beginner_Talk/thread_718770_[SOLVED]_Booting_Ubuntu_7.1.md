---
title: "[SOLVED] Booting Ubuntu 7.1"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by zark06 on 2008-03-08
I have just installed Ubuntu 7.1 on a Dell GX260 with p4 2.4gig
From a purchased cd. I used the reformated method and Ubuntu is the only operation system.
I am new to Ubantu and know pretty much nothing.
My problem is when booting from the hard drive a message (grub loading 
please wait,press escape to enter menu) apears for about 2 to 3 seconds.
If I am fast enough to press escape I have 3 choices to make,  If I choose (Ubuntu 7.1 kernel 2.6.22-14 generic ) Ubuntu will load normally.
If I miss this window, I get a black screen and after about a minute the
keyboard locks up.
Is there a way to make this function automatic? Is this a normal function?
any info would be appreciated.

---

### Post by jken146 on 2008-03-08
That option should be the default (and so it should boot up to that on its own).  Let's check if this is indeed the case.

Please open a terminal (Applications -> Accessories -> Terminal) and post the output of the command ```
cat /boot/grub/menu.lst
```

---

### Post by zark06 on 2008-03-08
Reply to cat/boot/grub/menu.1st
No such file or directory

---

### Post by MeURi on 2008-03-08
The extension is LST, but lowercase - not 1st

---

### Post by unutbu on 2008-03-08
Also, make sure there is a space after 'cat'.

---

### Post by zark06 on 2008-03-08
Sorry I missed the space after cat
there are three groups of replys
what am I looking for?

---

### Post by unutbu on 2008-03-08
> **zark06 said:**
> The result is the same
reply to cat/boot/grub/menu.lst,  is no such file or directory

Are you typing it into the terminal *exactly* like your are posting it in the forum?
Notice there is no space between 'cat' and '/boot/...' in what you posted above (twice).

I get the 'No such file or directory' error when I type the command with no space.

---

### Post by zark06 on 2008-03-08
Sorry I missed the space after cat
there are three groups of replys
What am I looking for?

---

### Post by unutbu on 2008-03-08
Post the result of the command here and maybe one of us will notice what is wrong.

---

### Post by zark06 on 2008-03-08
Sorry for the delay, I was unable to copy the command lines to disk on Ubuntu,Here are the command lines
title     ubuntu 7.10,kernel 2.6.22-14-generic
root    (hd0,0)
kernel   /boot/vmlinuz-2.6.22-14 generic root=uuid=df 826ec6-0011           -4233-83d
f-6297c9f0cb9e ro quiet splash
initrd    /boot/initrd.img-2.6.22-14-generic
quiet

title     ubuntu 7.10 kernel 2.6.22-14-generic (recovery mode)
root    (hd0,0)
kernel  /boot/vmlinuz-2.6.22-14 generic root=uuid=df 826ec6-0011
            -4233-83d
f-6297c9f0cb9e ro single
initrd    /boot/initrd.img-2.6.22-14-generic

title       ubuntu 7.10, memtest86+
root      (hd0,0)
kernel   /boot/memtest 86+.bin
quiet

---

### Post by unutbu on 2008-03-08
Is this really your entire menu.lst, or are you skipping lines that are commented out (that is, start with '#')?

Buried among the commented-out lines, about 14 lines from the top, there should be uncommented lines that read

```

default       0
timeout      <some number>
hiddenmenu

```

Do you have those lines?

[http://www.gnu.org/software/grub/manual/grub.html#default](http://www.gnu.org/software/grub/manual/grub.html#default)
says that the default is assumed to be zero if no default line is given, so if you don't have a  default line, grub should be booting you using the first entry anyway. On the other hand, if you have something like 

```

default      1 

```
Then that would point us toward the problem.

---

### Post by zark06 on 2008-03-08
there was a lot more information had i scrolled down to see it              the default is 0
and time out is 3
next line is  ##hiddenmenu

---

### Post by unutbu on 2008-03-08
zark06, fiddling with grub is something that in my opinion should be done with extreme caution. I suspect there is something wrong with your menu.lst, but I don't know what. It may be helpful if you could post your entire menu.lst -- and I don't want you to retype it. There is too much risk of a typo. Is there a way you can save menu.lst on to a floppy, or a thumb drive or something, port it to a computer with an internet connection and copy/paste and post it here?

---

### Post by zark06 on 2008-03-09
UNUTBU  I have tried every thing that I can think of to copy the text 
to disk or usb flash memory with no sucess.
However I have resolved the problem.
I had installed Ubuntu 7.1 for 64 bit, I think this should have worked
on a Intel p4 and it did except for the boot problem.
I installed the Ubuntu 6.1 version 32 bit that came with a Ununtu for
dummies book.
It now boots normally from the hard drive I have not had time to check
other functions but so far so good.
Now I have to check for any upgrades to 32 bit 6.1 version.
Many thanks for your help and thanks to others that replied to 
my post Im sure that i'll be asking for more help in the future.
Zark06

---

### Post by unutbu on 2008-03-09
I'm glad you found a way around the problem!
Enjoy your new system.

PS If you want to be adventurous, I think version 8.4 should be released in a month. Maybe that will will work for 64bit.

---

