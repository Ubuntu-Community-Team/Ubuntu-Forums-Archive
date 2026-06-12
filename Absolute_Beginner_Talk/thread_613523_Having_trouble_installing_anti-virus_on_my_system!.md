---
title: "Having trouble installing anti-virus on my system!!!"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Tachions on 2007-11-15
hey im trying to install avg free on my unbuntu 7.10 system, I am dual booting xp so i read its a good idea. i checked out the thread by artificial intelligence about how to install and i can only get to like step 2 because when its in the process it says stoped because of "broken pipe"!
I have no idea what that means, i even tried to down load other anti-virus programs and no luck....!
do you think it is a virus from allowing me to setup or bad install, im relatively new to linux but i'm loving every second except having trouble with this. any ideas would be helpful thanks a lot in advance!

---

### Post by delphiguy on 2007-11-15
i dont about avg in ubuntu, but i have tried clamav and it works for me. just
look it up at synaptic, you may also install the gui frontend of clamav, theres 
quite a few, but i prefer Klamav.

---

### Post by Tachions on 2007-11-15
hey I just installed clamav, thanks for the heads up, would really like to possibly get avg working, used it while in my windows days and had no problems. 

as for clamav when I run a scan it only check like 4 files it says, anyway to get it to scan my whole system...? 

thanks a lot for your help

---

### Post by delphiguy on 2007-11-15
first you need to update the virus signature by issuing this in terminal
sudo freshclam

then to scan the whole filesystem just issue this in terminal
sudo clamscan -ri /

this would take some time to finish though.  another option is for you to 
install the gui frontend for clamav, which is Klamav.

hope this helps.

---

### Post by Sef on 2007-11-15
[Install AVG]("http://ubuntuforums.org/showthread.php?t=610057&highlight=AVG") on Ubuntu.

---

### Post by Tachions on 2007-11-15
I checked your thread SEF and thanks for your help but when you say the gui, you mean the option when you click dl the .deb file for avg and open with command. I have doen that many times and nothing shows up in my applications list. i even have the file on my desktop right now bc i wanted to install it through the terminal. 
Nothing still so if you have any other ideas would be awesome! thanks

---

### Post by Tachions on 2007-11-15
bump

---

### Post by Tachions on 2007-11-15
bump

---

