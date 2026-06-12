---
title: "Installing new RAM, adding memory"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by sean0michael on 2006-07-07
I'm looking to uprade my Ubuntu box from 190mb to 256mb by replacing a 64mb RAM card with one that is 128mb. I have tried just swapping the two, but according to SysInfo, my memory remains at 190mb. all memory is PC133.

While I may lack technical prowess, I'm not afraid of the terminal (If I was, I'd stick to Windows!). What do I need to do?

System Info:

Computer: HP Pavilion 6730
chipset: Intel 810
Sockets: Two 168-pin DIMMs
Maximum: 2 x 128 MB DIMMs

~Sean

---

### Post by mlind on 2006-07-07
Kernel picks memory changes on-the-fly. Does your bios know you've added more memory?

---

### Post by sean0michael on 2006-07-07
Does BIOS know? That's doubtful at best. Thank you for the suggestion. I'll research this on the web, but if you have any advice on what to do, any help would be... well... helpful.

~Sean

---

### Post by xael on 2006-07-07
> **sean0michael said:**
> I'm looking to uprade my Ubuntu box from 190mb to 256mb by replacing a 64mb RAM card with one that is 128mb. I have tried just swapping the two, but according to SysInfo, my memory remains at 190mb. all memory is PC133.

While I may lack technical prowess, I'm not afraid of the terminal (If I was, I'd stick to Windows!). What do I need to do?

System Info:

Computer: HP Pavilion 6730
chipset: Intel 810
Sockets: Two 168-pin DIMMs
Maximum: 2 x 128 MB DIMMs

~Sean

Excuse me for asking: where did you buy that RAM, Sean?, was it in good condition when you opened the package?. The reason I asked is because I've a similar machine and the new memory I added a while ago, worked right after being added.

---

### Post by sean0michael on 2006-07-07
No, I checked my BIOS and the readout I still get is this:

Istalled Memory   192MB
Memory Bank 0     128MB
Memory Bank 1     64MB

Is this the proper question for the Ubuntu forums? If not, then please disregard. 

~Sean

---

### Post by mlind on 2006-07-07
> **sean0michael said:**
> Does BIOS know? That's doubtful at best. Thank you for the suggestion. I'll research this on the web, but if you have any advice on what to do, any help would be... well... helpful.

~Sean

Does your machine count its memory when you turn it on?

You probably need to enter the bios to see that no setting forces the amount of RAM to lower than its supposed to.

---

### Post by sean0michael on 2006-07-07
Problem solved. The 64MB was mistaken for 128MB since they appear the same. BIOS recognizes the memory. Ubuntu boots fine and recognizes the additional memory. 

Sorry for the inconvenience and thank you for your time. 

~Sean

---

### Post by spoonmason on 2008-05-31
Platform: hp 2002-3, Ubuntu 8.04
Recently added RAM,512MB
BIOS reeds it.
Ubuntu does not.
???????
:guitar:

---

### Post by spoonmason on 2008-05-31
f

---

