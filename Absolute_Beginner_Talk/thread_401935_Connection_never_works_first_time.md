---
title: "Connection never works first time"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by toscy on 2007-04-05
Whenever I turn on my computer the connection always has to turn on after my computer.

So in other words, I have to turn on my computer and then turn on my router or if my router is already on and I want to turn on my computer then I have to take out and put back in the cable that goes into my computer to start it.

It's really ridiculous and I don't think that this always happened but I couldn't be sure on that.

I hope what I said is clear and if you want me to explain again then please ask.

Thanks for any help.

---

### Post by Skrynesaver on 2007-04-05
It sounds as though your boot sequence is incorrect and you are trying to connect before a needed resource is loaded, could you post the output of dmesg after booting

---

### Post by Delvien on 2007-04-05
I would try a different router

---

### Post by Skrynesaver on 2007-04-05
It could indeed be a symptom of a particularly slow DHCP server on the router

---

### Post by toscy on 2007-04-05
Thanks for the quick responses.

Delvien, I can't try a different router as I don't have another. There's a possibility I'll be getting another one soon but for now I'd like to try and get this sorted out even if it is a bit of a hassle.

Skrynesaver, how would I go about running dmesg? Sorry, I'm still very new to all of this.

---

### Post by Skrynesaver on 2007-04-05
From the top panel Applications>accesories>Terminal and enter dmesg

---

### Post by toscy on 2007-04-08
Thanks Skrynesaver, I know how to do it now if it ever happens again but for now it seems to be fixed!

I'm not sure what did it though or if it was anything at all.:)

---

### Post by Austin_KW on 2007-04-08
If you have problems on boot try taking the interface down and up again using the command line, this should be the same as unpluging & pluging the cable. 
```

sudo ifdown eth0
sudo ifup eth0

```
if this fixes you problems you can add the ifdown and ifup commands to /etc/rc.local so the will be run at the end of your boot sequence

---

### Post by toscy on 2007-04-09
Austin_KW, thanks for your help, I'm going to try this to prevent this happening again.

Could someone please look at this and tell me if I'm doing it right? I don't want to have problems booting into Ubuntu or anything. Here is my rc.local file:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

Should I be changing this to:

```
sudo ifdown eth1
sudo ifup eth1

exit 0
```

Thanks.

---

### Post by Austin_KW on 2007-04-09
Yes but you probably dont need "sudo" the boot sequence is run as root.

---

### Post by toscy on 2007-04-10
Thanks a lot, I've done it without sudo and I'll let you know how it goes. :)

EDIT: It works great.

---

