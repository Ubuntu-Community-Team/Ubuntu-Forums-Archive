---
title: "Testing a script"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Titus A Duxass on 2006-01-27
How do I test a script?

I have written a script to apt-get install several packages, then change permissions for some files, then apt-get remove some files and finally reboot.

Is there something that can check to see if everything in the script is hunky-dory?

Ta

---

### Post by ]Nbx*cmD[ on 2006-01-27
I'm afraid you'll have to run it to test if it works.
Just chmod 777 yourscript.sh (for example) and then ./yourscript.sh

---

### Post by agapito on 2006-01-27
What I usually do is put an *echo* behind all commands ( if the script isn't too long) and see if it's doing everything the way I wanted.

---

### Post by drewbie on 2006-01-27
you could try adding -s as an option to apt-get to only simulate

you might also want to edit the first line of the script to give the x option

#!/bin/bash -x
this will print out in the terminal what the script is doing

---

### Post by agapito on 2006-01-27
[QUOTE=Titus A Duxass]I have written a script to apt-get install several packages, then change permissions for some files, then apt-get remove some files and finally reboot.
[/QUOTE]

By the way, if your script is doing all of that, consider (if you haven't allready...) adding *wait*  after some commands (in the next line). This way the script waits for the specified process to end before running another command.

---

### Post by Titus A Duxass on 2006-01-27
How does this look?

#! /bin/sh

apt-get update 
apt-get upgrade -y 

# Install these packages for the basic GD installation 

apt-get install mplayer-386 -y 
wait
apt-get install lame -y 
wait
apt-get install cdtool -y 
wait
apt-get install netpbm -y 
wait
apt-get install mp3info -y 
wait
apt-get install aumix -y 
wait
apt-get install mysql-server -y 
wait
apt-get install libcddb-get-perl -y 
wait
apt-get install libid3-3.8.3-dev -y 
wait
apt-get install libdbd-mysql-perl -y 
wait
apt-get install mpg123 -y 
wait
apt-get install make -y 
wait
apt-get install cdparanoia -y 
wait
apt-get install pilot-link -y 
wait
#Delete music's login password if you were required to enter one during the install: 

passwd -d music 

#Set read/write permissions on some of the devices to allow anyone to use them: 

chmod 777 /dev/dsp 
chmod 777 /dev/ttyS0 
chmod 777 /dev/rtc 
chmod 777 /dev/mixer 
chmod 777 /dev/null
chmod 777 /dev/cdrom

---

### Post by agapito on 2006-01-27
It looks good, but you could make it simpler (and maybe faster...) if you put all the packages you want to install in a couple of lines:

apt-get **-y** install  deb1 deb2 deb3 and-so-on
wait
apt-get **-y** install deb4 deb5
wait

Edit: I made a mistake. The option comes before the install commad. Sorry

What I don't get is the *passwd -d music* Quoting the man page:"You can  also  use  the  -d  option  to delete a user&#8217;s password (make it empty).  Use caution with this option since it can make an account not require a password at  all  to  login, leaving your system open to intruders." Is that what you really want to do?

---

### Post by Titus A Duxass on 2006-01-27
Thanks for the tips everybody.

It is my intention to delete music passwd, the system is not connected to anything and runs without keyboard or mouse.

---

### Post by agapito on 2006-01-27
[QUOTE=Titus A Duxass]It is my intention to delete music passwd, the system is not connected to anything and runs without keyboard or mouse.[/QUOTE]

I just wanted to warn you 'couse it could be a dangerous move, but not in your case. ;)

---

