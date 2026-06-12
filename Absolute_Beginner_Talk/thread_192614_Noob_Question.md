---
title: "Noob Question"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by markfasano on 2006-06-08
I have a Linux newbie question *par excellence:* the following is a sample of some commands to install XMMS:

sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3 sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list sudo mv /tmp/defaults.list /usr/share/applications/defaults.list sudo rm -f /tmp/defaults.*

Now, I can copy and paste each of these lines into Terminal one by one and watch the fun. What would happen if I copied the whole sequence and pasted it in Terminal? Would it run the commands in order, or just freak out and do nothing?

---

### Post by Dr. Nick on 2006-06-09
i think it would freak out on ya and say something along the lines of "command not found"
 
Also xmms is installable with synaptic much easier

---

### Post by darkali on 2006-06-09
To get the desired effect just put
;
after each line. (That's just ";" without quotes).

---

### Post by Dr. Nick on 2006-06-09
[quote=darkali]To get the desired effect just put
;
after each line. (That's just ";" without quotes).[/quote]

Ah cool, I figured you could put them in a script but didnt know about the : trick

---

### Post by markfasano on 2006-06-09
great tip, thanks.

---

### Post by nanotube on 2006-06-09
[QUOTE=darkali]To get the desired effect just put
;
after each line. (That's just ";" without quotes).[/QUOTE]

it is safer to put "&&" after each line, rather than ";". && will ensure that subsequent commands are run only if the previous ones completed successfully, whereas a simple ; will result in the rest of them still attempting to do stuff, even if some previous command returned an error.

("man bash" for more detail. :) )

---

### Post by markfasano on 2006-06-09
yeah I ran into that. thanks for the clarification.

---

