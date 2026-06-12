---
title: "tcpdump and wget"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by rubberduckie2003 on 2007-12-25
i want to capture using tcpdump HTTP request packets ( or packages , whatever they are called ) from a certain web page, let's call it X . i have to use for interrogation wget, i have to capture the first 15 packets from the communication, and i have to print them in ASCII format in output.txt .

any ideas? sound pretty ambiguous and i don't understand how i can do it ...

---

### Post by blueridgedog on 2007-12-25
Is this for a class?

Helping you may be cheating :-)

You can run tcpdump with:

 sudo tcpdump -i eth0

At that point, you can use your wget command to cause the traffic you want.

You can run tcpdump and direct the captured packets to a file with a command such as:

sudo  tcpdump -i eth0 > /home/USER/output.txt

(replace user with your user account)...

---

### Post by rubberduckie2003 on 2007-12-25
yes but when tcpdump starts i am not allowed to enter other commands such as wget link . how do i solve this ? and i thought u put the output of tcpdump with -w ..
i should group all this in one script ... does this help for the command sequence?

---

### Post by blueridgedog on 2007-12-25
While tcpdump is running, putting it output to the file, you open another terminal window and do your wget.

---

### Post by rubberduckie2003 on 2007-12-25
how do i do this in one single bash script ? that's what i have to do ... a bash script for this
not to complicated please, i'm only a beginner :)

---

### Post by Mba7eth on 2007-12-25
In not that expert in this ..... but i think you can use wireshark. I can capture all the packets transmitted by the NIC. you can download wireshark from repository.

---

### Post by blueridgedog on 2007-12-25
So, not only do you have to capture a tcpdump of a wget session, you have to do it in one bash script?

---

### Post by blueridgedog on 2007-12-25
This has some rough edges and could be done WAY better, it will need to be chmod 700 and run as root or sudo

Put this in a file called anything youwant (getanddump.sh for example). chmod 700 it (chmod 700 getanddump.sh for example).  Run with sudo yourfilename (sudo getanddump.sh for example)


#!/bin/bash
tcpdump -c 15 -i eth0 > /home/PUTYOURUSERACCTHERE/output.txt &
sleep 4
wget [www.PUTYOURSITEHERE.com](www.PUTYOURSITEHERE.com)
exit


This will wait for 15 packets, so if your wget only returns 14 or fewer, it will wait.  It sleeps 4 seconds in order for tcpdump to become initialized.  You can play with the length.

---

