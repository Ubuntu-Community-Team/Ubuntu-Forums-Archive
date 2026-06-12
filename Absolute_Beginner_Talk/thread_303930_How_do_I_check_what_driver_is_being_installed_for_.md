---
title: "How do I check what driver is being installed for my wlan interface(eth0)?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Andrea_44 on 2006-11-21
How do I check what driver is being installed for my wlan interface(eth0)?

Thanks,
Andrea

---

### Post by aidanr on 2006-11-21
if i go to System->Administration->Device Manager and select my network card, under the advanced tab theres a info.linux.driver string

theres a command to check from the terminal, but i can't think of it off the top of my head

edit:// "lsmod" thats the one i was thinking of:rolleyes:

---

### Post by steven8 on 2006-11-21
```
sudo lshw | less
```

A nice fella just told me this last week!!  it'll be some reading, but find your device, and it will tell the driver.

---

### Post by Andrea_44 on 2006-11-21
Thanks for the help!

Not sure if u know why Ethereal cannot detect my wireless interface? (i.e. No interface returned when "List the available capture interface" is clicked)

The driver for the wlan interface(eth0) is "orinoco_cs".
It is working properly (i.e. have internet connection).

Cheers~
Andrea

---

### Post by aidanr on 2006-11-21
[http://www.ethereal.com/faq.html#capprobunix](http://www.ethereal.com/faq.html#capprobunix)

---

### Post by rawirth on 2008-01-19
Any idea why linksys WPC11 ver4 freezes gutsy with free drivers blacklisted, ndiswrapper and accompaniing files loaded and 8180 loaded? Worked well with fawn. I actually mistyped on the blacklist and cannot find how to eliminate the bad command,actually for some reason when i type the ' symbols it does not show up and when i types it again it shows up just once but is read in the command as being there twice, in looking at the file it looks like it is there only once, but i still get the bad command error, either way I cannot figure how to change it b/c when I go to save the cahnges i am told i cannot change that file b/c it does not belong to me but belongs to the root. Thoughts?

---

