---
title: "Ubuntu forgot i had a laptop? (powermanagement grayed out)"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by bagbiter on 2007-05-09
Recently I discovered that my powermanager doesn't react if I pull out the cord from my laptop. And also the area where i change the powersaving settings for when i'm running the machine on batteries, it's all grayed out! So I tried a reinstall, but it's the same thing..

what's the deal here?

---

### Post by bagbiter on 2007-05-10
also, nothing happens when I close the laptop.. no hibernating, nothing.

---

### Post by Martin on 2007-05-10
Are you using the main account or are you using a regular user account? If so logout and go back in as the main user - the one with sudo rights and check your power setting manager again.

---

### Post by bagbiter on 2007-05-10
I am logged on my main account..

---

### Post by Martin on 2007-05-10
Meybe check your bios and see if all the power saving devices that are typical to a laptop are turned on and therefore possibly detectable by the OS. Although if they're working under windows that won't be the problem.

---

### Post by bagbiter on 2007-05-11
I changed powermanagement software to Klaptop. It's working now. Kinda.

Machine won't wake up after hibernating. Have to reboot it manually. Any ideas?
Suspend mode works very well.

---

### Post by Martin on 2007-05-11
Hibernating and associated problems are being experienced by a lot of people - me included. I use suspend instead. Works fine, only problems are if an external usb drive is left plugged in - then it won't suspend properly sometimes.

---

