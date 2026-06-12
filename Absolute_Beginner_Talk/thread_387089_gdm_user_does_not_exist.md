---
title: "gdm user does not exist"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by leatherworker on 2007-03-17
Hi there,

I upgraded this week with the regular upgrades that arrive and when I restarted my machine the next day, Gnome did not load - instead I got a message that said :

GDM user gdm does not exist, correct GDM and restart (exact message might be different) - I am using a different machine to post this)

Then in pressed Enter and got the command line prompt....

please help!   I searched the web and this forum, but Do not find the correct help....

JOhan

---

### Post by leatherworker on 2007-03-17
I have now tried  gdmsetup   from the command prompt,

but then I get gtk-warning:  cannot open display

Please help!

---

### Post by rylangrayston on 2008-03-30
my younger bother is having the same problem
i am hear for help on his behalf

---

### Post by rylangrayston on 2008-03-30
gnome Display Manager (GDM)
my bro tried

 sudo apt-get -f install

with no aperent result

see a similar thread  [http://ubuntuforums.org/showthread.php?t=267503](http://ubuntuforums.org/showthread.php?t=267503)

---

### Post by rylangrayston on 2008-03-31
i am at my brothers house hear is some more accurate info

Intell Pentium 3      498.2 mega hertz
L1 cache 32K 4884MB/S
L2 cache 512K 640MB/S
chipset : VT82C691/693A/694X

512 mega bites of random access memory  290MB/s

soon after clicing the update button on march 30 2008 his computer screen flashed multiple times 
and on reboot returns a screen with the folowing mesage

 

                                                The GDM user 'gdm' dose not exist.  Please correct GDM
                                                configuration and restart GDM.

                                                                                      <ok>


after hitting enter the computer screen shows a command line login
after logging in i tried the following commands bellow 

user:~$ gdmsetup

(gdmsetup:4779): Gtk-WARNING **: cannot open display:
user:~$  sudo apt-get -f install
user:~$

---

