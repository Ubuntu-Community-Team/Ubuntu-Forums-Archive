---
title: "Dualt boot"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by balvincriffa on 2007-11-29
(Excuse my ignorance but I really am a beginner)

Why is it neccessary to install Windows XP before the UBUNTU linux OS?

Thanks.

---

### Post by skymera on 2007-11-29
its not.

its just if you install XP after ubuntu, it overwrites you bootloader.

so install XP first saves time.

---

### Post by quandary on 2007-11-29
> **skymera said:**
> 
so install XP first saves time.

No it doesn't. It saves time if you're gonna use grub, but it's a bad idea to use grub, in case you're gonna reinstall windows, or install a newer version of Windows...
I would not recommend using grub in the MBR.

---

### Post by teryowen on 2007-11-29
Only because when you install windows second it will over write the MBR to boot windows and then you will have to set up the MBR and GRUB so that you can boot into ubuntu.

But if you install windows first and then Ubuntu, ubuntu takes care of the MBR and grub and makes it right away so you can boot into both with no trouble, or re setting up

---

### Post by ptn107 on 2007-11-29
You should listen to the posts above.  Installing Ubuntu after windows saves you the frustration of reinstalling GRUB to your MBR.  Windows would overwrite your MBR otherwise, and you wouldn't be able to boot Ubuntu.

---

### Post by quandary on 2007-11-29
> **ptn107 said:**
> You should listen to the posts above.  Installing Ubuntu after windows saves you the frustration of reinstalling GRUB to your MBR.  Windows would overwrite your MBR otherwise, and you wouldn't be able to boot Ubuntu.

Nonsense, it's better to install Grub in the MBR of the second partition, and use NT bootloader to load linux.
better, because you can reinstall windows & linux everytime you wish. Otherwise you will get into trouble.

---

### Post by Bigbird999 on 2007-11-29
This is the absolute beginners forum so how about giving advice for beginners and take your "expert bickering" outside.  If you think about how confusing it is for a newbie to get conflicting advice from 2 experienced posters and then get into an argument about whose method is better, you might stop.

Obviously, it is far easier for a newb to do it by installing Windows first, because you don't have to screw around with GRUB and MBRs etc,  

I am a newb and this is one of the most frustrating things about this forum.  Almost every question has several right answers.  For newbs, the easiest way is usually the best.  

So, OP, one newb to another, do yourself a favor and install Windows first.

BB

---

### Post by teryowen on 2007-11-29
Ive been with ubuntu for a few weeks now --> im a nood,
but ive learned quite a bit and grub is definitly easier.

---

### Post by quandary on 2007-11-30
> **Bigbird999 said:**
> 
I am a newb and this is one of the most frustrating things about this forum.  Almost every question has several right answers.  For newbs, the easiest way is usually the best.  

So, OP, one newb to another, do yourself a favor and install Windows first.
BB

Well sorry, yes installing Windows first and Linux afterwards is easier of course.

However, Linux first is not that much more complicated, and the easiest way is not always the best way...

Well ok, newbies do WinXP first if you don't understand much about computers.

But the point is, that if you later install a new version of windows (eg. Vista), Vista will erase the MBR (Master Boot Record), hence you will be unable to boot Linux.

And reinstalling Grub is much more trouble than the 3 mouseclicks to add Linux to the NT bootloader.
Besides, Grub is buggy because it mixes up drive mappings when the boot order is changed...
But i suppose that this too is not good for the beginner forum ;-)

So ->Newbies = XP first
    -> nerds & geeks = Linux first

---

### Post by pilli on 2007-11-30
Any chance of sparing 10 minutes explaining the NT bootloader way.  Would be useful.  What do we need, how do we do it?

Would obviously raise the nerd/geek quotient a little bit. :lolflag:

---

### Post by frank002 on 2007-11-30
I am a newbie also and have a question about dual booting. I assume the original poster  here has both OSs on the same hard drive. I have Windows on hard drive 1  and Ubuntu on hard drive 2. If I have to reinstall Windows, what do I have to do to keep dual boot? By the way, I had Windows first, then I installed Ubuntu.

---

### Post by meierfra on 2007-12-01
There is no compelling reason to install windows before ubuntu
There is no compelling reason to install ubuntu before windows.
There is no compelling reason to use NT Bootloader rather than grub
There is no compelling reason to use Grub rather than the NT Bootlaoader.

If you install install ubuntu after windows, ubuntu might erase windows.
(search the forums, it happened today)

If you install windows after ubuntu, windows might erase ubuntu
(search the forums, it happened today)

If you use the NT Bootloader and then decide to  get rid of Windows, you will have   rewrite the MBR to be able to boot into Ubuntu.
(search the forums, it happened today)

If you use Grub and then decide to get rid of Ubuntu you will have to rewrite the MBR to boot into Windows.
(search the forums, it happened today)

Install windows  before ubuntu saves you a few minutes setting up the boot loader afterwards.  (Because ubuntu  automatically recognize windows, but windows does not recognize ubuntu). But those few minutes are to insignificant to really matter.


[Reinstalling Grub]("http://ubuntuforums.org/showthread.php?t=224351") is  just as easy as [fixing the Windows MBR]("http://http://ubuntuforums.org/showthread.php?t=616540#2")

---

### Post by meierfra on 2007-12-01
> If I have to reinstall Windows, what do I have to do to keep dual boot?

See this link:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")


It tells you how to reinstall grub from the Ubuntu LiveCD.

But if can  switch the boot order in the bios I suggest to do the following now:

1) Install   Grub to the MBR of the ubuntu drive. If you read the above link, you should be able to figure out how to do that  (you don't need to use the LIveCD, it works  just as well from ubuntu). In addition you will  need to edit the file /boot/grub.menu.lst (basically   have to change all (hd1,x) to (hd0,x)).   

2) Fix the MBR of the Windows drive: There are lost of ways to do that, see for example 
[http://ubuntuforums.org/showthread.php?t=616540#2]("http://ubuntuforums.org/showthread.php?t=616540#2")
And  if you want you can add Ubuntu to the NT bootloader (its easy in Vistas a little bit more work in Windows)

After that you can boot from either drive and still get the choice to boot into windows  or ubuntu. And deleting one of the OS's won't disturb the other.


If you need help with 1) or 2) just ask.

---

### Post by frank002 on 2007-12-01
Thank you

---

