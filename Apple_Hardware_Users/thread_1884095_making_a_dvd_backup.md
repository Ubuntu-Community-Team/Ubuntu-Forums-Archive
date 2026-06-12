---
title: "making a dvd backup"
date: 2011-11-20
forum: Apple Hardware Users
---

### Post by illprime on 2011-11-20
So, I just got this new mac book and i want to install ubuntu on it, but i dont want to lose any of the data thats on the laptop. is there a way that i can compress whats currently on the hard drive and save it in a partition when i install ubuntu. My end goal is to have a majority of the hard drive available to me once i install ubuntu.

---

### Post by happywing on 2012-08-14
What model is that?

__________________
[A+ BBB]("http://lepkeautotrans.com")

---

### Post by pierpier on 2012-08-16
> **illprime said:**
> So, I just got this new mac book and i want to install ubuntu on it, but i dont want to lose any of the data thats on the laptop. is there a way that i can compress whats currently on the hard drive and save it in a partition when i install ubuntu. My end goal is to have a majority of the hard drive available to me once i install ubuntu.

Hi,

Yes, the easiest way is enter in \Application\Disk Utility\ then select your OS partition and click on the top on "New Image", macbook will create an ISO file that will allow you to restore your system and all your data, since the file will be big, i suggest you to save it on an external hard drive.

Then you can run linux using a live version (via usb or DVD) and delete the partions using Gparted application, then reinstall OS X 10.5 - 10.6  - 10.7 using the installation DVD and create 1 partition for it and leave free space to install Ubuntu later.

Once OS x is installed you can restore your previous pc using the iso file created before (enter in disk utility and click on restore - select the partition and the path of iso file, it will require about 20-30 minutes).

I wish it's helpful for you, don't hesitate to reply me or to send me a private message ;)
Cheers,
Pier

---

