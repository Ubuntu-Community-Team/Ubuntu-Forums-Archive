---
title: "Mount Time Capsule on Ubuntu 16.04"
date: 2016-08-07
forum: Apple Hardware Users
---

### Post by ashkanrafiee on 2016-08-07
Hi All,
I have been an Apple user for a long time which I decided to move on :) However, I have backed up all my files on a Time Capsule (I used simple rsync command, so the files can be easily accessible).
I followed instructions on mounting Time Capsule but I just cannot mount the drive. I am directly connecting the Time Capsule to my desktop running Ubuntu 16.04.

I would highly appreciate any advice.

Cheers
Ashkan

---

### Post by senorpony on 2016-08-25
Figured it out after several weeks of effort! I used this as a starting point, but couldn't get the script to work: [https://ineed.coffee/418/how-to-automatically-mount-and-umount-apple-time-capsule-on-linux/](https://ineed.coffee/418/how-to-automatically-mount-and-umount-apple-time-capsule-on-linux/) 

**Here's the code to mount:**
sudo mount.cifs //IPV4ADDRESS/Data ~/MOUNTFOLDER -o password=YOURPASSWORD,sec=ntlm,uid=USERNAME THIS IS ON YOUR TERMINAL

*for example:*
sudo mount.cifs //10.0.0.3/Data ~/TimeCapsuleMount -o password=Password123,sec=ntlm,uid=senorpony

*Breaking this down... *
sudo takes action, you mount.cifs; 
you enter the IP address (it isn't the router address but the IPv4 address (you can find this in AirPort Utility);
 "/Data" is how the volume is structured in the hard disk of the Time Capsule... although you need to see if your version differs;
~/MOUNTFOLDER is any location you want--I decided to put it in my home folder under TimeCapsule Mount (the ~ gets you to home);
password is the password you use to connect to the Time Capsule;
not sure what sec is;
uid connects to the local user profile

**Unmounting**:
From what other users say, you should unmount before shutting down. I guess this is not to do a hard disconnect?

*here's the code:*
sudo umount ~/TimeCapsuleMount

again sudo to take an action;
read carefully as it isn't UNmount, it is umount;
then the next piece is the mounting point

Good luck!

---

