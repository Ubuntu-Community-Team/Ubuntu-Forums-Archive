---
title: "Logout Blackness"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Animortis on 2006-01-26
Alright, when logging out of my user on Ubuntu Breezy, very often, there will be nothing that happens. I'll click logout, it'll fade, go to a black screen, then sit there. Usually when these weird things happen I just let it sit til it fixes itself, then it'll never do it again, at least with Linuxes. But in this case it's definately not fixing itself.

Anyone know what I should do?

---

### Post by Pragmatist on 2006-02-05
I've had a similar problem.  First, try: ```
sudo shutdown -h now
```
Does that create the problem?  If it does, try:
```
CTRL-ALT-F4 
``` login as root and type: ```
/etc/init.d/gdm stop
```  the type: ```
startx
```  Then, once your at your desktop, go to System --> Logout  This won't give you a menu of choices like before.  Just say OK.  This should take you back to your virtual console. type: ```
CTRL-ALT-F4
``` just in case you got sent to a different one.  If that worked and you didn't get the black screen thing, then you've narrowed the problem to GNOME/GDM  probably GDM in my opinion.

The other are to work on is APIC, the power management.  There is a way to boot with APIC off.  I don't remember exactly how, but you could find that easily enough on by doing a search here.

Finally, there are settings in your GDM config file.  make a backup of your /etc/gdm/gdm.conf  then go in and find the lines dealing with power management, comment them out and see if that helps.

In all of these cases, let us know what happens.

---

