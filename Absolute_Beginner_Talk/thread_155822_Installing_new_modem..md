---
title: "Installing new modem."
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by kwjaxon on 2006-04-05
Have tried to install Intel 536EP hardware modem for the last week without success.  Have new serial modem coming, U S Robotics.  With all the installations and tries that I did with the other modem, should I reboot or just remove all the files that I can find.  It would seem best to reinstall as I have done nothing to the OS except try to get online.  Can you help???  TIA

---

### Post by StefanoCole on 2006-04-06
Well if it is a serial modem no additional drivers are required. Open a terminal and type:

sudo pppconfig

Enter the information as needed. Use the name provider for your default connection. COM1 is /dev/ttyS0, COM2 is /dev/ttyS1, and so forth.
Add your user to the dip group using the advanced options.
Save and exit.
sudo pon
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.
sudo poff hangs up.
You need to log out and back in for your user/group settings to be updated. You can then pon and poff without the sudo. 

Stefano

---

### Post by dvarsam on 2006-04-06
he...he...

I always prefer the US Robotics brand... there is always something magic about them...

You need NO drivers to install any of their kind to the Windows Platform...

...and I BET they can work as easily on the LINUX platform...

---

### Post by kwjaxon on 2006-04-06
Thanks.  Sorry to be slow to respond.  I like that last answer.

---

