---
title: "help abt some commands"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by usien on 2006-12-26
i am new to linux nd ubuntu.i hav to type these lines everytime i want 2 connect 2 the internet in the terminal:

sudo ln -s /dev/ttyUSB0 /dev/modem
sudo dmesg -c

without these lines my modem is not detected(its a usb modem).i wanted 2 know if there is some procedure i can perform just once so i dnt hav 2 do it over nd over again.also how can i delete or create directories/files from the gui browser rather than typing sudo nd the commands everytime in the terminal.and lastly can i configure gnome ppp dialer with a conf file.plz help.

---

### Post by davmac on 2006-12-28
I don't think it's the "proper" way to do it but the first problem can be dealt with by adding the two commands to the file /etc/init.d/bootmisc.sh (in terminal type "sudo gedit /etc/init.d/bootmisc.sh"). If I have misc bootup commands I want to run I put them in here just after the section "# save udev log in /var/log/udev".

For the second problem, if in a terminal you type "sudo nautilis ." (with the dot) you can start a file browser that has root permissions. BE CAREFUL THOUGH!

Hope this helps,

Dave Mac

---

