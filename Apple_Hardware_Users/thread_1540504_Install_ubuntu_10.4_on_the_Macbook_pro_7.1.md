---
title: "Install ubuntu 10.4 on the Macbook pro 7.1"
date: 2010-07-27
forum: Apple Hardware Users
---

### Post by shangjieok on 2010-07-27
I was try to installed ubuntu 10.04 on the Macbook pro .But it was failed .I got following message:
/init: line 1: can't open /dev/sda: No medium found 

I have already Bootcamp to create a partition to install Ubuntu .

partition file system is FAT32.

anyone can help?

---

### Post by keegug on 2010-07-28
Hi

I was trying to install the 10.04 release too but it seems not working :/

after further research, I learnt that macbook pro **7.1** doesn't work with the last release (1004) due to the nvidia chipset MCP89. (source : [http://doc.ubuntu-fr.org/macbook_pro_7.1](http://doc.ubuntu-fr.org/macbook_pro_7.1))

new iso is available but sound doesn't work...wich can be  a problem for studio users.

Anyone can help ?

For me, the only solution could be installing a previous release of ubuntu but I am not quite sure it will be ok...How a previous release could be more efficient than the new one ?

---

### Post by benced on 2010-07-28
hi,

going through the same process too at the moment,

downloading the iso from the documentation page,

my mac is intel based though (not amd64) so not sure if it will work or not :S

will be keeping track of this thread...

---

### Post by shangjieok on 2010-07-29
Hi 

Thank you very much for your feedback .
my mac is intel based too ...I don't know why it is prompt:/init: line 1: can't open /dev/sda: No medium found
however when I try to execute "ls /dev/sda" under the ubuntu command line .it is success .

Is this  a bug of ubuntu ?

---

### Post by dgbarlow on 2010-07-29
Download and burn latest daily snapshot build.  The problem you are experiencing is a bug in a driver which prevents recognition of the sata hard drives.  This has been patched recently.

---

### Post by keegug on 2010-07-29
Yes indeed

I downloaded the lastest daily build and install it ... it seems to work 

-> [http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)

thank you :p

---

### Post by shangjieok on 2010-07-29
Really ? are you install on the intel based or amd64  ?

---

### Post by keegug on 2010-07-29
intel based. I don't think amd macbook pro exists

---

### Post by shangjieok on 2010-07-29
Thank you very much .I was installed ubuntu

---

### Post by shangjieok on 2010-07-29
Thank you very much .I was installed ubuntu success too ..
But The sound is not working ..did you got this problem ?  and it is very slow for boot from rEFlt .
Need pay long time for display rEFlt tool .

---

### Post by keegug on 2010-07-29
yes, sound off and disk acces is low. 

waiting for an upgrade soon :)

---

### Post by benced on 2010-07-29
update: the iso used from the documentation page has seemed to work okay for intel (even though it's labelled amd64)

no sound though, typing from ubuntu on macbook now

Update 2 : Sound working now

turns out all the instructions are here all along [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

Sound specific -> [https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound)
[]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483332")

---

### Post by dgbarlow on 2010-07-30
Don't worry too much about the use of the term amd64.  This is simply the description of the architecture and does not discriminate between Intel and AMD chips.  My understanding, (and please feel free to correct me if I'm wrong, as I'm not doing any reading to confirm my memory), is that Intel's vision for 64 bit computing was by way of its own architecture, Itanium, or IA64, which was not compatible with the old 32 bit x86 machines.  AMD, on the other hand, opted for a 64 bit architecture compatible with x86 machines.  AMD soon proved the winner and Intel soon supported it also.  I'm not sure of the current status of Itanium.

---

