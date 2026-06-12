---
title: "rc.local question..."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by chlorinekid on 2006-11-26
ive managed to get 915resolution to change my desktop resolution but i have to change it everytime i restart the computer

in another thread someone gave this advice about editing the rc.local file so that the resolution starts everytime i start the computer...
> 
Add the desired 915resolution {sudo 915resolution 5c 1280 800 24} above the "exit 0" line.

Save /etc/rc.local and exit gedit.


ive done this and nothing happens... i notice the script says its not active by default, how do i activate it??

---

### Post by NetworkGuy on 2006-11-26
Remark out the exit 0 line.   

If your commands are beneath that, they aren't being run because of the exit statement.

---

### Post by chlorinekid on 2006-11-26
the command is above that line...

---

### Post by NetworkGuy on 2006-11-26
Try remarking out the exit 0 anyway.

I once added something to the rc.local file and it worked by having that line remarked out.

---

### Post by chlorinekid on 2006-11-26
ok ill try that... just to be sure, does this command look right...

[COLOR="Red"]**sudo 915resolution 49 1280 800 16**[/COLOR]

or should it be wrapped like this..

**[COLOR="Red"]{sudo 915resolution 49 1280 800 16}[/COLOR]**

??

---

### Post by NetworkGuy on 2006-11-26
I'm wondering if you need the sudo, since rc.local runs during system init.

I doubt you need to wrap it but I don't need to run the command on my low resolution laptop 1024x768  :()

---

### Post by chlorinekid on 2006-11-26
i removed the '0 exit' line and it seems to have worked...
fingers crossed it stays that way!!

thanks for help network guy :)

---

### Post by Frost89 on 2007-08-14
Hi Chlorine kid,
I'm having the same problems as you, Can you please post how your rc.local file ended up looking?

---

### Post by st33med on 2007-08-14
OH! That's why nothing ran in my rc.local! Note to self: need to update rc.local. And update my HOWTO...

---

