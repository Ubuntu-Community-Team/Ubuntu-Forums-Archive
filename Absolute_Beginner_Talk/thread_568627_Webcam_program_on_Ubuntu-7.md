---
title: "Webcam program on Ubuntu-7"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by AkiraBergman on 2007-10-06
When I run the Webcam command I get the following error;

xxx@xxx:~$ webcam
reading config file: /home/xxx/.webcamrc
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no grabber device available

I checked to see the file /dev/video0 and it is not there. Anyway, why is it that the file /video0 is not in the /dev directory?

 I am trying to use Creative Webcam Vision. I read on the net that it works.

---

### Post by kvonb on 2007-10-06
I would suspect that if there is no /dev/videox then the cam isn't being detected properly :(.

From my limited knowledge, v4l (Video 4 Linux) automatically creates the dev file when it detects a cam.

What version of Ubuntu are you using?  Edgy and Feisty should both detect it.

Is there any /dev/videox device at all?

I plugged my cam in and it created /dev/video0, although it doesn't actually work, it still made the device.

Try running

lsusb

from a terminal and see if your cam is listed.

If not, it could be a USB fault.

---

### Post by AkiraBergman on 2007-10-06
Thanks for the quick reply.

I got Ubuntu-7.04. I suppose it is Feisty. As you said it detects it;

xxx@xxx:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 041e:4010 Creative Technology, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

I got no other Creative devs on USB so it should be the webcam. There is no /videox file in the /dev file. There should be one, shouldn't there?

---

### Post by AkiraBergman on 2007-10-06
I forgot to ask a question, if this webcam does not work.

Could you recommend a webcam that works?

---

### Post by kvonb on 2007-10-06
I'm not much help unfortunately, but I just checked for support of your cam and it doesn't seem to be there!

It might be a sub-model which is not yet supported unfortunately, I have the same problem with mine!

Have a look here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

This is the guy that writes the drivers for webcams, and I can't see your model listed.  Search the page for your model number given in the output from lsusb.

041e is the Vendor ID, but Product Id 4010 isn't listed :(.

That page is the best guide you will get for supported cams.

Regards, Kev :)

PS.  The BEST way to make sure it is supported is to take your computer (if you have a laptop!!) to the computer store and plug it in before you buy it!  Install camorama through synaptic, it's a cam viewer.  Or if you can persuade the shop to let you load a live copy of Ubuntu on one of their machines that would work too :).  But beware some are very hostile, an official Ubuntu CD would make a better case rather than a self-written copy.

---

### Post by AkiraBergman on 2007-10-06
Cheers mate!

---

