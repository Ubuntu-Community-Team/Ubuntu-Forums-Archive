---
title: "Can locate IP address"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by creatingpurpose on 2007-11-05
I am really an absolute beginner here so bear with me. I have a Linksys wireless router connected into a modem for my ISP. I also have WiFi Radar. (all installed by my son, who thought I should try using this system rather than the "M").  I have been using this successfully for 6 months but now cannot get on the Internet.  I have two laptops, one with "M" operating system and it still works fine, so I know it is not the router or modem.  When I open "networking" , it is defaulted to Wired Connection. I open up wireless Connection, enable, put in my network name and password, leave the configuration at DHCP but nothing happens.  Tried doing this and rebooting, but nothing. I tried looking at Network tools and using that IP address and Netmask to put in the Static IP portion, but no luck.  I think this is something pretty simple but cannot figure it out. Can anyone help?

---

### Post by wieman01 on 2007-11-05
Ok, it will be tough to help if we don't do a bit of command line... hope that's ok with you. First of all, I would ask you to scan for wireless networks after opening a terminal window:
> sudo iwlist scan
Then type in your password. If that does not work, do this please:
> iwlist scan
Now... is your network listed? Or is there no output at all?

---

