---
title: "problems with firestarter in 6.10"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by polemarchus on 2006-12-10
hi im trying to install firestarter in ubuntu 6.10 and for it to start on boot but minimised.

i have installed firestarter and it works fine, however, i still cannot get it to start on boot. i have added the line:

Joe ALL=NOPASSWD: /usr/sbin/firestarter

to /etc/sudoers

Joe being my username.

I have also added the line:

sudo firestarter –start-hidden

to the start-up option under system/preferences/sessions

however it still doesn't appear active when i boot my system. i am running ubuntu 6.10 and all seems fine apart from this minor thing.

contents of sudoers is:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Joe ALL=NOPASSWD: /usr/sbin/firestarter


thanks!

---

### Post by ferg on 2006-12-10
I took this bit from here... [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

Open up your GNOME menu, select *Preferences* followed by *Sessions*. Switch to the *Startup programs* tab, pictured right. 
  Click *Add* and enter
[FONT=georgia,terminal]sudo firestarter --start-hidden[/FONT]
as the startup command. Click *OK* and you're done. 
  To stop Firestarter from loading on login, simply remove its entry from the startup programs listing. 




Hope that's of some help. There's some more useful information on that page you might want to take a look at :)

---

### Post by TomFumb on 2006-12-14
Most of the time you'll find that firestarter actually is running and you just don't realise it - try typing 

ps aux | grep firestarter


ps aux lists the processes currently running on your computer, and grep firestarter searches the output for firestarter. Chances are you'll see that firestarter is running and it's gui simply isn't. Just load up the gui if you want to change your settings, but otherwise just let it be. 

Another way to check is to remove the splash screen from your boot-up and shutdown, and they you'll see firestarter shutting down when you switch your computer off.

---

### Post by polemarchus on 2006-12-26
nice one, thanks!

new about ps aux but had never worked the grep command before - very useful!

had worked out that by typing 

```
sudo /etc/firestarter/firestarter.sh status
```

i got the same result (kinda!)

cheers tho :)

---

