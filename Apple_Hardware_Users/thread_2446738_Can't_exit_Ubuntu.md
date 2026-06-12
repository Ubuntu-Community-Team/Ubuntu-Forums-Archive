---
title: "Can't exit Ubuntu"
date: 2020-07-06
forum: Apple Hardware Users
---

### Post by isza on 2020-07-06
Hi,
I am very new to Ubuntu, using the Ubuntu Studio flavour on my Mac Mini as an optional OS. I succeeded in installing it on a USB stick and it runs on my Mac all right. However, after installing additional software form the Ubuntu download site I now can not exit Ubuntu when clicking on the shut-off button. It starts anew. The only way now to exit is by force quitting pressing the rear button on my Mini.
What is happening here? How can I reestablish the normal way of shutting down?
Help appreciated!

Andy

---

### Post by gsahli on 2020-07-06
Just for troubleshooting, have you tried using the terminal command - sudo shutdown -h now

---

### Post by isza on 2020-07-09
Hi gsahli, thanks for helping!
Just to make sure before I screw up something. The command is:
sudo shutdown -h now
Correct?
Is this a one off solution or is it supposed to restore the shut-off button's function in Ubuntu for good?

---

### Post by gsahli on 2020-07-11
That's the correct command. This is just to see if the computer CAN be shut down from software.

---

### Post by isza on 2020-07-13
Yes, it can. I've entered the command and it works in a strange way and only once per session. After entering the command and clicking on the shut-off button, Ubuntu starts again and then goes out. Next session does not work, have to enter command again.
This is not a satisfactory solution for good, but works as an emergency.

---

### Post by gsahli on 2020-07-14
That's what it is for - a one-time shutdown. Modifying it to sudo shutdown -r now forces a reboot. When you use this command, there is no button to click.
I wonder what you meant?
Looks like you need to learn some linux terminal commands - so you can get the full utility out of linux.

---

