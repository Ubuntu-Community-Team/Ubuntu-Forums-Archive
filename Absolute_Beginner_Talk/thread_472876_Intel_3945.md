---
title: "Intel 3945"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Nxion on 2007-06-13
Hi,

I am going to get a new laptop and was curious to know if the Intel 3945 is supported at all by Ubuntu. I am also curious to know if the Intel supports audit tools suck as aircrack, kismet, and various others.

Can some one help me please ?

---

### Post by Inxsible on 2007-06-13
I have a 3945 ABG wireless in my machine and it worked pretty much out of the box. 
 
About the aircrack and kismet, I have no clue

---

### Post by Nxion on 2007-06-15
Thanks Inxsible for the input. 

Any one else know the answer to my other questions ?

---

### Post by Bachstelze on 2007-06-15
Yes, it supports this kind of tools. You might need to recompile the driver to be able to use the monitor mode, tough.

---

### Post by jakev383 on 2007-07-09
As a reply to this.... I just moved up to 7.04 this weekend, and my 3945 worked out of the box. I had a Broadcom running ndiswrapper in here before.
Anyway, like I said, it worked perfectly. I also installed Kismet, and after configuring for my card (and diabling wireless in NetworkManager by right clicking and de-checking "Enable Wireless") Kismet worked perfectly as well. I have not tried the WEP cracking thing yet, but that will happen in the next week or two as well.
Good luck!

---

### Post by jakev383 on 2007-07-10
Next update....
I didn't get much time to mess with it, but I was able to put my 3945 into monitor mode, and used airodump to capture some stuff.  This would lead me to believe that I can crack the WEP on my home wireless, since the last thing to do would be to decrypt the packets.
Hope that helps some.

---

