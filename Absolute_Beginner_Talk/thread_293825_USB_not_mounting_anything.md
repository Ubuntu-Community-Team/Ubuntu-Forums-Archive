---
title: "USB not mounting anything"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Mr. Blake on 2006-11-05
When I plug a device like an external hard drive or my iPod my computer reads that the hardware is there, but it doesn't mount it. It give the message 
"Unable to mount selected volume."  When I click the details link I get the message, "error: could not execute pmount."  This is posing quite a problem because I need to back up my computer. Any suggestions?

---

### Post by dmizer on 2006-11-05
think you'll find your answer here: [https://launchpad.net/distros/ubuntu/+source/pmount/+bug/49655](https://launchpad.net/distros/ubuntu/+source/pmount/+bug/49655)

---

### Post by Mr. Blake on 2006-11-05
I read through the the link that you posted.  I think it might help a lot.  The problem is, is that I don't understand how to activate the patch.  I know how to use the terminal fairly efficiently, I just don't know what to type.

---

### Post by dmizer on 2006-11-05
sorry, you won't actually have to apply the patch ... you'll have to edit /etc/pmount.allow and add:
```
exit(-1); -> fclose(fwl); return 0;
```
to the end of the file

let me know if that works, and if it doesn't, what locale are you using?

---

### Post by Mr. Blake on 2006-11-06
I tried the edit /etc/pmount.allow and I got a message saying
```
Warning: unknown mime-type for "/etc/pmount.allow" -- using "application/*"
Error: no write permission for file "/etc/pmount.allow"
```
I'm using in English, in the U.S. I'm running on a hp pavilion mx70 that I absolutly despise. I've had my friend come over to fix it more times than I can count. He has commented that this computer hates the world and everybody in it.](*,)

---

### Post by dmizer on 2006-11-08
you'll have to do this from the command line.  you need root rights to write to this file.  you can't just click on it, open it, and change it because it's a system critical file.

try this in the command line (assuming you're using gnome):
```
gksudo gedit /etc/pmount.allow
```

---

### Post by givré on 2006-11-09
Hum, the fix was released, and it was due to some special locale. So not sure  this is the problem.
You should rather try to find why pmount don't work.
In a terminal, try :
```
PMOUNT_DEBUG=1
pmount-hal /dev/sda1
```

---

