---
title: "Multiple Problems"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2008-01-21
[COLOR="Red"][SIZE="7"]Warning:
This post might result in causing you headache and might waste quite a lot of your time :P :D [/SIZE][/COLOR]

System Specs:
Ubuntu 7.10 Fully Updated
Yamaha 724
Intel Somewhat lan card
i think that would be enough


Well here it starts:
Yesterday i was working on my system, everything was going fine, like surfing, playing music, copy and pasting data into one partition to another. I had to restart the system, now when i started back there was this problem:
Both gnome panels has gone to their homes , and i couldnt even use the shortcut keys like Alt-F1/F2, I even tried the failsafe and default gnome but no use, everything else e.g. sound, internet was working fine till this moment.

I went to #ubuntu and asked it there, someone suggested me to paste another user's .gnome* to my directory, which i tried but no use. after a long struggle, and waking up all night, i found that there was problem in the "session" file, I created a new account, copied all data to his home, gave him rights, and deleted the malfunctioning session file, and now he can see panels.

Problems are:
That user cant access any partition, or admin tools, how do i make him sudo? i mean i login using root into X11 and try to open System > Admin > Users.... and it gives an error that i am not authorized to modify system configuration, i mean then why am i root?
seconldy now sound and internet on all accounts have gone, i am using a live CD and both are working fine, clicking the volume icon says that my gstreamer plugin is not configured or sound card isnt present, and believe me, i didnt even touched that. About the internet i use ADSL router, 24 hours, no login. Wehn i login i see that it is saying "establishing a connection to eth0" but it takes all my lifetime and never does....


In short:
1. How to make a user run sudo, make him a little low then root, i mean like a administrator, instead of a super administrator which is root.
2. How do i get my internet working?
3. What is the problem with sound?
4. why cant the other user see other mounted and network partitions?



Thanks a lot for reading such a long post, i am really sorry, but i am way too confused and suffering headache due to waking up all night and fixing one damn problem and facing another....

---

### Post by cotcot on 2008-01-21
Have you tried in recovery mode ? 
You can give users sudo right by editing the sudoers file using "visudo" (and nothing else). 
Maybe you could do a new install on the free space of your hdd. This does not take a lot of time (at least less than a night).

---

### Post by shoaibi on 2008-01-21
and what to do with the new install? what about these so many softwares that in installed in this lon time :(
i will try your ecovery mode tip, thanks for that, i didnt even remember that

---

### Post by Sef on 2008-01-21
> copy and pasting data into one partition to another.

What exactly did you do?  Likely you made the error here.

---

### Post by shoaibi on 2008-01-21
forget it, its wasnt what you took it as.....
i meant that everything was normal....

---

