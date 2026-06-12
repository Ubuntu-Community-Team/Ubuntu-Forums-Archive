---
title: "putting command in boot, use rc.local?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-12-05
I need to regulate the cpu freq with* sudo cpufreq-set -u 2400000. *

reading around people say put it in rc.local or init.d but that rc.local may not be the best way on a debian based distro. 

if I put it in init.d then I need to *sudo update-rc.d script_name defaults* ?

how do I put it in there anyway? make a new little text file with just that command in it? what to name it?

with xubuntu-desktop settings> sessions & startup settings will provide no help on this. 

if there's really no better way than with etc/rc.local do I just paste the command in before the "exit 0" without a # before it? or am I mistaken,  should I be concerned with /etc/init.d/rc.local ?

thank you

---

### Post by David_T on 2006-12-05
If you want your command to run at boot time, just place it in /etc/rc.local without the sudo in front of it, above ``exit 0''.  You can test it by running the command:

sudo /etc/init.d/rc.local start.

---

### Post by leetrefz on 2006-12-05
ok that worked well, thanks.

---

### Post by tbeld on 2007-02-27
It didn't work for me at boot:( 
I can run the script fine in a terminal. Any suggestions?

---

