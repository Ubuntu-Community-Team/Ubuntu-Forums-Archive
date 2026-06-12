---
title: "networking (wifi) password not saved"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by raspberryh on 2006-08-23
Hi,
When I go to System -> Administration -> Networking, and I click on "Location" and create a new location (in this case, "Home"), then I go to Properties and select the wireless network that I want to associate with "Home", and I type in the password. Then, if I go somewhere else, like to school, where I don't need a password, I create a new location (in this case, "UCF"), and then I go to Properties, and I select the wireless network that I want to associate with that account... And the password field contains the password for the previous network that I connected to - so I clear it out, since this one doesn't need a password. Then I connect.
Then, next time I am at home, I go to Networking again, and I select the location "Home"... And when I go to Properties, the password is gone! And the wireless network that I had selected for UCF is still selected.
Now what I am wondering is... Does Ubuntu not save the password for wireless networks? And what is the point of having locations if it doesn't save unique information for each location? Am I doing something wrong?
Thanks,
Heather

---

### Post by Metacarpal on 2006-08-25
Hmm.  I'm not sure why the networking config is doing that.  I do know one potential fix, however.  There is a package in the repos called Wifi Radar that you can use to create profiles for individual wireless connections, and it does save settings, passwords, WEP keys, etc.  You can find it in Synaptic.

---

### Post by raspberryh on 2006-08-25
I will try that. Thanks so much!

---

### Post by steve.horsley on 2006-08-25
I've had that trouble. I came to the conclusion that you have to set up the networking how you like it, and **then** create the location, at which point it stores the current settings under that name.

---

### Post by raspberryh on 2006-09-07
> **steve.horsley said:**
> I've had that trouble. I came to the conclusion that you have to set up the networking how you like it, and **then** create the location, at which point it stores the current settings under that name.

I tried this, and it worked!!! Thanks a ton!! :KS

---

