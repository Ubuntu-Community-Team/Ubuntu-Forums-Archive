---
title: "Lost NetworkManager, now lost internet"
date: 2009-09-15
forum: Apple Hardware Users
---

### Post by Chris Grk-O-Matic on 2009-09-15
I lost network manager in my task bar, and attempting to fix the problem, it seems I lost any network connection altogether. 
I followed someone's advice on a forum and he said to go to Synaptic Manager and uninstall network-manager and reinstall it. Well once I uninstalled it, it unknowingly killed my internet connection.

I tried sudo apt-get install network-manager and no luck because my laptop just can't get on a network now.

I'm assuming I can use my live-cd to get the right software??

Can somebody offer some advice? The more detailed the better [as I am still learning to use linux].



1Ghz Titanium Powerbook
Ubuntu 9.04


Kind regards,
Chris

---

### Post by Yannick Le Saint kyncani on 2009-09-15
sudo dhclient eth0

If you're using a wired connection.

---

### Post by Chris Grk-O-Matic on 2009-09-15
WOW... that's all I have to say... WOW

I don't know what it did, but it worked. I will look into it after I watch X-Men Origins.


Thank you for that quick response!


Best,
Chris

---

### Post by Yannick Le Saint kyncani on 2009-09-15
And reinstall network-manager of course.

---

