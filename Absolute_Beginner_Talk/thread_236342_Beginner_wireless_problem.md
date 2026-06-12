---
title: "Beginner wireless problem"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Robopop on 2006-08-14
Hi!
I'm a long time Windows user and last week i decided to try Ubuntu. I had some troubles installing Dapper so temporary I have Ubuntu 5.10. I'm using GRUB to dual-boot Windows/Ubuntu.

The problem is that I'm totally new with Linux and I can't get my internet connection to work. I'm using a D-link DWL-510 wireless network card and I really would appriciate some beginners help! When I check my network stats I only find "eth01" and another modem connection ("PPP") but no wlan. I've been searching forums here and found some treads about something called "ndiswrapper", I read some but only understood half of it so it because of that I'm making a new post. I checked "device-manager" and there I saw my card on the list, so I belive Ubuntu has found the card. 

I found this:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

I can't understand this: 
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf

How do I link from the CD?

I saw the "wireless" part of ubuntuforums but because I'm totally raw with Linux I prefered posting here.
If somebody can help me so please take it as easy with me as possible, I'm new at Ubuntu and my English isn't perfect either.

//Robopop

---

### Post by Longer on 2006-08-14
> **Robopop said:**
> I can't understand this: 
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf On your CD in folder DRIVERS/WIN_XP(I`m not sure...) Is file: AIRPLUS.INF... That`s file what you need... You should search this file... :D

---

### Post by Robopop on 2006-08-14
How do i write the URL to the CD?

/CD/Driver/whatever.inf   ?

---

### Post by Longer on 2006-08-15
You can copy this file to desktop, and then you can use this: /home/your_login/Desktop/AIRPLUS.INF

---

