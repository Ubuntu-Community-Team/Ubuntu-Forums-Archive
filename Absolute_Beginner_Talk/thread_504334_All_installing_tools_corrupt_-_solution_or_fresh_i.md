---
title: "All installing tools corrupt - solution or fresh intallation of Ubuntu?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Che_GueVaRRista on 2007-07-19
Hello to everyone on the forum!!!

Ubuntu and Linux newbie here.


Problem>>>I have had a couple of unsuccessful installations on my Ubuntu, involving Yahoo and Skype, several times the installing tools had to be shut down manually, after which I was getting the error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report


Let me just say that before that I had a series of installations where one was moodle, which has been left unconfigures as I didn't know how to configure it (not that I wanted to install it at all). 


I solved the error message problem by following this command:


Open a terminal (Menu->Accessories->Terminal).
Type the following command and press the Enter key:

dpkg --configure -a && sudo apt-get -f install

(found on [https://answers.launchpad.net/ubuntu/+source/yelp/+question/6112](https://answers.launchpad.net/ubuntu/+source/yelp/+question/6112))



it required superuser privilege, so I have followed the following tip from the above page,

try sudo dpkg --configure -a && sudo apt-get -f install


--------------------------------------------

That seemed to have finished to unfinished installation, and it looked like the problem is resolved. 


But it looks now that the problem is back on, as neither the add/remove nor the synaptic package manager are starting any of the installation/uninstallation processes (instead the openining of process lingers forever)


So my dillema is, and I hope you can help me, is there a way to get around this problem and have it back to normal, so the software can be added and removed, or I will have to install the OS from scratch, and go through all the configuration again?




Very Grateful for your replies,

Che

---

### Post by meborc on 2007-07-19
what is the exact error you get when running```
sudo apt-get update
sudo apt-get -f install
```?

---

### Post by ubanchaos on 2007-07-19
which linux are u using be specific

---

### Post by Che_GueVaRRista on 2007-07-20
> **ubanchaos said:**
> which linux are u using be specific

I am using Ubuntu 7.0.4 Feisty Fawn

---

### Post by Che_GueVaRRista on 2007-07-20
> **meborc said:**
> what is the exact error you get when running```
sudo apt-get update
sudo apt-get -f install
```?

I don't think there was an error when I tried with this sudo command, I believe this command restarted and finished the unfinished installations when I was getting dpkg error, but what happens now is the total inability to install and uninstall programs. When I start add/remove or synaptic package manager, it shows that it is doing something, but nothing happens. That is why I believe there is a corruption in the system.

---

### Post by rillip on 2007-07-20
could try booting from a live CD and, dumb as it sounds, try reinstalling dpkg?

---

### Post by Che_GueVaRRista on 2007-07-21
Thanks.

Can you tell me what is meant by "live CD", is it just the installation CD of Ubuntu?



I have installed Ubuntu with Wubi 7.0.4, on the virtual drive, haven't had any touch with installation CD, how would I install dpkg from the CD (or better to ask, is there a non destructive way to do the same thing?)




Thanks a lot for your answer.

---

### Post by Che_GueVaRRista on 2007-07-21
[COLOR="Sienna"][B]I just found the solution.


I have the issue with the program called Moodle. It is a stubborn program, and it won't let you uninstall it (or finish proper installation) unless it is configured. That is what is blocking the terminal and synaptic package manager to get on with the installation and updates of other software.



To resolve this, I went to synaptic package manager, and search for Moodle. After that I marked "Moodle" for reinstallation. I clicked on apply. In the beginning it is going to ask you to configure it. Select the offered settings and put in your password, just to get thru with it. 


Then I apply the changes, and  this will finally eliminate the errors and the installation holdup I was going through.


This way I could get all the system updates, I could install it it and all the trouble was over.[/B][/COLOR]

---

