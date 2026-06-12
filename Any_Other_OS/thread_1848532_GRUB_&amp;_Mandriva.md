---
title: "GRUB &amp; Mandriva"
date: 2011-09-22
forum: Any Other OS
---

### Post by oscarivera9 on 2011-09-22
Has anyone tried the new Mandriva 2012?  I want to know if there are still problems with GRUB and Mandriva.  In the past, I've had to make a custom entry for Mandriva because for some reason GRUB didn't recognize it.  Once the custom entry was made, there were no problems, but up until that point GRUB's Mandriva entry would not boot Mandriva.  If, on the other hand, I were to use Mandriva's Legacy GRUB then IT would only recognize Mandriva.
So the question is, does anyone know if Mandriva 2012 is more compatible with GRUB than previous versions were?

---

### Post by wolfen69 on 2011-09-22
That's strange, because I've never had a problem with grub in mandriva. And after perusing the forums, I don't think it's an issue.

---

### Post by oscarivera9 on 2011-09-22
> **wolfen69 said:**
> That's strange, because I've never had a problem with grub in mandriva. And after perusing the forums, I don't think it's an issue.

It was a problem with me until I used that custom entry, like I said.  I know I'm not the only one, check it out:
[http://forum.mandriva.com/en/viewtopic.php?p=743185](http://forum.mandriva.com/en/viewtopic.php?p=743185)

And I believe this is where I originally found the answer to my problem way back then:
[http://melpctec.blogspot.com/2009/11/dual-booting-mandriva-2010-with-grub2.html](http://melpctec.blogspot.com/2009/11/dual-booting-mandriva-2010-with-grub2.html)

This problem was still there with the 2010 version of Mandriva, which was still using Grub Legacy.  So, I think the answer might lie in whether Mandriva 2011 is using Grub Legacy or Grub2.

---

### Post by oscarivera9 on 2011-12-12
I finally went ahead and installed Mandriva 2011 on my PC.  So now, Grub 2 gives me the option to boot into Ubuntu 11.10, Windows 7, or Mandriva 2011.  I installed the Mandriva Grub Legacy in Mandriva's own partition because my original plan was to keep using Ubuntu's Grub 2.  After initial installation, I had to boot into Ubuntu (Mandriva was not yet listed by Grub), and then: 
```
sudo update-grub
```After running the update-grub, Mandriva was listed as one of the choices, but when I tried to boot into it, I couldn't do it.  Instead, I got a black screen with a blinking cursor.  So then, I had to boot into Ubuntu again and create a custom entry for Mandriva.
Now, when I start my PC, Grub gives me the following options:

> Ubuntu with Linux kernel-3.0.0-14-generic
Ubuntu with Linux kernel-3.0.0-14-generic (recovery mode)
Ubuntu with Linux older entries
Mandriva Linux-2.6.38-12-generic
Mandriva Linux-2.6.38-12-generic (recovery mode)
Memory Test (memtest86+)
Windows 7 (loader) on /dev/sda1
Mandriva Linux 2011.0 (2011.0) on /dev/sda7If you notice, there are 2 entries for Mandriva (3 entries if you count the recovery option).  The very last entry is the one that I created as a custom entry, and it is the only one that works to boot into Mandriva.  

So, to answer my own question in case anyone else out there needs help with this issue:
The Grub provided by Mandriva doesn't recognize Ubuntu as an operating system, Ubuntu's Grub acknowledges Mandriva's presence but fails to boot into it unless you are able to create a custom entry for it.
In order to create Mandriva's custom entry, I had to first find out exactly what to write as a custom entry by following the steps outlined here:

[http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html#How_To_Boot_An_Operating_System_Directly]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html#How_To_Boot_An_Operating_System_Directly")

Then, after gathering the exact information needed for the custom entry I used the instructions here under Sub-Menu section 6 to actually create the custom entry:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


The good news is that Grub, Ubuntu and Mandriva do get along fine but some people might need to do a bit of extra work.

:guitar:

---

### Post by wolfen69 on 2011-12-12
Testing 123...... sorry about that

---

