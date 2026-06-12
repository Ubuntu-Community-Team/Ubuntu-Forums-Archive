---
title: "Ndiswrapper problems."
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by IvanGrozny on 2005-10-11
Alright I got Ndiswrapper working, i have my wireless network card working, the internet works fine and everything. The only thing is everytime I restart my computer I have to re-enter all those commands to get my wireless card working again. How do I make a script or whatever you would do in this situation so it just loads the wireless card at startup?

---

### Post by Eldon on 2005-10-11
The cheap and dirty place to stick em is in your bashrc file
sudo gedit ~/.bashrc
But we're talking dumpster dirty.. hopefully someone will come up with something more elegant for you.

---

### Post by loupy on 2005-10-11
after you did ndiswrapper -i xxxxx.inf did you do ndiswrapper -m ?

that should save it - I am a newbie, but when I installed my card I did the following three commands and have had no issues when I reboot:

sudo ndiswrapper -i DRIVER.inf (whatever driver you used)
sudo ndiswrapper -m
sudo modprobe ndiswrapper

Let me know if this works.

---

### Post by IvanGrozny on 2005-10-11
I did that but it didn't work, after i restarted the computer I still had to go:

modprobe ndiswrapper
dhclient wlan0

While this isn't a huge inconvience I should be able to put it somewheres on boot.

and in that bashrc file where do i put the commands were I to do that?

---

### Post by skirkpatrick on 2005-10-11
what you want to do is add "ndiswrapper" to the bottom of the file /etc/modules.  That will cause it to do the "modprobe" on every boot.  You can also add "map wlan0" after "map eth0" (make sure you space or tab over) to /etc/network/interfaces.  You'll also want to add "auto wlan0" to /etc/network/interfaces, just like the "auto eth0" that is already there.

---

