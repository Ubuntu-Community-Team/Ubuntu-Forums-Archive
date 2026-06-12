---
title: "Starting Scripts from Cairo Dock"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by gotee12 on 2008-02-14
Hey guys,

I need some help in figuring out why a custom launcher in Cairo Dock is not working properly. I've created two scripts, one that starts the Cisco VPN client and another that does some housekeeping (apt-get clean/remove old bootcharts). 

Anyway, I've made a launcher in Cairo Dock for each of these scripts but they never execute when I attempt to start them from Cairo. The scripts work properly if I run them from the location in which they actually reside (/home). 

I've added other launcher's to Cairo (Putty, CCSM, etc) and they work fine. Is there an extra step involved with getting bash scripts to execute in Cairo? Thanx in advance.

gotee12

---

### Post by gotee12 on 2008-02-17
Anybody have any idea? Thanx.

---

### Post by GoingDown on 2008-04-08
You should launch them inside terminal, using command line like:

/usr/bin/gnome-terminal -e {your command}

Of course replace gnome-terminal with the terminal you use (kterm, xterm). Of course command line switch for running script within the terminal might be different for different terminals.

For example, following runs my VPN script:

/usr//bin/gnome-terminal -e /home/xxx/myvpn.sh

---

### Post by manicnerd on 2008-05-13
> **GoingDown said:**
> You should launch them inside terminal, using command line like:

/usr/bin/gnome-terminal -e {your command}

Of course replace gnome-terminal with the terminal you use (kterm, xterm). Of course command line switch for running script within the terminal might be different for different terminals.

For example, following runs my VPN script:

/usr//bin/gnome-terminal -e /home/xxx/myvpn.sh

This was very helpful in solving my cairo-dock problem.  I was trying to launch matlab with the -nojvm option .... the command for my launcher ended up being:

gnome-terminal -x matlab -nojvm

i had to use -x instead of -e because of the -nojvm option

---

