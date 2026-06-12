---
title: "Error when running synaptic in new installed Ubuntu FF"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by samael_ on 2007-04-19
I have just installed Ubuntu FF and i was gonna install envy. I am not able to do this since i have broken dependencies...

i then do as i am told. i try to run sudo apt-get install -f ... this is the error i get in terminal:

username:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i then try to run the command and i get the error the i have to have superuser acces (directly translated from norwegian to english...

what am i suppose to do??? i cant update my apps and i cant run synaptic. should i just reinstall FF???

---

### Post by tbg58 on 2007-04-19
Use sudo to run the dpkg command.
Alternatively, do 
sudo -s
and enter your password as prompted.
This is the same as changing to root in effect -- you should be able to run your dpkg command then.
Hope this helps!  Good luck!
Rob

---

