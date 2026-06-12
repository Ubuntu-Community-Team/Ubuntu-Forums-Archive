---
title: "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-09-18
i am trying to change my nvidia settings but when i change the settings and click Save to X configuration file, i got an error: Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.
how do i fix this?

---

### Post by jimbob on 2007-09-18
sudo rm -rf  /etc/X11/xorg.conf.backup
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by amneziac on 2007-09-18
that didnt do anything

---

### Post by amneziac on 2007-09-18
it now says cannot create new xorg.conf.backup

---

### Post by jimbob on 2007-09-18
Did you do it from a terminal (command line)?

What message(s) did you get?  Post the output of the following:

cd /etc/X11
ls -al xor*
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by amneziac on 2007-09-18
manar@manar-desktop:~$ sudo rm -rf /etc/X11/xorg.conf.backup
manar@manar-desktop:~$

---

### Post by amneziac on 2007-09-18
manar@manar-desktop:~$ cd /etc/X11
manar@manar-desktop:/etc/X11$ sudo rm -rf /etc/X11/xorg.conf.backup
manar@manar-desktop:/etc/X11$

---

### Post by x1a4 on 2007-09-18
Before saving, nVidia Settings backs-up xorg.conf.  Because you didn't run it with root priviledges it couldn't do it.  When you ran sudo rm ... you got no error because it was successful and the file was removed.  

For nVidia Settings to be able to write to xorg.conf run it with root priviledges like so: 

gksudo nvidia-settings

You can also run 

sudo nvidia-xconfig

from a terminal to write current settings to xorg.conf

---

### Post by Beakerz on 2007-09-24
Just wanted to say thanks to x1a4 - was having same issue. <--nub to linux, but trying hard :D

---

### Post by pdlethbridge on 2007-11-15
fixed my problem as well, thanks

---

### Post by PC_load_letter on 2008-03-04
I'm running into the same problem. When I log into the "root" session I could easily change the resolution to 1152 x 864 and it sticks.
The exact opposite happens in my "user" session. First I got the ***"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup"*** error, but then I followed what x1a4 suggested. Now, the saving process goes without any errors but once I restart the X-server and login back as "user" the changes revert back to 1024 x 768 res. 

I'm running Ubuntu 64bit on an AMD X2 machine with an nvidia chipset, the on-board nvidia GPU is: Quadro NVS 2105 / Nvidia GeForce 6150LE as it appears in the nvidia-settings.

Any help is greatly apprciated.

Thanks.

---

### Post by mcdan on 2008-03-04
instead of using sudo, you may have to use gksudo.  gksudo is similar to sudo, but is used to change graphical things.  it'll prompt you for a password, and it's the same as your sudo password.

hope this helps

---

### Post by PC_load_letter on 2008-03-04
Just tried the gksudo to no avail. After typing the password, nvidia-settings started, then I changed the resolution, saved and quit. Upon restarting X-server I'm back again to 1024 x 768.

What drives me nuts is that if I log-in as root in the X-session, everything is fine and the higher resolution is now the default. 

I did some digging and some people had this problem due to that the monitor refresh rates were not correct in the xorg.conf file, but isn't it the same file that is used when I log in as root? 

:confused::confused::confused:

---

### Post by PC_load_letter on 2008-03-05
....bump. 

Can someone at least explain to me why I can not change to a higher resolution in my "user" account, while I already did it for my "root" accout???

Thanks in advance.

---

