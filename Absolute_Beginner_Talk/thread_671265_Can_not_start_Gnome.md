---
title: "Can not start Gnome"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by BodaciousBrian on 2008-01-18
When my computer boots up. it puts me to the log in screen after trying to do the automatic log in.  I put my username and passsowrd in, the screen trys to change resolution, and goes right back to the login screen again.  I can start when i use the failsafe gnome option.

I just updated, and i also tried to play a game(soldat) when it crashed(perfectly normal!)  Other than that, i don't know what caused this!

Any ideas?

Thanks!

---

### Post by simonjcruse on 2008-01-18
got the same problem, thought it was to do with the xorg update today? seems to work in failsafe mode only! its also strange when i press ctrl-alt-F1 i dont get a command line? Been working on this for 8 hours now, still no luck. 

Anybody else had this problem after the update?

---

### Post by imT on 2008-01-18
well i'm a lil bit newbie too, 
try use another username/account and if the problem persists try a reinstall,
other than that i cant say...goodluck :)

---

### Post by hyper_ch on 2008-01-18
can you login using fail-safe / recovery mode?

I think you end up on the command line, enter then:

```

startx

```

---

### Post by BodaciousBrian on 2008-01-18
I can start in fail safe just fine, I can also access my other consoles via ctrl+alt+fX.  X is all ready running.

---

### Post by hyper_ch on 2008-01-18
then create a new user and make him admin and then login with that and copy all the stuff back or create a new user, login with that one and the copy the new user's configs to your old one...

---

### Post by eolson on 2008-01-18
Y'all wouldn't be using Hardy would ya?

---

### Post by BodaciousBrian on 2008-01-18
7.10  is what im on.. Gutsy i think is its name =)

Hyper, i made an administrator, he had the same problem.

Also, i cant run any games!  no wine games, no xmoto...  I can use firefox, terminal, and notepad.

---

### Post by eolson on 2008-01-18
Right.  The reason I asked is that I've been playing with Hardy on my laptop and it did the same thing on an update.  Didn't worry me much because you kind of expect weird things when you're plaing around with software that's still in alfa.   Anyway here's part of what happened to me.  The Xorg.conf file was overwritten with just a basic shell.  Something else was done also because I replaced the overwritten file with a known good one (that I'd previously saved to a usb stick).  And things were still messed up.   To make a very long story short, probably your best bet is to file a bug report and reinstall Gutsy but DO NOT do the updates.  You can install software from the repos,  but stay away from the update button.

I hope somebody has a better answer.

---

### Post by BodaciousBrian on 2008-01-18
Me too!  Is there a list of what updates were applied today?  And perhaps a way to undo them?

---

### Post by sebbouckaert on 2008-01-18
I have a Nvidia card + driver and compiz running on 7.10 and I have the same problem. Couldn't get it fixed, and had lots of other PC work and little time today, so after backing up my e-mails in failsafe mode I reverted back to an earlier image of my Gutsy partition from within Windows XP. 
This sort of stuff shouldn't really happen and is very annoying. What if I did not have a dual boot?
Of course I now have again a list of new updates waiting, but I think I'll wait with installing those for now.:(

---

### Post by simonjcruse on 2008-01-18
same problems here... Tried to downgrade Xorg thru synaptic but didnt work. HELP

---

### Post by hyper_ch on 2008-01-18
> **BodaciousBrian said:**
> Also, i cant run any games!  no wine games, no xmoto...  I can use firefox, terminal, and notepad.

well, you'd have to reset this up for the new user (or copy configs from the old one)

---

### Post by usprinter on 2008-01-18
i have the exactly same problem.
i delete whole of my home folder but it doesn't help

seems related to recent updates :confused:

---

### Post by BodaciousBrian on 2008-01-18
Again, making a new user has no effect on my ability to start gnome normally.

---

### Post by al108 on 2008-01-19
I have same problem. Restarted after update and whoops... It plays the "happy music" and gnome restarts.

---

### Post by al108 on 2008-01-19
As I was typing it my update light went on and it offered another xorg update, but to no avail. I saw gnome panels for a brief moment and that's it - goes back to login screen. Still works in "fail safe gnome" though.

---

### Post by al108 on 2008-01-19
Read some other posts and reinstalling Nvidia drivers was a solution for me. Perhaps it had something to do with overwriting a link to libglx.so.XXX libglx.so where XXX is your driver version. But I've just installed new driver, since Nvidia already had an update from the last time I installed it.

---

### Post by BodaciousBrian on 2008-01-19
I reinstalled the Nvidia driver, That made it worse.. I switched the xorg.conf to say "nv" instead of "nvidia" now i can get into x normally, but have no graphics acceleration..

---

### Post by unarmedninja on 2008-01-19
i had the same problem. i read the bug report posted on digg. there was a problem with xorg overwriting the nvidia drivers. I just reinstalled the previous xorg and then the nvidia drivers again and everything is fine now.

this links to the bug report. theres a few work arounds in there somewhere.
[http://digg.com/linux_unix/Ubuntu_update_break_java_wxwidgets_and_wxpython_application](http://digg.com/linux_unix/Ubuntu_update_break_java_wxwidgets_and_wxpython_application)

---

### Post by roastbeef on 2008-01-20
I didn't rollback anything - I just applied the latest updates then installed the latest nvidia drivers from nvidia.  This fixed my problem.

It might be helpful for me to mention how to install the nvidia drivers so you don't go through the same troubles I had.  First, go to nvidia.com and get the driver file.  Restart Ubuntu.  Make sure that, once at the login screen, hit ALT+CTRL+F1, then login and type

sudo /etc/init.d/gdm stop

then type

sudo killall X
sudo killall Xorg

(Not sure if you really need to type those).

Then type 

sudo sh NVIDIA-blah-blah-blah.run

(Where NVIDIA-blah-blah-blah.sh is the name of the file you downloaded from nvidia.com)

---

### Post by David_1cog on 2008-01-20
Same problem here in Hardy.  Solved by reinstalling Nvidia driver:

1. login to 'Failsafe Gnome'
2. gksu gedit /etc/default/linux-restricted-modules-common
    add 'DISABLED_MODULES = "nv nv-new"'
3. sudo /etc/init.d/gdm stop
4. sudo sh /path/to/NVIDIA-DRIVER
5. sudo /etc/init.d/gdm start

---

### Post by goldfalcon on 2008-01-20
Just wanted to verify that I had the same issue (Gnome Failsafe only login after update, running Nvidia drivers). Problem was corrected by stopping GDM and reinstalling Nvidia drivers.

---

