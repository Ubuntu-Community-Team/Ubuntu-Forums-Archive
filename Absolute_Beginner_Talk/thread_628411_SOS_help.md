---
title: "SOS help"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Dashuka on 2007-12-01
Hi, guys!

I am totally lost. I got my ubuntu yesterady and already did something very wrong. Please, I need your help. 
The problem is after I log in the message 
''Your home directory is listed as: '/home/Dasha' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.''
appears.
If i push no - i need to login again, if i push yes, it still stops session after 10 seconds.
I have no idea what is wrong and how to fix it. Please, help!!!

BR

P.S. I have only one user on that computer.

---

### Post by cmnorton on 2007-12-01
If you session stops after ten seconds using /root as your home directory, then boot with a live or recovery CD, mount the disk that contains /home, and go create your home directory. 

Make sure /home/your-name is chown -R your-name:your-name and the protections allow at least owner to r+w+x. chmod -R 700 /home/your-name.

If you installed by Ubuntu live CD, you should be able to do this. My personal preference is to keep a Knoppix CD around, but you've got to get beyond this problem, first.

---

