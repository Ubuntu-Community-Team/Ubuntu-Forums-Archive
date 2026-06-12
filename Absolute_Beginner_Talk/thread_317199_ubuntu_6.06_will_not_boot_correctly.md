---
title: "ubuntu 6.06 will not boot correctly"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by niallcd on 2006-12-12
Hello.


I am useing an Athlon 64 with a Radeon 9800 pro.

I first created an image disk and tried to install Ubuntu 6.06. This process ended when I got the Ubuntu load screen and then after a minute or two I got a  blank screen and nothing happened. I then decided to enter the Kernal and entered chroot /root nano /etc/X11/xorg.conf

This worked and I installed Ubuntu 6.06 however when I tried to reboot I found that Ubuntu would load then send me to the kernal where I then had to type chroot /root nano /etc/X11/xorg.conf over again and then exit the kernal
then it would load. 

This is painful and I would like it to work so if anyone has any ideas I would love the support.

Thank you.

---

### Post by Ecthelion on 2006-12-12
Did you try reconfiguring the /etc/X11/xorg.conf using ```
sudo dpkg-reconfigure xserver-xorg
```?
Answer the questions and if you don't know leave the default choice

To see if this works you don't have to restart your whole pc. Just doing Ctrl-Alt-Backspace (make sure you don't have anything important open) should restart your xserver and then you should see if the problem is fixed.

---

