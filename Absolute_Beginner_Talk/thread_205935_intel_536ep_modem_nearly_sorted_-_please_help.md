---
title: "intel 536ep modem nearly sorted - please help"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by cubastreet on 2006-06-29
Hi there,
This is the first time I've installed linux in a few years, trying to rid my computer of windows...
I've managed to get my modem to work with a combination of matchless' guide here: [http://www.ubuntuforums.org/showthread.php?t=171284&highlight=536ep](http://www.ubuntuforums.org/showthread.php?t=171284&highlight=536ep) and also the readme that comes with the driver.
matchless' guide does the most of it, but I still need to open a terminal and enter these two commands to get it to work:
sudo mknod /dev/536ep c 240 1
sudo ln -s /dev/536ep /dev/modem
can someone please tell me how to load these commands when the system boots?
Cheers,
Jeremy.

---

### Post by Apple 101 on 2006-06-30
1. You'll need to write the script first.  I'm no expert when it comes to scripting, so someone will need to help you with that.
2. Put the script into the */etc/init.d/* directory.
3. In a terminal: *update-rc.d <filename> defaults*
4. Make the script executable.  In a terminal: *chmod +x <filename>* (you'll need to be in the directory first, though).

---

