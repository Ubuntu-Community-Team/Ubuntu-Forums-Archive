---
title: "i am a noob, so i have a question"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-02-03
i got ubuntu 6.06 installed on the old computer. it loaed right up & now..my belkin wireless g usb network adapter (part#f5d7050) isn't recogized. i printed out the directions from wifidocs/device/belkin f5d7050 but before i start...

how do i follow those directions without being able to get on the internet?

should i be getting files off here then getting them to the other comp?

sorry for the dumb questions :P i'll probly have to edit ths post a few times as i come up w / more. :P

---

### Post by Infernal Byte on 2007-02-04
Depending on what the instructions say, you'll probably need to dial up or cable your connection until your WiFi is set.  I have the same problem as you to deal with in the next week or so.

...

---

### Post by jvc26 on 2007-02-04
Whether you have to connect/transfer files will depend entirely on what the instructions say.
Il

---

### Post by lunaz on 2007-02-04
update1

my setup is 1 winxp comp connected by ethernet to my shitty actiontec wireless router/modem combo, with qwest dsl. ubuntu dapper comp with belkin wireless usb adapter wich worked fine with winxp.

i got ubuntu 6.06 installed on the old computer today. it loaed right up & now..my belkin wireless g usb network adapter (part#f5d7050) isn't recogized. i printed out the directions from wifidocs/device/belkin f5d7050 but before i start...

how do i follow those directions without being able to get on the internet? the only way i can get that comp on the net is to get this one off the net, hook up 50ft phone line/ethernet to my modem/router combo thing, and plug it in there. but how would that help me fix wireless?

should i be getting files off this comp then getting them to the other comp?

sorry for the dumb questions :P i'll probly have to edit ths post a few times as i come up w / more. :P i can't wait to be totally windohs free eventually. ::beer::

hope some of this made sense,will b working on it more tomorrow..let me know if u need more info

update2

well after more digging around i found ndiswrapper-utils_1.8-0ubuntu2_i386.deb & ndiswrapper-1.37.tar.gz (probly typed those names wrong..). i put em on my usb flash drive, then stuck it in the ubuntu comp & dragged em to desk top. then went to terminal & tried

gail@gail-oldpos:~/Desktop$ sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.debSelecting previously deselected package ndiswrapper-utils.
(Reading database ... 69971 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.8-0ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

gail@gail-oldpos:~/Desktop$
i dunno what to do now haha.

edit: this is where i got some info
[http://www.linuxforums.org/forum/ubu...questions.html](http://www.linuxforums.org/forum/ubu...questions.html)

it's hard to find plain english stuff. if i have too i'll just drag out the 50 ft of phone line..... :(but any ways ill still need a plain english howto heh. i'm a day new.

---

### Post by lunaz on 2007-02-04
i found these instructions [http://ubuntuforums.org/showpost.php?p=1223311&postcount=2](http://ubuntuforums.org/showpost.php?p=1223311&postcount=2) and followed them up to step 7 where it hung up for a while, th en when it finally showed up, nothing about wireless, just eth & modem. i have both of them deactivated.

anything else?

---

