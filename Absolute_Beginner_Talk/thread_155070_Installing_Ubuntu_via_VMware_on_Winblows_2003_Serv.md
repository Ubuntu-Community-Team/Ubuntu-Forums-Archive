---
title: "Installing Ubuntu via VMware on Winblows 2003 Server issues"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Magic Hat on 2006-04-04
Greetings all!!

when it comes to linux, im a complete newb. I decided to start my linux using quest by installing Ubuntu 5.10 via VMware 5.5.1 on Winblows 2003 server. Installation went fine untill the very end. Once my pc rebooted and i logged in,
under where it says: Ubuntu comes with absoultely no warranty, to the extent permitted by applicable law, appears:
tester(myusername)@ubuntu:~$

and nothing else happens....
i can type in the screen, but i am complely clueless on what to enter.

any help?

thanks in advance!!!

respect!

---

### Post by Magic Hat on 2006-04-04
let me revise my issue. when i open up ubuntu, after i log in, i get no GUI. just command lines.  

can anyone help?


thnaks again

---

### Post by Randomskk on 2006-04-04
log in, and try typing "gdm" (I assume you're using GNOME and not KDE) to start the graphical thingy.
Also try "startx", one of them at least should either load graphics or give you a useful error message.

---

### Post by Magic Hat on 2006-04-04
lthanks you the reply!!
massive respect!!

let me tell ya exactly what i did.

opened up vmware
created a new workstation
installed ubuntu

the commands you told me to type in all came back the same:

command not found

am i missing something??

gnome and kde???

please readvise

thanks again!!

---

### Post by Randomskk on 2006-04-04
Did you do a ubuntu-server install?
Once logged in, try the following (will need a fairly big download):
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Magic Hat on 2006-04-04
:D 

after all the tutorials i read today...

the one little line of code that you told me to input was by far the best piece of info i have received all day!!!

now its unpacking like crazy, looks like its going to take a while (over a gig of stuff to unpack)

massive respect!!!

ill post if i have any further questions or issues.

just praying for a gui!!!

thanks again

---

### Post by Magic Hat on 2006-04-04
ps,

no, this isnt a ubuntu server install

---

### Post by Magic Hat on 2006-04-04
YEAH!!!

I GOT A GUI!!!

THANKS ALOT!!!!

respect

---

### Post by Randomskk on 2006-04-04
No problem, glad to hear it worked for you :D

---

### Post by Magic Hat on 2006-04-04
:D

coming to you live from my 2003 Server/Ubuntu Machine!!!

thanks again

---

