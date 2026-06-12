---
title: "gui halted after changing video card"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by SonicSteve on 2006-07-14
Hi There,
I think my title says most of what you need to know. 

I had a really old ati rage agp card and I decided that I would change it out for a slightly less old 32mb nvidia card. 

After doing this I could no longer load into the gui. I unfortunately didn't write down the message but, here is my question.

Is this a normal thing? Is there a special way to upgrade hardware? 
Or... should this have worked?

Thanks

---

### Post by rowanparker on 2006-07-14
You need to change the display drivers.
Run ```
dpkg-reconfigure xserver-xorg
``` From a terminal.

---

### Post by SonicSteve on 2006-07-14
Thanks,
So the process is then;
Run the command,
shutdown the system
change the card
reboot

or 
shutdown
change the card
get the error
run the command

coming from windows (from the beginning) both ways seem possible but which is it?

---

### Post by autocrosser on 2006-07-14
The Linux way>>
 
Shut down
Install new item(s)
Reboot
Reconfigure
Enjoy your new stuff
 
NO Need to do mutiple reboots!!:-D

---

