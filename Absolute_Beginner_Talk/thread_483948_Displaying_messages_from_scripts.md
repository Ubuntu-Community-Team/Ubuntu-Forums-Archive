---
title: "Displaying messages from scripts"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by percivalbragg on 2007-06-25
I am a newbie to linux and I am trying to popup a message from a script that is run automatically when a pcmcia card is plugged into the computer, this I got working through /etc/udev. I just don't seem to get a message to appear.

When I run the script from a terminal I can get the message to appear but not when it is triggered automatically by the hot plug.

Any help would be greatly appreciated.

---

### Post by Skrynesaver on 2007-06-25
Scripts write to their own designated STDOUT (STandarD OUT) if the script is called by udev which writes to either /var/log/messages or /var/log/dmesg have a look in these files with grep to see where your message is sent

---

### Post by percivalbragg on 2007-06-25
I am not worried about where udev sends my message, I wnt to display the message on the screen.

---

### Post by Skrynesaver on 2007-06-25
udevd (The monitoring process the runs in the background) is run as root in the background.  It cannot know that there is a user logged in, you could run a process/script as the user as part of your login which monitors the logfiles for output from udev and diplays that output in an Xmessage window.

---

