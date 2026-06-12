---
title: "Blink a led on laptop when receiving an email?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-22
Is there a way to get the email led to blink in Ubuntu?

In windows the blue led on my laptop would blink when there was a new email in Outlook. It's a very helpful feature when you are away from the laptop, you can simply glance at it from a distance and if the blue led is on you know you've got mail (help when you don't want an audio signal).

Thanks.

---

### Post by linux_kid on 2007-02-22
Cool feature...
What exact light do you want to blink?

---

### Post by arkangel on 2007-02-22
I have the same trivial and really small problem , i mean  my laptop has a led for telling me when i got a email,  you probably will have to link the led with the email client post if you succeed ;) I have an Asus A6Va  here  
the  led state can be found if you type in terminal 
# cat /proc/acpi/asus/mled

this  guy with these laptops   (debian) had the time and the patience to  set up this stuff,  give it a try  ;)

[http://www.i-jeriko.de/2006/03/03/debian-sarge-on-asus-a6va/]("http://www.i-jeriko.de/2006/03/03/debian-sarge-on-asus-a6va/")

---

### Post by PartisanEntity on 2007-02-22
> **linux_kid said:**
> Cool feature...
What exact light do you want to blink?

This one: :)

---

### Post by PartisanEntity on 2007-02-22
Okay I found [this page]("http://www.asusforum.encke.net/modules/dokuwiki/hotkeys_unter_linux_konfigurieren") (in German) where it is explained how to tget the hotkeys working under linux.

In my case the hotkeys are already working, and so are all of the LEDs except for the email one.

I found this script which misuses the email LED for speedstepping feedback, I am wondering if anyone knows how to rewrite this script to make it blink when Evolution gets new emails?

```
#!/bin/sh
 
# Helper script to update the LEDs of an ASUS notebook
######################################################
 
# update e-mail led (which is misused as an indicator for manual speedstepping)
###############################################################################
 
if cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor | grep -q powersave ||
    cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor | grep -q performance ||
    cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor | grep -q userspace; then
    echo 1 > /proc/acpi/asus/mled
else
    echo 0 > /proc/acpi/asus/mled
fi
 
 
exit 0
```

---

### Post by PartisanEntity on 2007-03-13
I found a way to get the email LED on my Asus A6k notebook to light up when new emails arrive and to turn off when I have viewed these emails.

You need to install the mail-notification and mail-notification-evolution packages from the repos.

Then you go to Applications > Internet > Mail Notification in order to set it up.

Click on 'Add', select a mail reader (for example Evolution) or a method (for example POP3) then select the mailbox or enter the POP3 data. Select how often you want Mail Notification to check for emails (for example 5 mins)  then once you are done click 'Add'.

Then in the 'Commands' section (making sure both are ticked) enter the following where it says:

'When new email arrives': 
```
echo 1 > /proc/acpi/asus/mled
```

'When all mail has been read':
```
echo 0 > /proc/acpi/asus/mled
```

That's it, close and then test it by sending yourself an email. For those using Evolution the LED will turn on as soon as the email has been downloaded into your Inbox. For those using POP3 or some other remote method the LED will only light up when Mail Notification checks (for example every 5 mins).

This method should work for any laptop model, you just need to search the web to find out the location of modules that turn the LED on and off.

p.s. If you would like an icon to appear and remain in the notification tray then click on the 'Status Icon' tab and tick 'Always Display'.

Enjoy :)

---

