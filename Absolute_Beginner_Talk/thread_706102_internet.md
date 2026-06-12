---
title: "internet"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by nagaraj on 2008-02-24
i've been using ubuntu for the last 3 months on a wired LAN with wired internet connection(adsl). there are 6 pcs on the net and 4 have only ubuntu as the sole os and two have win xp as well. yesterday all ubuntu pcs stopped connecting to the net while the ones with xp connect when booted with xp and dont when booted with linux. i'm at aloss to find any explanations. can anybody help me find the reasons and a solution?

---

### Post by jeffus_il on 2008-02-24
What changes took place on your network before this happened? Changes to the router?

---

### Post by toa on 2008-02-24
> **nagaraj said:**
> i've been using ubuntu for the last 3 months on a wired LAN with wired internet connection(adsl). there are 6 pcs on the net and 4 have only ubuntu as the sole os and two have win xp as well. yesterday all ubuntu pcs stopped connecting to the net while the ones with xp connect when booted with xp and dont when booted with linux. i'm at aloss to find any explanations. can anybody help me find the reasons and a solution?

There is a cause for something, maybe it was an update which took place in the background, or an application installed on all PC's, check the previuos log files of the past days for any changes.

Something installed changed the network settings or resetted the settings, or a firewall installed ... something!

---

### Post by nagaraj on 2008-02-24
how do i check that? i mean the log and the firewall or changes in setings?

---

### Post by toa on 2008-02-24
> **nagaraj said:**
> how do i check that? i mean the log and the firewall or changes in setings?

The main thing is checking any changes occured on the network settings of your system, any LAN changes, did you configure the systems manually before or Ubuntu connected with default settings, anything changed from that, try connecting one of the PC's to a seperate labtop via cable, see if the network recognizes the labtop.

for the log files, which ill keep as a last option.

Click on System menu > Choose Administration > System Log:

(The GNOME System Log Viewer) 

You can also start the GNOME System Log Viewer from a shell prompt, by entering the following command:
$ gnome-system-log &

---

### Post by nagaraj on 2008-02-24
i'll go thro the log and c if i can solve the problem

---

### Post by toa on 2008-02-24
> **nagaraj said:**
> i'll go thro the log and c if i can solve the problem

i still assume its an update or something that was installed, since all the PC's had the same problem at once...

---

### Post by nagaraj on 2008-02-25
tried tracking changes in the recent past. no apparent changes have been made to the network and internet configurations. tried connecting a laptop to the network. the laptop gets recognised on the network. tried pinging from all terminals. works fine. but still no internet connection on ubuntu terminals.went thro the trubleshooting as well and tried pinging ubuntu.com. gives error message saying there is no such address. any more suggestions? thinking of reinstalling ubuntu. 'll it help?

---

### Post by nagaraj on 2008-02-25
tried connecting with the ubuntu installation cd, even that could not connect!!!

---

