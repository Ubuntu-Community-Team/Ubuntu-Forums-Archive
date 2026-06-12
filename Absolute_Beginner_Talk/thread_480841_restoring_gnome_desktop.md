---
title: "restoring gnome desktop"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-06-21
Just a few minutes ago I had to reboot my backup Ubuntu box running edgy. The login screen comes up and I sign in with my user name and password . . . the screen changes to a blank solid background and gnome never appears. How do I get my desktop back using command lines?
tim

---

### Post by Crafty Kisses on 2007-06-21
> **SVWander said:**
> Just a few minutes ago I had to reboot my backup Ubuntu box running edgy. The login screen comes up and I sign in with my user name and password . . . the screen changes to a blank solid background and gnome never appears. How do I get my desktop back using command lines?
tim

You should try reconfiguring your X server, sounds like a video card driver issue, this has happened to me before.

To reconfigure your X server, go into the command line and type:
```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

If you need more information on this matter, please visit the following link:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by SVWander on 2007-06-21
> **Codename said:**
> You should try reconfiguring your X server, sounds like a video card driver issue, this has happened to me before.

To reconfigure your X server, go into the command line and type:
```
sudo dpkg-reconfigure xserver-xorg
```

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

If you need more information on this matter, please visit the following link:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Thanks for the info. I used the command and it came back /usr/sbin/dpkg-reconfigure xserver-org is broken or not fully installed. Strange that it was working before I rebooted. I will research some more. I guess I need to reinstall something.

Tim

---

### Post by Crafty Kisses on 2007-06-22
> **SVWander said:**
> Thanks for the info. I used the command and it came back /usr/sbin/dpkg-reconfigure xserver-org is broken or not fully installed. Strange that it was working before I rebooted. I will research some more. I guess I need to reinstall something.

Tim

I think you may find this link very useful:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by SVWander on 2007-06-22
> **Codename said:**
> I think you may find this link very useful:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Well, I followed the instruction and read the article related to my issue but nothing works. I think the problem goes deeper than just a messed up ubuntu-desktop. I am getting an error message that was masked until I hit alt ctrl F4. It read [127.190271] codec write timeout status = 0xffffffff
To me that sounds like a memory problem but when I run the memory check it seems to be okay. But I didn't know how long to run the memory test. It seemed it would go on forever. Anyway, thanks for the help but it might be in the motherboard.

Tim

---

### Post by Crafty Kisses on 2007-06-22
> **SVWander said:**
> Well, I followed the instruction and read the article related to my issue but nothing works. I think the problem goes deeper than just a messed up ubuntu-desktop. I am getting an error message that was masked until I hit alt ctrl F4. It read [127.190271] codec write timeout status = 0xffffffff
To me that sounds like a memory problem but when I run the memory check it seems to be okay. But I didn't know how long to run the memory test. It seemed it would go on forever. Anyway, thanks for the help but it might be in the motherboard.

Tim

How much RAM do you have?

---

