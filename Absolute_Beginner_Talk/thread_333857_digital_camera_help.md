---
title: "digital camera help"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-01-08
I have an HP dv8000t laptop with a built in (7 in 1) media card reader. But so far ive had no luck in getting it to work. So instead I tried to plug in my camera (kodak v603) via USB. And the "import Camera" thing comes up asking me if I want to import my pictures, after I click on the "import " button another screen comes up asking where I want to download the pictures etc... But at the bottom of the menu theres an error report:
-------------------------------------------------------------------------------------------------------------------------------------
an error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
-------------------------------------------------------------------------------------------------------------------------------------

Even if I click on "import" nothing happens I just have to exit out. If anyone has any advice on how to get either my media card reader working or the camera import wizard I would really appreciate it!

---

### Post by yabbadabbadont on 2007-01-08
What is the output when you run:

grep "usb_device" /etc/udev/rules.d/*

in a terminal window?

---

### Post by Loki57701 on 2007-01-08
the output is:

/etc/udev/rules.d/20-names.rules:SUBSYSTEM!="usb_device", GOTO="usb_device_end"
/etc/udev/rules.d/20-names.rules:IMPORT{program}="usb_device_name --export %k"
/etc/udev/rules.d/20-names.rules:LABEL="usb_device_end"
/etc/udev/rules.d/40-permissions.rules:SUBSYSTEM=="usb_device",         MODE="0664"
/etc/udev/rules.d/45-hplip.rules:SUBSYSTEM!="usb_device", GOTO="hplip_rules_end"
/etc/udev/rules.d/45-libgphoto2.rules:SUBSYSTEM=="usb_device", GOTO="libgphoto2_rules_real"
/etc/udev/rules.d/45-libnjb.rules:SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libnjb_rules_end"
/etc/udev/rules.d/45-libsane.rules:SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"



Is that bad? lol I have no idea. I know my USB ports work because linux will detect USB devices when I plug them in.

---

### Post by yabbadabbadont on 2007-01-08
> **Loki57701 said:**
> /etc/udev/rules.d/40-permissions.rules:SUBSYSTEM=="usb_device",         MODE="0664"

Edit /etc/udev/rules.d/40-permissions.rules (you will have to run the editor of your choice with sudo) and append, GROUP="plugdev" to the end of that line.  It should look something like:

SUBSYSTEM=="usb_device",         MODE="0664", GROUP="plugdev"

Also, make sure that your user is a member of the "plugdev" group (it should be) by running, "id username" and verifying that plugdev is listed.  If not, you will have to add yourself to that group using "sudo gpasswd -a username plugdev".  If you have to do that, you will need to log out and back in before the change will take effect.

Finally, you will need to restart udev.  The safest way is to just reboot or you could run "sudo udevcontrol reload_rules" and it should be safe too.  If you don't reboot, be sure to unplug your camera and then plug it back in *after* you restart udev.

---

### Post by Loki57701 on 2007-01-08
Thx you soooo much. It worked. After a reboot I was able to download pictures off my camera with no problems! I really appreciate it...

My question is: How did you know how to do that. And why arent the permissions set up upon install? just a bug.



Thx again.....

---

### Post by yabbadabbadont on 2007-01-08
You are welcome.  I'm glad it worked for you.

After you've answered the same question a few dozen times (OK, that's a little exaggerated), you remember the solution off the top of your head.  :D

I don't have a lot of posts in the Ubuntu forums, except for the Word Association thread ;), but I'm in the top 50 posters on the Gentoo forums.  Gentoo suffers from the same issue, so I assume it is something to do with the upstream package maintainers.

---

### Post by angelsneverdie on 2007-01-08
just wanted to say thank you - this also worked for me.

---

### Post by Kujen on 2007-01-08
Another thanks.

---

### Post by Loverman on 2007-01-12
Many thanks it work for me also. I changed to Ubuntu 6 months ago and i love it. Unfortunetly it's small things like this that is holding me back to recomend Linux to my friends.

---

### Post by comet on 2007-01-16
this is a great solution.. thanks again for posting this.. I recently installed Ubuntu on my friend's old HP.. he was getting very tired of windows XP running so slow, and he got an incredible number of viruses.. 

after installing Ubuntu, he called me up the next day saying how please he was.. Except that his digital camera didn't work.. I walked him through these steps over the phone, and it worked like a charm! after witnessing his successful, he squeled with delight.. haha.. I swear I've never seen support as good as the Ubuntu community.. thank you all so much..

---

