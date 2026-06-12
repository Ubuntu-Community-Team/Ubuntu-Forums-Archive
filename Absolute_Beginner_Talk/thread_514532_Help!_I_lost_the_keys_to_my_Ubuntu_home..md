---
title: "Help! I lost the keys to my Ubuntu home."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by A Zen Roshi on 2007-07-31
I installed a File System reader program into window$ 2000 and now i can not log into Ubuntu 7.04 - I don't speak the language so this is frustrating.  I have tried to create a new super user, that does not work because i can not change the password and have no idea how to do so from the terminal command line.  I have a slew of messages at login.  Home direcotory listed does not appear to exist , .dmrc file is being ignored, 644 permissions, GDM could not write, it is not possible to log in, etc.  I hate to ask for help and i have used the forum as a read only source of information.  any suggestions are appreciated [even if it is to tell me to give up :)]

---

### Post by nitro_n2o on 2007-07-31
to change the password from the terminal 
```
sudo passwd <user_name>
```
If you don't know your password log into ubunut recovery mode, by pressing ESC before the grub menu, or choosing the recovery mode if it's available as an option. 
then type passwd 
enter the new passwd 
then passwd <user_name>

---

### Post by A Zen Roshi on 2007-07-31
thank you,

the problem; however, goes further than this.  each time i try to create a new user, change that password or log into any mode - i am compounded by error messages that end up telling me the same thing - "it is not possible to log in.  Please contact your System Administrator".

I am trying to find a way to create an admin user, change that admin user password, reboot, log in as the recently created admin user and move forward with my Ubuntu Experience.  

I will continue searching.  Again, any help - (and i don't get on my knees too often) is greatly appreciated.  :D.

---

### Post by nitro_n2o on 2007-07-31
This might happen if you've changed your shell to something not valid... if have an account now go to Administration->Users and groups and play a little bit with the gui, give yourself permissions and that's it. 
It's highly unrecommended to run your system as root it's really dangerous. 
to add a user from the terminal 
```
sudo adduser <user_name> --gid <use: 0 for root> --shell /bin/bash
```
to add another root with user name hello for example 
```
sudo adduser hello --gid 0 --shell /bin/bash
```
i'd say don't specify the --gid don't even use it and play with permission form the system->administration->users and groups
have fun :)

---

### Post by A Zen Roshi on 2007-07-31
thank you for your interest in my problem.  i have tried to create a new user - i am unable to do so by adduser username admin - this does not work. something about 0666 should be 0440 - sorry i didn't write all of that down but it reported something about /etc/sudousers.  i know i was logged in with admin authority.

I am thinking about reinstalling - probably will be easier.

Sometimes a fresh start and reading ahead before acting upon a situation is best.

Thank you :D

---

