---
title: "Ubuntu on Compaq Evo N410C - W200 Wireless LAN not working"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-08-31
I decided to move my last post in [this thread]("http://ubuntuforums.org/showthread.php?t=61023") to this forum instead. I am an absolute beginner at Ubuntu, and I also think more people will see it here, which will make it more likely that someone who knows the solution will notice. :) 

Here we go. The guide I'm referring to is from the wiki, I think. [WifiDocs/Device/CompaqW200]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200")

I followed that guide very carefully, I copy-pasted every command into the terminal and so on, and I was doing pretty well, right up until I came to the part with downloading Windows firmware and activating the adapter. After I pasted in

cd firmware
  ./get_ezusb_fw

and hit Enter, I got this back:

chili@chili-laptop:~$   cd firmware
bash: cd: firmware: No such file or directory
chili@chili-laptop:~$   ./get_ezusb_fw
bash: ./get_ezusb_fw: No such file or directory
chili@chili-laptop:~$

I'm not sure what that means, or where to go from here. As a long-time Windows user, my first instinct is to reboot and start over. Would that even work?

/Mimsy

---

### Post by Mimsy on 2006-08-31
I did try again, and this is what hapens when I try to download the firmware.

chili@chili-laptop:~/orinoco/firmware$ ./get_ezusb_fw
./get_ezusb_fw: line 26: curl: command not found
./get_ezusb_fw: line 40: ezusb.drv.pkz: No such file or directory
436+0 records in
436+0 records out
6976 bytes (7.0 kB) copied, 0.003615 seconds, 1.9 MB/s
chili@chili-laptop:~/orinoco/firmware$

If there is any other information I need to post, I probably need to be told where to look for it and how to grab it, but I will do my very best to post it here.

/Mimsy

---

### Post by Mimsy on 2006-08-31
This just occurred to me: Could this have something to do with the evil router I have the laptop connected through? It's a Dynex, if anyone wants to know. :)

/Mimsy

---

### Post by Mimsy on 2006-09-01
Problem solved! :)

---

