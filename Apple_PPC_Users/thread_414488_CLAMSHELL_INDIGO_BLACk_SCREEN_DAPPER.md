---
title: "CLAMSHELL INDIGO BLACk SCREEN DAPPER"
date: 2007-04-19
forum: Apple PPC Users
---

### Post by bigred3373 on 2007-04-19
HELLO

 i** have been trying to install dapper on my old clamshell 366mhz fire wire 10gb 350mb ram it installs and goes through the normal process then goes to the black screen. How do i change the preferences for the screen the refresh and vert?  **

---

### Post by phummers on 2007-05-09
> **bigred3373 said:**
> HELLO

 **i have been trying to install dapper on my old clamshell 366mhz fire wire 10gb 350mb ram it installs and goes through the normal process then goes to the black screen. How do i change the preferences for the screen the refresh and vert?  **

Have you tried Control-Option-F2'ing from the black screen to another terminal? That should get you a command-line terminal without X. Log in and have a look with an editor at the /etc/X11/xorg.conf file. (nano is a nice editor if you're not familiar with vi.) 

cd /etc/X11 (changing directories)
sudo cp xorg.conf xorg.conf.orig (backing up the original file)
sudo nano xorg.conf

The xorg.conf man page (man xorg.conf) should give some hints as to what to look for.

and after any changes switch back to X -- Opt-F7 --  and restart X with Control-Option-Backspace to check out the result.

---

