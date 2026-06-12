---
title: "Cannot login after initial install"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2006-12-25
Just finished install of Ubuntu 6.06.1 and everything seemed to go just fine. I installed on my old Compaq 5900Z 256 RAM 40 Gig HD. Did a clean install but when rebooted after CD eject the main logon screen comes up, asking for username and password. During install I was asked for Host name and password and entered them like I was supposed to, and wrote them down so I wouldn't forget. If I enter the Host name into the username field and the correct password it fails saying "incorrect username or password". Any idea what I am doing wrong? Thanks in advance and Merry Christmas.

---

### Post by r4ik on 2006-12-26
reboot into "rescue mode" by selecting it in the bootloader. it will let you login as root with no password, or it may just give you a root promp. either way just type the follwing:

Code:

passwd [username]

obviously replace [username[ with your username

if you don't know your user name, you can look for it by typing

Code:

cat /etc/passwd | grep [some-or-all-of-your-real-name]

Good luck !

Edit: check you're caps please :)

---

### Post by jerrynewt on 2006-12-26
Tried the grep and name and still nothing. Is there a default username assigned during installation, because I was never asked to supply username during initial install. Thanks again

---

### Post by NeoLithium on 2006-12-26
Try this:
Just run sudo oem-config-prepare from a terminal in recovery mode. Next reboot, oem user will be deleted and you will be prompted to create a new login and password.

I suspect that it was installed in OEM by accident, this should delete any OEM username and ask you on next reboot for a username and password.  It will be just as if you set up a fresh install; the only difference is that this will be your new default user.

---

### Post by LOTL on 2006-12-27
NeoLithium,
Im having the same issue here after installing Ubuntu 6.10 alternate on an older P2 266 w/128 MB RAM. I had to install via text mode and it took a good couple hours for the install.
Im fairly new to Linux and had played around with Mandrake and SUSE a few years ago. Id consider myself a newbie though when it comes to using the command line in Linux.
I managed to figure out how to get into recovery mode by hitting the escape key at startup.
I think when you say Terminal you mean a command prompt. I got as far as entering sudo -i to start a root shell, but im having no luck entering in any variation of your command oem-config-prepare. Could you maybe take it down a notch and explain exactly how to enter that command and let me know if im correct at how im arriving at where im entering it?
Thanks
(not to dilute this thread, but am i asking for trouble installing Ubuntu on such an old machine with 10GB HD? itll be used mainly for browsing and email)

---

### Post by LOTL on 2006-12-27
Well i really didnt think i chose OEM install and after looking at some screenshots of the alternate install, i knew i had chosen text mode.
I then found tis thread [http://ubuntuforums.org/showthread.php?t=318758&highlight=forgot+password](http://ubuntuforums.org/showthread.php?t=318758&highlight=forgot+password)
Did what was suggested and changed the password. 
So far so good and it doesn't seem that sluggish all things considered.
Im sure i have plenty more to learn and questions to ask.

Thanks

---

