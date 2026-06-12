---
title: "System tray clock"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-26
People,

I configured the system clock UTC offset to -2:00, yet it displays the wrong time as if I were in UTC 0:00 time zone.

For instance: it is 4:15PM here and Ubuntu's clock is 6:15PM.

How do I fix this?

Thanks in advance.

---

### Post by ShakingSpirit on 2005-11-26
Right click the clock -> Adjust Date & Time

Simple :) It wont automatically change time to match your timezone unless you tell it to synchronize time from the internet time servers.

---

### Post by paulozzzz on 2005-11-26
:confused: 

Well, I had to choose a location in the UTC 0:00 timezone which is not true.  Strange...

Thanks, it worked.

---

### Post by paulozzzz on 2005-11-26
Still I found it illogical to uncheck the "Use UTC" option and Ubuntu insists in displaying the UTC time.

---

### Post by teaker1s on 2005-11-26
administration- time and date change your time zone and untick periodically syncronize clock with internet servers
administration-services and untick clock syncronisation service if you still can't stop it

---

### Post by atoponce on 2005-11-26
What is your hardware clock set to?  When you installed Ubuntu, how did you answer the question when it asked you if your hardware clock was set to GMT?

Your clock in the system tray sets itself to an offset from the hardware clock based on the timezone you set in Ubuntu.  I imagine that your hardware clock is not set to GMT.  You can change it in your BIOS.  Check that.

---

### Post by paulozzzz on 2005-11-26
"administration- ... untick periodically syncronize clock with internet servers"

It was unchecked already.

"administration-services and untick clock syncronisation service if you still can't stop it"

There is no such option in my System->Administration menu.

Thanks.

---

### Post by paulozzzz on 2005-11-26
"What is your hardware clock set to? When you installed Ubuntu, how did you answer the question when it asked you if your hardware clock was set to GMT?"

I do not remember.

"Your clock in the system tray sets itself to an offset from the hardware clock based on the timezone you set in Ubuntu. I imagine that your hardware clock is not set to GMT. You can change it in your BIOS. Check that."

There is no way to adjust the HW clock in my CMOS setup utility.  You know those obscure notebook setups...  I can reboot with Windows and know for sure the HW time.

---

### Post by ssam on 2005-11-26
unix and windows deal with time differently. windows sets the hardware clock to localtime, and you adjust the hardware clock whenever you change timezones or for daylight saving time.

unix (tradisionally) keeps the hardware clock in UTC, and then calculates the local time from that. this is because UTC never goes backwards (appart from the occasional subtractive leap second), and severs need to know the order things happened. It also makes it easier for different users/programs to have different time zones.

if you just run linux on you computer then you want to have the hardware clock in UTC, if you want to dual boot, then you need the hardware clock in localtime (to make windows happy). perhaps during the install you told ubuntu that the hardware clock was in UTC when it isnt.

---

### Post by teaker1s on 2005-11-26
strange services is missing use 'gksudo services-admin' in terminal to access it

---

### Post by paulozzzz on 2005-11-26
[QUOTE=teaker1s]strange services is missing use 'gksudo services-admin' in terminal to access it[/QUOTE]

It does not work.  I type the command, the system requests password, I type my password, nothing happens. 

1)The console outputs "sudo: services-as"
2)The password dialog appears.
3)I enter the password.
4)The console outputs "udo:" and gets back to the command prompt.

:confused:

---

### Post by ssam on 2005-11-27
you have to do it without the quotes
```
gksudo services-admin
```

---

### Post by paulozzzz on 2005-11-27
[QUOTE=ssam]you have to do it without the quotes
```
gksudo services-admin
```[/QUOTE]

It requested password input, then it seemed that nothing happened.

---

