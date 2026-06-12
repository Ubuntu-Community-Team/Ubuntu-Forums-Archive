---
title: "keyboard video mouse"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by mordeith on 2008-01-11
i am using a kvm....whene i switch from one computer i have a problem with the mouse cursor jumping around the screen for about 30 seconds or more...very aggrivating....any clues how to prevent this

---

### Post by nikoPSK on 2008-01-11
I don't really understand... do you mind rephrasing please?

Best, 
nikoPSK

---

### Post by Zill on 2008-01-12
mordeith:  I found a solution on [this]("https://slion.net/view/Dev/LinuxUbuntu#How_to_make_your_mouse_work_with")  website:

> **How to make your mouse work with KVM**

After a KVM switch and back the mouse can behave erratically or buttons and wheel might not be working anymore. Here is how to fix that:

    * Edit and add the following to /etc/modules : 

#Load psmouse module
psmouse

    * Edit and add the following to /etc/modprobe.d/options 

#Make my mouse work with KVM
options psmouse proto=imps

Reboot

It worked for me :-)

---

### Post by nikoPSK on 2008-01-12
glad to know. :popcorn:

---

### Post by gcornett on 2008-01-13
I also have this problem with a Belkin SOHO KVM.  Very annoying. I tried Zill's suggestion on Gutsy.  It killed my mouse.  Any other suggestions would be more than welcome!  :)

---

### Post by Zill on 2008-01-13
> **gcornett said:**
> I also have this problem with a Belkin SOHO KVM.  Very annoying. I tried Zill's suggestion on Gutsy.  It killed my mouse.  Any other suggestions would be more than welcome!  :)
FWIW, this fix worked for me using a Belkin OmniCube F1D092 KVM and a Genius 3-button optical wheelmouse (PS2).  One PC running Dapper and one Gutsy.  Before the fix the mouse was all over the place after switching.  After the fix both PC's work fine with a rock-steady mouse.

---

### Post by mordeith on 2008-01-13
hey thanks that  worked:KS

---

### Post by nikoPSK on 2008-01-13
Please mark this thread as "SOLVED". :)

Regards,
nikoPSK

---

### Post by gcornett on 2008-01-14
Since Zill was sucessful with this fix, I've done some more digging.  Whereis doesn't find psmouse in my system.  I went ahead and added it to /etc/modules and rebooted.  Still can't find it with whereis.  I've got to be missing something here.

---

### Post by Zill on 2008-01-15
gcornett:  Whereis doesn't find psmouse in my systems either!  Man pages reveal that "whereis" locates binary files for a command.  However, psmouse is a kernel module so it will not show up with this command.  The following code should confirm that psmouse is loaded into your kernel:
```
lsmod |grep psmouse
```
Assuming it now is, have you added the line "options psmouse proto=imps" to /etc/modprobe.d/options as suggested?
It is also important to reboot each PC with the KVM switched to that PC until the boot process has completed.

---

### Post by gcornett on 2008-01-26
Zill:  Thank you.  I will use lsmod | grep to search for psmouse when I get back home. Unfortunatly, I'm out of town for a few weeks and away from that computer.

I'm pretty sure I did add options psmouse proto=imps to /etc/modprobe.d/options but I will try it again and reconfirm.    

I appreciate the help!

---

