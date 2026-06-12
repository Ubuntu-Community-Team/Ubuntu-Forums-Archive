---
title: "please help!! laptop screen broke need to comfigure xorg"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-05-31
hi

i have an dell inspiron 5150 and i think my screen has just died.

if i take the hard disk out and attach it to another pc can i configure the xorg.conf file so it displays to a monitor via the monitor out port on the laptop?

if so how??

thanks!

simon

---

### Post by nalmeth on 2006-05-31
That seem's like a little bit of an impractical way to go about it.
First, laptop's are built like new car's, only to be serviced by the manufacturer or by a servicing company. That's not to say you can't do it, perhap's you already have and know what you're talking about.
Theoretically you could mount the system on another linux distro, chroot into it, and make the proper adjustment's. But if you are sure it's just X that is borked, then you should still be able to log in with "recovery mode". Right when you see GRUB loading, hit ESC as prompted to enter the GRUB menu, and select recovery mode. 

If you can't see anything when the laptop power's up, I'm afraid you probably have a physically broken screen. 

What caused the problem's you are having? Did you drop the laptop? Spill something on it? Can you see anything when you boot up? Or is it really just the Xserver that's broken?

---

### Post by cowley on 2006-05-31
hi thanks for the prompt reply

i shut the laptop down then when i went to reboot the screen is black - i have tried to see if i can see a faded image on the screen to see if its a back light problem but i cant see anything!! its just permantly black i dont even see the dell splash screen
the reason i was asking about the xorg was i have an external flat screen monitor which could be connected to the laptop if i could get that to work as the default monitor i wouldnt have to worry too much about getting the screen repaired

thanks

simon

---

### Post by Dr. Nick on 2006-05-31
If you use the external monitor it might work fine, just appear distorted. If it doesnt work then boot into recovery mode and run 

sudo  dpkg-reconfigure xserver-xorg

which will walk you through the process again.

---

