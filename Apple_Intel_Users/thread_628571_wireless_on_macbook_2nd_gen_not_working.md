---
title: "wireless on macbook 2nd gen not working"
date: 2007-12-01
forum: Apple Intel Users
---

### Post by tiiim on 2007-12-01
Hello,

I know this has prob been ask many times but i need help urgently. I am looking about coming back into the linux game after a few years off but having trouble making the wireless working on this 2nd gen macbook.

I have installed build-essential
I have installed the latest madwifi driver and after a restart doesnt work.
However its not reconise.
If i so a sudo wlanconfig ath0 it says no such device!
I looked at this thread for ndiswrapper [http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless+macbook](http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless+macbook) 
and this has not worked!
Can someone help me bit stuck, if i cant get this working will have to abandom my linux journey before i start :(

---

### Post by tiiim on 2007-12-01
hello,

dont worry i remove ubuntu, and resize Leopard's partition on the fly to cover the empty space... so back to normal (also very impress that Apple's disk utility has come a long way!)

I will give Linux a miss until the next release of ubuntu, i am planning to get it back into sometime but ill wait to ubuntu to support Apple's wireless out of the box... so to speak.:)

---

### Post by wigglydiggly on 2007-12-02
Wireless on the second gen macbook will work but you do need to tinker with it first.  it sounds like you were almost there.  You just need to use the daily build madwifi-ng.  I'm using 10-18-2007 and it works fine.  I understand the fustration but for me its all about the Ubuntu.  I only use OSX for skype video when on the road otherwise I've been very happy with Ubuntu on my second gen Macbook.

---

### Post by tiiim on 2007-12-03
Hello

I might try it again to night since i no now how to restore os x back to normal so we see :)

---

### Post by tiiim on 2007-12-03
hello
Thought ill update you! After a while of blacklisting drivers and adding drivers i decided to use ndiswrapper and extracter the driver from 10.5 cd, after installing it and adding the module to load to /etc/modules i restarted and it worked!!! whoo hoo

so this is resolved!:)

Now ill work on the rest of the ubuntu etc .. looking forward to coming back into the world of linux :)

---

