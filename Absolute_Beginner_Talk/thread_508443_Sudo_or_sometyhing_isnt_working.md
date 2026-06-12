---
title: "Sudo or sometyhing isnt working"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-24
my friend installed Ubuntu last night and everything went well.
all seemed good.

however tday when i spoke to him, i gtold him to sudo apt-get update
he enter passwrod but it done nothinh?

i then told him to do graphically via, ststem>administartion>update manager
still nothing happened.

i told him to og hcekc the disk's integirty.

i think that may be the problem, but if the disk is ok, any ideas on why itas not working?

---

### Post by Skrynesaver on 2007-07-24
Check /etc/passwd, did he create a user during the setup that he's forgotten about?

---

### Post by sad_iq on 2007-07-24
You told him to use the disk to do the updates??? He has to be online to update his box...the cd...after the install is not needed, unless he has no internet and needs to install some package.
 >  i gtold him to sudo apt-get update
 he enter passwrod but it done nothinh? 

 That is not an acceptable  answer...either it didn't find an update (witch isn't nothing)...or it printed in a terminal something like this:```
sadiq@omerta:~$ sudo apt-get update  
Password:
sadiq@omerta:~$
``` witch is actually something serious(and is actually a "nothing happened" type response) Make sure you get all the details from him whenever possible...and that's why these forums are filled with things like "paste the output from this command here"...what doesn't look like an error to some may be to others!!!

---

### Post by ReaderRat on 2007-07-24
When you use the Terminal, if you enter a Password, it will not show on the screen. This is for security and privacy reasons.

---

