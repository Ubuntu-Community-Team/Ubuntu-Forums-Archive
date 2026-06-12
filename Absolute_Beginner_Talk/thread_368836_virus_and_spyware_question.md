---
title: "virus and spyware question"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-02-23
i know theres very few viruses for ubuntu but ive got my windows xp hard disk mounted in ubuntu so i can transfer files etc. if there are infected files on my windows disk can they get into ubuntu and infect that? i do internet banking and the like and am kinda paranoid about getting my details read.

thanks

---

### Post by fusiachi on 2007-02-23
The short answer: it's an extremely long shot.

---

### Post by IYY on 2007-02-23
No, they can't.

---

### Post by darkeale on 2007-02-23
cool thanks guys. i guess my paranoia can ease now since im not running windows

---

### Post by Patrick K on 2007-02-23
If you can still boot windows, you might want to run an AV program on it.

---

### Post by MasterOfDisaster on 2007-02-23
If you use files downloaded from Ubuntu on your Windows machine, you can use ClamAV to scan them before you they can wreak your Windows install.  Handy.

---

### Post by darkeale on 2007-02-23
yeah its clean. none of my spyware programs work anymore tho. even if i reinstall them and ive tried loads of different ones. annother of my reasons for switching to ubuntu

---

### Post by darkeale on 2007-02-23
thanks. yeah i use clamav. windows is hardly gonna be used tho. just for printing and...nope thats about it. so long as i know my ubuntu is safe. thanks guys

---

### Post by speeddemon8803 on 2007-02-23
They CAN infect your ubuntu partition IF you have WINE installed and you somehow transfer the viruses over to your ubuntu partition then run them in wine...thats about the only way I know how it could possibly do that.

---

### Post by darkeale on 2007-02-23
thats ok. i dont use wine. i read the thread by the guy who ran a virus in wine just to see what happened. pretty funny stuff

---

### Post by ramjet_1953 on 2007-02-23
One area that is growing is exploitation using rootkits.

It is becoming quite a problem on Windows machines and there is a possibility for problems with Linux as well.

There is a package available on Synaptic called Check Rootkit (chkrootkit).
I run it onece a week, just to be sure.

Regards,
Roger :cool:

---

### Post by darkeale on 2007-02-23
yeah ive got that and rkhunter. 

i just ran rhunter and it came up with this 


* Filesystem checks
Checking /dev for suspicious files... [ OK ]
Scanning for hidden files... [ Warning! ]
---------------
/etc/.pwd.lock /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools
---------------
Please inspect: /dev/.static (directory) /dev/.udev (directory) /dev/.initramfs (directory)

anything to worry about?

---

