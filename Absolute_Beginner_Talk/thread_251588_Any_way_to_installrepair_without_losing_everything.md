---
title: "Any way to install/repair without losing everything?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crhall on 2006-09-05
Had XGL up and running fine. =)
Saw there were updates this morning and installed them. =/
Broke XGL. =(
Trying to fix it broke xserver. =_(

I've tried so many things at this point I don't know what's wrong, or what's on it, or anything. Is there any way to reinstall/restore  Ubuntu short of mounting the drive and backing off my home directory?

---

### Post by gruffy-06 on 2006-09-05
Boot up your computer and select the option that allows booting into Ubuntu recovery mode. Also, give me the output when you type in *startx*. i.e. what messages appear?

---

### Post by bulldog on 2006-09-05
To let Xgl working again, do the following.

Remove your compiz start from Preferences->session->starting programs[like thefuture,compiz-start.py or whatever]

Then on the middle tab of sessions remove every option that points to compiz.
Then set in starting programs   /usr/bin/compiz-start  to start compiz.
You can manage your plugins with 'csm' in the terminal
When you have trouble with sticking the changes you make in your plugins do:

sudo chmod 755 ~/.compiz -R

From compiz forum,

this is because compiz relies on csm instead of gconf now...
so you must start compiz differently, basically...

go to system -> prefs -> sessions -> startup programs and put in "/usr/bin/compiz-start"

EDIT:after today's update just then, /usr/share/compiz-start doesn't work for me anymore, so if it doesn't work for you, put in "compiz-start --replcae" instead...

(instead of whatever you use to start compiz currently)

also make sure you have "csm" installed and all other packages are upto-date....

then run "csm" in the terminal to change any of the settings for any plugin....

if changes in csm don't have any effect, then go into the terminal and type "sudo chmod 755 ~/.compiz -R"
if it complains about a folder being missing, then create a ".compiz" folder in ur home folder and run the command again....

then it should all work again....

---

### Post by crhall on 2006-09-05
> **gruffy-06 said:**
> Boot up your computer and select the option that allows booting into Ubuntu recovery mode. Also, give me the output when you type in *startx*. i.e. what messages appear?

Booting from disk I chose the recovery of a broken system choice. The Rescue gets hung on the network hardware detection portion.

When I try a startx, I get a 'Failed to initialized the GLX module' error. (grep for glx in xorg.conf shows nothing.) And an nvidia module not found error. 'Failed to load the nvidia kernel module'. (when I run sudo apt-get install nvidia-kernel-common it says the most recent version is installed.)

---

### Post by crhall on 2006-09-05
Thinking it might be my CD, I downloaded a new one and burned it.
Now I don't even see the Restore option. What gives?

---

