---
title: "URGENT! WUBI Install of Ubuntu, now i can boot Vista!!! PLease Help"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by aidope on 2007-09-28
Hi. My name is Aidan and I have had a huge problem for the last 4 weeks. Here goes,

4 weeks ago I installed Ubuntu using Wubi. It worked fine! I even got Compiz working on it. But soon after I installed Ubuntu, I wanted to upgrade my Premium version of Vista (the one with the wubi install on it) to Vista Ultimate. I did that and everything seemed to be going fine until the Vista Ultimate Installation was complete and it asked me to restart. Now every time i turn my laptop on, I get a black screen saying this;

----------------------------------------------------------

Booting 'Windows Vista'

acpi
Vista Loader2.1.2

 ACPI: Reclaim Memory not found!
Done!
fallback 1
find --set-root /bootmgr

Error 17: File not found
 Booting 'Windows NT/2000/XP'

fallback 2
find --set-root /ntldr

Error 17: File not found
 Booting 'Enter Command Line'

Boot Failed! Press any key to enter command line.

--------------------------------------------------

When i press "any key" I get this screen;


--------------------------------------------------

GRUB4DOS 0.4.3 2007-03-13, Memory: 638k / 501M, CodeEnd: 0x3D7BC

[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists the possible
completions of a device/filename. ESC at any time exits. ]

grub> _ 

--------------------------------------------------

My Vista Install is on partition C with Wubi (Ubuntu) installed on it. I have Xp Pro on Partition D as a standalone install. None of these operating systems will start and as you can imagine its very frustrating. Any help would be most welcome. Even if someone could tell me how to format my HD without being able to boot into an OS. I would loose out on some very valuable information by formating but at this stage I dont think I have any other choices, or do i?

---

### Post by nowshining on 2007-09-28
"Vista Install is on partition C with Wubi (Ubuntu) installed on it"

is most likely ur problem - you'll have to do a backup if not then format drive C:\ wholly and then install Vista first and then ubuntu. :)

---

### Post by meborc on 2007-09-28
just use any linux live cd... boot it up... transfer your data from hard drive to dvd's or external drive... insert win cd... install... etc etc...

i would NOT recommend wubi... use normal partitioning and install instead

---

### Post by aidope on 2007-09-28
Thanks for your quick replies ppl. I don,t have the facility to back-up or restore as I cant boot into any OS. Could you send me a link to download a bootable live cd Meborc. Thanks guys.

---

### Post by w4ett on 2007-09-28
Here is the official Ubuntu download link:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

