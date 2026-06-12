---
title: "WHAT is going on?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-06
i was looking through the servuices-admin menua and  turnin junk ones off, power manager and bluetooth.

it then from and logged me out, when i sdigned back in, i cant change anything!

i click on services, or users accounts and i gt this error.

The configuration could not be loaded
you are not allowed to access system configuration.

even says that when i use sudo!

ive had a few problems like this and its really getting on my nerves

so whats going on? :mad::mad::mad:

---

### Post by skymera on 2007-08-06
please, dont all rush at one...

---

### Post by Ek0nomik on 2007-08-06
I am at work, thus I am forced to use Windows at the moment.

You are opening software and trying to change things, yes?

```
gksudo programName
```

wasn't able to provider you with the proper access?

---

### Post by Gmbrdilos on 2007-08-06
I could be wrong but it seems like you have changed your own permissions.

---

### Post by milosz.galazka on 2007-08-06
Hello,

If you want to choose "services" in another way (from console) then after running *sudo su* use *update-rc.d* like

* update-rc.d openvpn defaults*    
(to start it at boot)

*update-rc.d openvpn -f remove*
(to not start it at boot)

To see all services run  *ls /etc/init.d/* 

To run X apps as root you can use *su-to-root* script.

---

### Post by eentonig on 2007-08-06
First off. Don't hurry. We're all here in our free time!!

Second, do you know what services you've turned off? Or did you just went along and turned off the ones you didn't know what good they were?

---

### Post by Tomosaur on 2007-08-06
Without a proper list of what you did, it's going to be pretty difficult getting you back up and running :S

Are you sure you know which services / daemons are, in fact, 'junk' and which are critical?

In any case, try rebooting your machine and choosing the recovery mode option in the bootloader. This should hopefully give you a root terminal, in which case maybe people will be able to help you out.

---

### Post by skymera on 2007-08-06
i turned of power managerment and bluetooth.

i can just reinstall :)

---

### Post by tqk on 2007-08-06
> **milosz.galazka said:**
> To run X apps as root you can use *su-to-root* script.

Thanks for that, but could you say more on the "su-to-root" script thing?  I've never seen that.  Exactly, what does it do?  "su" or "su -"?  xhost/XAUTHORITY, $DISPLAY, ...  If there's a webpage I can access from non-*buntu, that would be great.

BTW, I don't run *buntu, but I'm supporting someone who does (and loves it :-).  Thanks.

---

### Post by milosz.galazka on 2007-08-06
Yes of course just look at [http://www.cyberciti.biz/tips/shell-scripting-reading-a-root-password.html](http://www.cyberciti.biz/tips/shell-scripting-reading-a-root-password.html)
[http://209.85.129.104/search?q=cache:TwR62AdPnGQJ:bardolph.ling.ohio-state.edu/cgi-bin/dwww%3Ftype%3Drunman%26location%3Dsu-to-root/1+manual+%22su-to-root%22&hl=pl&ct=clnk&cd=2&gl=pl](http://209.85.129.104/search?q=cache:TwR62AdPnGQJ:bardolph.ling.ohio-state.edu/cgi-bin/dwww%3Ftype%3Drunman%26location%3Dsu-to-root/1+manual+%22su-to-root%22&hl=pl&ct=clnk&cd=2&gl=pl)

---

### Post by Caffeine_Junky on 2007-08-06
...hey there,


Re services,  if you want to look into services that you may not need you may like to have a look at this thread....[ http://ubuntuforums.org/showthread.php?t=89491&highlight=disable+unwanted+services]("http://ubuntuforums.org/showthread.php?t=89491&highlight=disable+unwanted+services")

...also have a look at **sysvconfig**  ...it can be installed via synaptic

goodluck ..and don't rush these things,  there is a learning curve to take into consideration here... :)

---

### Post by skymera on 2007-08-07
thanks, i just done a fresh install.

looking at that link now :)

---

