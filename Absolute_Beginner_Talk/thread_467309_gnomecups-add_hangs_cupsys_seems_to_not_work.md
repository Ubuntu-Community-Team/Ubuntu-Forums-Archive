---
title: "gnomecups-add hangs cupsys seems to not work"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by mlentink on 2007-06-07
This is one I can't seem to find an answer to, so I am hoping you can point me in the right direction.

I recently installed Ubuntu 7.04 as a dual boot with Windows XP Pro on my notebook, a HP Compaq nx 7400 ( Intel Core Duo 1.66 G, 1 GB RAM, Intel Graphics and Intel 3945 ABG Wireless). 

Now just today I wanted to add my two networked printers (both HP). 
But I didn't get that far: I did System>Admin>Printers, clicked on Add Printer and then the little Gnome-CUPS-Add window. And kept telling me it was reading the CUPS database. And kept telling me it was reading the CUPS database. And kept telling me it was reading the CUPS database.
So I killed that after 10 minutes and started searching these forums. I found and tried this: "http://localhost:631" , which brought up the CUPS HTML interface, which I didn't know existed. Tried to add a printer through that.  Which did not do anything either.
So I tried to see if the process CUPS was running by looking at System>Admin>Services, where cups is checked.
Next I tried to restart it by doing 
```
sudo /etc/init.d/cups restart
```
and was told such a command does not exist. So I cd-ed to that directory and indeed, there's no cups, but there is a cupsys, which I then 
```
sudo cupsys restart
```
which also told me "command not found". I did another ls and it really listed 'cupsys' in there. 
I fiinally fired up system monitor to look at running processes and (as I kinda expected) no cups, no cupsys, the only remotely related was gnome-cups-icon.

What am I doing wrong?

---

### Post by mlentink on 2007-06-07
Addition:
Just tried again and to a look at the System Montor gnome-cups-add shows up in there, but it 'sleeps' (boy, does it ever!).
The only strange thing I can find in the system logs is a number of lines that say 
Creating missing directory '/var/run/cups/certs"
I checked, but that directory does exist. I forgot how to check permissions on that, but will try to find out.

For now it&#347; bedtime for me, I just hope that some of you in more user-friendly timezones will be able to come up with a suggestion on what to do next.

for that: thanks in advance, and if more info is needed, let me know

---

### Post by mlentink on 2007-06-08
bump
No cups guru's around?

---

### Post by mlentink on 2007-06-08
I am not really sure whether this is relevant, but it could be. I found something on Launchpad about a hanging gnome-cups-add, that seemed to be related to the locale used. I use Nl-nl (yeah, I know).

Has this happened to other non US-locale-users before?

thx for ***any*** pointers at all!

---

### Post by mlentink on 2007-06-08
Found it!

Starting gnome-cups-manager in terminal immediately gave me a number of error messages, complaing that T-ish metal (the gnome theme I using) is not supported by Clearlooks. But this time, I did get printers to select and it immediately recoiginzed my OfficeJet 6310. 

So I'm printing!

Now I have to troubleshoot that T-ish Metal vs Clearlooks thing. But for that there's no hurry, because everything is working...

---

