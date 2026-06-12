---
title: "The problem of GRUB"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Sammora on 2007-01-12
The problem of GRUB 



My operating system is Windows XP SP2 , I installed ubuntu-alternate-i386.iso; as an experiment to identify the Linux installation was to Drive E devoted to this case and walked very beautiful, and I was pleased for two days ... Some of the programs were updated automatically ... The problems did not come up with only the issue of the Mount, which has tried repeatedly and carried out all that was required to no avail ... Not that there would be obscured. The problem does not lie here has been a problem and I am restart on one occasion for the transition from Ubuntu  to Windows XP, and was moving smoothly, if adopted at the start of the operation does not appear window select the operating system and shows that there Error in the GRUB tried repeatedly without success, which for me to go on the roller boot emergency delete the distribution and re-install Windows XP real I was happy with linux, but the problem of GRUB ... Wasted joy. Is experts find a solution or an explanation of this problem?! 

With a friendly and sincere respect.

---

### Post by rai4shu2 on 2007-01-12
I'm sorry, but I do not understand. Please consult this link for better help:

[http://www.ubuntu.com/community/forums](http://www.ubuntu.com/community/forums)

---

### Post by Wim Sturkenboom on 2007-01-12
I also don't understand, but let's try to make a summary:
[LIST]
[*]you had a mount problem; when and what are you trying to mount?
[*]next you removed Ubuntu (how) and the system did not want to boot (grub error)
[/LIST]
Is this a correct summary?


PS In my opinion, the font (size, alignment) that you used does not make your post readable.

---

### Post by Sef on 2007-01-12
So you have reinstalled XP and no longer have Ubuntu on your computer?  Is that right?

---

### Post by Sammora on 2007-01-12
> **Wim Sturkenboom said:**
> I also don't understand, but let's try to make a summary:
[LIST]
[*]you had a mount problem; when and what are you trying to mount?
[*]next you removed Ubuntu (how) and the system did not want to boot (grub error)
[/LIST]
Is this a correct summary?


PS In my opinion, the font (size, alignment) that you used does not make your post readable.


yes sir

i had a mount problem

and when i faced GRUB problem , I deleted the partition containing Ubuntu by using Hiren's boot CD

many thanks

I have understood my problems and I'll go to resolve it

---

### Post by Sammora on 2007-01-12
> **Sef said:**
> So you have reinstalled XP and no longer have Ubuntu on your computer?  Is that right?

I'll reinstall Ubuntu

many thanks

---

### Post by mikewhatever on 2007-01-12
Hope it works with no problems now. Just an advice, write in short sentences separated by dots. You might get more help this way.:D

---

### Post by Wim Sturkenboom on 2007-01-12
Sammora, for your info:
It was probably not necessary to re-install WindowsXP. When you removed Ubuntu, you also removed a part of Grub and that is probably why you could not boot anymore.
Next time when you have the same problem, boot from the Windows XP CD, boot into recovery mode and run ***fixmbr***. That should 'recover' Windows.
Please note that when you do this on a dual/multi boot Winodws/Linux system, you will loose access to other operating system(s).

And when you have the mount problem again, you can post it here and someone might be able to help.

---

### Post by Sammora on 2007-01-14
many thanks

I'll do

---

