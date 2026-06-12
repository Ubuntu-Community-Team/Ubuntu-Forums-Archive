---
title: "cannot login"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by youbetcha on 2007-01-05
hello all,

I have download and installed Xubunto 6.10 ,  i have goten to the point to log i nfor the first time, 
I entered in "oem" and my password i created at the install. 

they system begins to load/run , it then logs me out , when i log in again it logs me back out ?

any ideas or is their somthng i;m doing incorrect?

thank you for your help.

pat

---

### Post by taurus on 2007-01-05
Boot into recovery mode from GRUB menu and paste the output of this command here!

```
df -h
```

---

### Post by MkfIbK7a on 2007-01-05
well the problem could be that you have no room left on your HD however this is unlikely considering xubuntu is only 1.4gb...

---

### Post by Sasa_Ivanovic on 2007-01-05
> **youbetcha said:**
> hello all,
they system begins to load/run , it then logs me out , when i log in again it logs me back out ?

does it displays message : "user name or password incorrect!"

---

### Post by youbetcha on 2007-01-05
hello, how do i boot into recovery mode?

it does recognise the user name as corret

---

### Post by MkfIbK7a on 2007-01-05
are you sure you did an oem install?

---

### Post by MkfIbK7a on 2007-01-05
> **youbetcha said:**
> hello, how do i boot into recovery mode?

it does recognise the user name as corret

oh and to boot into recovery mode 

press esc while grub is loading

---

### Post by youbetcha on 2007-01-05
hello , 
i have access to the recovery mode 

i have 3 options 
Ubuntu, kernal 2.6.17-10-generic
Ubuntu, kernal 2.6.17-10-generic (Recovery mode)
Ubuntu, memtest86 +

i have tryed the first one, it starts up the program, i type in "oem" and my password, it starts , i can see the desk top it then gose back to the login screen.


i also have the option to select e  to edit a comand 
or c to get a command line

FYI:

I did install OEM ,  I'm running a p2, 400mhz 10gHD

---

### Post by taurus on 2007-01-05
Use the down arrow key and move to the second option, Ubuntu, kernal 2.6.17-10-generic (Recovery mode).  That's your recovery mode...

---

### Post by youbetcha on 2007-01-05
ok,
i ran the recovery 

it stoped at 

root@lucky: #

lucky is the name of my c drive

---

### Post by taurus on 2007-01-05
That's what we call a prompt.  Now, type in this command and paste the output here...

```
df -h
```

p.s.  Lucky is the name of your machine.

---

### Post by youbetcha on 2007-01-05
filesystem	Size	used	Avail  Use % Mounted on
/dev/hda6	4.5g	1.6g	2.7g 	37%   /
varrun		189m	16m	189m	1%	/var/run
varlock		189m	0	189	0%	/var/lock
procbususb	10m	88m	10m	1% 	/proc/bus/usb
udev		10m	88m	10m	1%	/dev
devshm		189m	392m	4.8G  	1%	/media/hda1

---

### Post by taurus on 2007-01-05
Can you paste the output of this command here?

```
ls -la /home/oem
```

---

### Post by youbetcha on 2007-01-05
hello taurus,
i do not knw what this is but her it is

total 60
drwxr-xr-x 9 oem oem 4096 jan  5 06:29 .
drwxr-xr-x 3  root root 4096 jan  5 04:54 ..
-rw------- 1 oem oem 2826 jan  5 06:29 .iceauthority
-rw-r--r-- 1 oem oem 220 jan  5 04:54 .bash_logout
-rw-r--r-- 1 oem oem 414 jan  5 04:54 .bash_profile
-rw r--r-- 1 oem oem 2227 jan  5 04:54 .bashrc
drwx------ 4 oem oem 4096 jan  5 04:59 .cache
drwx------ 4 oem oem 4096 jan  5 04:58 .config
-rw------- 1 oem oem 24 jan 5 04:58 .dmrc
drwx------ 2 oem oem 4096 jan  5 06:29 .gconf
drwx------ 2 oem oem 4096 jan  5 06:29 .gconfd
drwx------ 3 oem oem 4096 jan  5 04:58 .gnome2
drwxr-xr-x 3 oem oem 4096 jan  5 05:04:58 .local
-rw-r--r-- 1 oem oem 2306 jan  5 06:29 ,xsession-errors
drwx------ 2 oem oem 4096 jan 5 04:58 desktop
lrwxrwxrwx 1 oem oem 26 jan  5 04:54 examples -> /usr/share/example-content

---

### Post by taurus on 2007-01-05
Reboot your machine to normal mode and instead of trying to log in at the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Then, log in with **oem** as your username and your password.  Can you log in from a console at all?

```
shutdown -r now
(to reboot...)
```

---

### Post by youbetcha on 2007-01-05
it says 
i was able to access the console

last login : fri jan 5 06:29:20 07 on :0
followed by warranty info

ending with 

oem lucky:~$

---

### Post by taurus on 2007-01-05
> **youbetcha said:**
> it says 

last login : fri jan 5 06:29:20 07 on :0
followed by warranty info

ending with 

oem lucky:~$

It means you can log in from a console.  Now, what happens when you run this command because you need to run this to create a regular user, the one that you would use from now on instead of oem...

```
sudo oem-config-prepare
```

---

### Post by youbetcha on 2007-01-05
it says password:

i entered one 

it says adding system startup fo /etc/init.d/oem-config...

oem-config will run the next time the system boots

---

### Post by taurus on 2007-01-05
I think it will ask you to create a username and password when you reboot your machine now...

```
sudo shutdown -r now
```

---

### Post by youbetcha on 2007-01-05
restarted

it boots up 
the back ground is a light brown color .

it goes blank 4 or 5 times then it stays on the screen with the brown background,

note the mouse noes not work just an X in the middle of the screen

tryed to enter the console but is does not recognise any key board entry's at this point ,

restarted to make sure the key boad was working , it does work up to the point the brown backgroud appears.

I do not get a login user or password  scren

should I reinstall? 
i double checked  the disk and it check out good.

---

