---
title: "Login window goes blank, but desktop loads fine"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by DigitalDaiquiri on 2006-11-14
Hey all, I want to start out by stating that I'm a new Linux user, and I have tried to look through all of the available documentation such as the wiki, and past forum posts and wasn't able to find a solution to my problem.  I recently installed the ATI drivers provided by AMD.  Everything seemingly worked fine, as I was able to properly adjust my resolution and monitors refresh rate; that was until I rebooted.  For some reason my login window appeared only as a blank black screen.  After fumbling around with the keyboard I finally managed to log in, only to realize that my desktop environment booted up just fine.  I then went to switch users to see if the problem was consistent every time I accessed the login screen, only to find that it loaded just fine.  I figured that there must have been a driver load error, so I tried rebooting to no avail as the problem reoccurred.  Finally I tried reconfiguring xserver by typing the following into the terminal: 

```
sudo dpkg-reconfigure xserver-xorg
```

Completing the setup process just reverted the display drivers back to the fglrx driver.  As a temporary solution I enabled automatic login.  Just for reference I am currently running the following hardware:

[LIST]
[*]Gigabyte K7 Triton - GA-7S748 Series – AMD Socket A
[*]ATI Radeon 9500 Pro
[*]AMD Athalon 2500+ Barton Core Socket A
[*]128 MB DDR RAM
[/LIST]

Thank you all for your time and help!!! :-D

---

### Post by ReaderRat on 2006-11-14
[**ATI Radeon 8500 & Higher Video cards**](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

