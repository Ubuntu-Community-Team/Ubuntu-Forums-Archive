---
title: "Problems logging in"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by J-me on 2007-04-16
Hello me again, 

I'm having a lil trob signing in to Ubuntu at the mow. I sign out last night to run my newsgroup reader over the night, and tried to sign back in today and it kept bring me back to the logging screen. after a number of attempts it took me to a full screen  terminal asking for user name and password, which I retyped and then I guess it gave me admin rights but I didn't know how to get the GUI back up? 

yes I made sure to type the username and password really slow making sure I got them all right and no caps was not on.

any ideas?

---

### Post by taurus on 2007-04-16
Any chance you could run out of disk space on your machine?  What does it say when you run this command from a prompt?

```
df -h
```

---

### Post by J-me on 2007-04-16
I think ur right I had left a torrent running forgot about clearing up space b4 logging out. is there any way I could get in and transfer files to my spare usb harddrive?
would that solve it, 
good work by the way I think u hit the nail on the head first time.

---

### Post by taurus on 2007-04-16
Boot into recovery mode from GRUB menu and clean out your cache.  That would buy you some space so you can log in and then delete or move whatever you want to your USB harddrive.

```
aptitude clean  <- clean out the archives
df -h  <- check for space on /
shutdown -r now   <- reboot the machine
```

---

### Post by J-me on 2007-04-16
Who needs to pay for tech support on windows when you can use Ubuntu with forums like this.
Thanks so much for the very fast replys,

---

### Post by taurus on 2007-04-16
Just wait until you get the bill!  ](*,)

---

