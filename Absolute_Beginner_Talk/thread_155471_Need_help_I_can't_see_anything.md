---
title: "Need help I can't see anything"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by bakie on 2006-04-05
Hi,
i'm new to linux ubuntu for 3 days now and i like it more then windows :D 
i installed everything i needed like xmms, nvidia drivers, etc...
but yesterday i got a problem when i start up my ubuntu i cant see the normal interface the only thing i see is the command line (compare it whit dos in windows).
Now i've tried many things (stuff like: sudo /etc/init.d/gdm start, reconfigure my xserver, tried to find an answere on google and even asked my brother for help) but nothing worked.
so if any1 has any idea on how i can fix this problem please help me.

---

### Post by catlett on 2006-04-05
Open the terminal and type```
 sudo dpkg-reconfigure xserver-xorg
``` this will take you through the setup of x. Somehow you lost it. This is probably the easiest way to get it back (at least that I know of). For right now type ```
startx
``` and see if the window manager starts.

---

### Post by millol on 2006-04-05
Hello,
I got the same problem. When I installed plugins and drapper packages I couldn't start xserver. So I did from the command line:
sudo apt-get dist-upgrade
and everything worked. Give it a try.

---

### Post by meborc on 2006-04-05
[QUOTE=millol]Hello,
I got the same problem. When I installed plugins and drapper packages I couldn't start xserver. So I did from the command line:
sudo apt-get dist-upgrade
and everything worked. Give it a try.[/QUOTE]
are you suggesting to upgrade to dapper? or? since the starter of the thread probably has breezy installed... 

anyway a simple dist-upgrade WILL NOT upgrade breezy to dapper... you have to modify your sources.list to apply to dapper...

---

### Post by millol on 2006-04-05
[QUOTE=meborc]are you suggesting to upgrade to dapper? or? since the starter of the thread probably has breezy installed... 

anyway a simple dist-upgrade WILL NOT upgrade breezy to dapper... you have to modify your sources.list to apply to dapper...[/QUOTE]

In my case, yes, I modified sources.list.
But I think that dist-upgrade may resolve dependancies problem even if you don't wanna upgrade cause his problem is probably about dependancies.

---

### Post by bakie on 2006-04-05
first thx for the quick reply's i've tried everything yuo guys said and with the startx command i can get back in the graphical interface so i can see everyhting again.
but now when i want to shutdown or reboot my pc i first need to log out and then type in the command line reboot if i want to reboot.
now i started thinking since my loggin screen doesn't show up i wanted to see if this was still ok but when i go to System --> Administration, there's no Login Screen tab. is there a way to acces the login Screen tab on an other way so i can check if everyhting is still ok?

---

### Post by bakie on 2006-04-05
I fixed the problem myself so wont be needing anymore help.
thx all for helping me

---

### Post by erniewinner on 2006-04-05
"sudo dpkg-reconfigure xserver-xorg"
i'm not sure if this is a silly question, will that be the same for the ppc version also? i'll have to set my mac up again! :rolleyes:

---

