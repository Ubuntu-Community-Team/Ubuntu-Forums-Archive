---
title: "Changed video card and x doesn't start"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by chapmc on 2006-12-20
I changed the video card in the pc where ubuntu 6.06 is installed.  When I rebooted the x server configuration is now incorrect.  I searched the threads and I tried using "dpkg-reconfigure xserver-xorg" and answered the questions best I could, mostly took the defaults.  The video card is nvidia vanta.  I looked at the errors from x and it looked like the problem is that it couldn't find /dev/fd1, etc.  They say no such file or directory.  Error says see the "above".  I can reinstall if I have to because I don't have anything important on the machine but I would like to fix it if I can.

If you have some suggestions for me please let me know.  I don't even know what /dev/fd? is.
Thanks..

---

### Post by meng on 2006-12-20
Which video driver did you choose? Try 'nv' or 'vesa' if you haven't done so already. Steer clear of 'nvidia', at least initially, the first priority to get X going somehow, the second priority is to fine-tune.

---

### Post by sonny on 2006-12-20
Did you have the nvidia drivers before you changed your video card? where you using an ATI or a integrated intel?

When you do "sudo dpnkg-reconfigure xserver-xorg" do you choose the nv or the nvidia one?

And finally in order for someone more experienced than to help you I think you should post the error log.

---

### Post by chapmc on 2006-12-20
I did choose nv for the chipset.  The video card I took out was ATI.  I can't really post the error log because I don't have a working internet connection there and I don't know how to get the log to another computer to send it.  (Not very good on the linux terminal).

---

### Post by meng on 2006-12-20
vesa?

---

### Post by chapmc on 2006-12-20
OK I tried vesa and it is working.  Now my resolution is 640x480 and that is the only option I have.  Is there a way to change this or I should try again with nv?

I am going out of town tomorrow.  Will have to finish this come other day.  Thanks for your assistance so far.

Merry Christmas, all!!

---

### Post by chapmc on 2006-12-22
FYI I have it working now!!  used "dpkg-reconfigure -phigh xserver-xorg".  The only choice I had to make was to check the resolutions to allow.  Reboot and that's it.

This is a great forum.  Thanks for all the willing help.

MERRY CHRISTMAS.....

---

