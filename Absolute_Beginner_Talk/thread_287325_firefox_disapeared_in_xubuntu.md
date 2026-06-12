---
title: "firefox disapeared in xubuntu"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by slipperhead on 2006-10-28
hello all

i just installed xubuntu on a toshiba 320cdt 233mhz 96mb, which i know is below the requirements. it ran quite well until firefox just disapeared while surfing .(took awhile though before i figured out how to get it on the net)
 when i tried to reopen firefox, it notified me it was still running but i could not find it to close it.i assume its a memory problem although xubuntu in general ran quite well with a big swap file.
being quite new to linux, i could not find a task manager or anything to stop running programs. (daft question time)is there such a thing?

---

### Post by whizbaby on 2006-10-28
There are (more than) two ways to manage tasks

(1)install xubuntu task manager:
xfce4-taskmanager - taskmanager for xfce

obviously will not work when xfce doesn't (e.g. Xserver broken) so its powers are limited.

(2)use **ps aux** (yes in terminal) for a list of processes and the tools killall and kill to stop processes.

To your firefox problem: perhaps a firefox task is running. If so, kill it. If not (e.g. you restarted the computer) remove the lock

rm .mozilla/firefox/_!!!random_string!!!_.default/lock

(where _!!!random_string!!!_ really is random, e.g. jodnsfmid.default, you'll have to look up yours)
and try again.

---

### Post by slipperhead on 2006-10-28
install xubuntu task manager:
xfce4-taskmanager - taskmanager for xfce


thankyou,so i was looking for something that wasnt there!
i didnt know about ps aux,still learning.
so ps aux should also work when i cant restart x after doing ctrl alt 1 because of a lock?

---

### Post by whizbaby on 2006-10-29
ps aux is a terminal program, so if you are still able to switch to virtual console (which you will be 99% of the time) you can use it (e.g. as you said ctrl-alt-f1).
**ps aux** and **top**(realtime) to monitor procs and
**kill, killall** does more than replacing the dozers task manager (which doesn't even come up sometimes as I remember).

---

### Post by slipperhead on 2006-10-29
thanks, all is working as it should. i am now ready to install on my main pc now that i know the basics!


ps.just how do you pronounce linux - lin as in win(dows) or lin as in line.
 (hangs head in shame,dont know anyone who uses it to hear how they say it!)

---

### Post by NeoLithium on 2006-10-29
Well, there is a recording of Linus pronouncing it "Lih Nux", some people say "Lie-nux"...I just call it better than windows.

---

### Post by slipperhead on 2006-10-29
hmmm, no definitive answer then. i,ll go with lih nux then! rolls off the tongue easier!
and ubuntu/xubuntu? i,m thinking oohbuntoo/zoobuntoo!
if i,m going to sing its praises to my friends it would be good to be able to pronounce them!

(i,ll stop asking silly questions now!)

---

