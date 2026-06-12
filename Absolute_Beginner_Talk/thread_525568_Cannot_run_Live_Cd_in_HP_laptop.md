---
title: "Cannot run Live Cd in HP laptop"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by hardikorama on 2007-08-14
I have a HP pavillion notebook with an amd turion 64 x2 processor, 2 gb RAM and 160 gb hard disk. When I press enter at the menu of the live cd of Ubuntu 7.04 (Start or Install Ubuntu), It shows an "Bios Bug found" error. Also, during loading, it shows some microcode error. I can't even run the live cd, let alone install Ubuntu. Please help.

---

### Post by Ek0nomik on 2007-08-14
Out of curiosity, have you tried the Alternate CD?

---

### Post by hardikorama on 2007-08-14
Alternate CD? I havent tried anything like that. The one I tried had support for intel and amd athlton.

---

### Post by Ek0nomik on 2007-08-14
> **hardikorama said:**
> Alternate CD? I havent tried anything like that. The one I tried had support for intel and amd athlton.

The Alternate CD will support both of those as well.  It's just a text based installer as opposed to a Live CD where you get to try out the actual operating system.

I used the Alternate CD last night on an old box at a friends house, and I have also used it on two of the four boxes of my own.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Below the green 'Start Download' button is a checkbox to get the Alternate CD.  This will hopefully get you past any hardware issues you are having so you can deal with them after the install (if they still exist).

---

### Post by hardikorama on 2007-08-14
Well I havent tried the text based installer before. So I just want to know if it is easy to configure or not.

---

### Post by logos34 on 2007-08-14
> **hardikorama said:**
> Well I havent tried the text based installer before. So I just want to know if it is easy to configure or not.

I assume that HP notebook has windows installed.  If so check out this dual boot guide using the Alternate CD ('Ubuntu + NTFS')
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by hardikorama on 2007-08-14
Thanks for the link. I hope it's helpful.

---

### Post by Ek0nomik on 2007-08-14
> **hardikorama said:**
> Well I havent tried the text based installer before. So I just want to know if it is easy to configure or not.

Yeah, it's very easy.  It will walk you through each step one at a time.

---

### Post by Blutack on 2007-08-14
This is a known bug with some HP laptops.  The alternative install CD will not work either.  You need to append
noapic
to the boot options.
More info from
[http://www.linuxquestions.org/questions/showthread.php?t=574070](http://www.linuxquestions.org/questions/showthread.php?t=574070)
Hope this helps.

---

