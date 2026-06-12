---
title: "modem madness"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by SVDtiger on 2007-07-31
hello everyone 

i have a best data 55k hardware modem i purchased so i could access the net with my new ubuntu. all is going pretty well consdiering im a challenged user.not just newb but sight issues too. my only issue has been the shut down button disappeared but you folks taught me "sudo halt" from terminal and thats fine

i need to find out if there is any way besides a big beach towel to make my modem be silent? the settings in networking have no effect on its screeching. my gal is threatening my dear little modem now. if i cover it then it heats up  and thats not something i want to happen.

much thanks as always, john

---

### Post by ddrichardson on 2007-07-31
The hayes dataset command for a silent modem is L0. You need to add this to whatever script dials your modem.

---

### Post by SVDtiger on 2007-07-31
thank you, i had totally forgotten about init string commands like that. how might i access the  script to enter the command?

---

### Post by phidia on 2007-07-31
> **SVDtiger said:**
> thank you, i had totally forgotten about init string commands like that. how might i access the  script to enter the command?

In debian based distros the string is in /etc/chatscripts and the correct entry which should be inserted between ATDT is M0L0. that's the letters "M" & "L" with the numeral "0"

> ATM0L0DT

---

### Post by ddrichardson on 2007-07-31
I'll be honest - I haven't used a modem in years. The scripts used to be in /etc/chatscripts I think it was pppconf.

---

### Post by SVDtiger on 2007-07-31
much thanks to you both. i will go try that right now.

---

### Post by SVDtiger on 2007-07-31
ok i found the proper place but it will not let me write the change of course. how is the quickest easiest way to edit the dial command or change to 

if any part of computers mess me up its the config as i know of no way to magnify them so i can acutally see them now. i would not even attempt this if my woman was not all over me like a bad hat. i still dont know much about ubuntu except i love it. not being able to read well or at all puts damper on things.

fortunately most everything worked well from my start with dapper. except cd/dvd but thats another thread and its just not set up correctly. 

how do get access to write to the modem command file?

---

### Post by ddrichardson on 2007-07-31
The assistive technology screen magnifier can help - its under system/preferences/accesibility

---

### Post by phidia on 2007-07-31
When you say it will not let you change(edit) are you using > sudoto open your editor of choice? For people new to linux gedit is often recommended. so the command would be:
> sudo gedit /etc/chatscripts  I suggest you back up your original chatscripts file.

I recently was able to get DSL, but I've used dial up for a long time.

---

### Post by Irihapeti on 2007-07-31
You could try installing and using Gnome-PPP to edit the modem script. I found it worked more quickly for me than trying to use the command line, and it's a lot easier to see as well.

It works in feisty. Presumably it's available for earlier distros as well.

HTH
Irihapeti

---

### Post by SVDtiger on 2007-07-31
i will back up the modem file and use the gedit to edit the atdt command.

the screen reader and magnifier will be a super help to me if i can make them run and learn to use them. . even with my pc  being old it does pretty good now thanks to ubuntu.6.06 . if i had all the former winwoes i would never touch it again due to not being able to maintain it

hopefully one day i can get a newer box from madtux , then move up to 6.10 or even further as im pretty sure new apps will come along. could not get 6.10 to install but 6.06 went perfectly as far as i know anyway

you folks are most excellent and im very grateful for the guidance as always. john

---

### Post by ddrichardson on 2007-07-31
> **phidia said:**
> When you say it will not let you change(edit) are you using to open your editor of choice? For people new to linux gedit is often recommended. so the command would be:
  I suggest you back up your original chatscripts file.

I recently was able to get DSL, but I've used dial up for a long time.

It's recommended that for X progams you use:

```
gksudo gedit /etc/chatscripts
```.

I got picked up for this recently - ;-)

---

### Post by SVDtiger on 2007-07-31
sorry guys neither one gives me access to edit. i think ill just leave it alone before i cant get online at all. she can just deal with modem screech. i sorta like it as i can tell when im hooked up.

(gedit:6676): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
application finalize called


ill let you know if i do get the adaptive apps to help me. highest regards, john

---

