---
title: "[SOLVED] added and external usb hard drive"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-11-08
i added an external usb hard drive ntfs i was copying songs to a friends hard drive i kicked out the plug when i plugged it back in it is all locked no permissions read only???????

---

### Post by tyfius on 2007-11-08
I think there was a command to unlock them. Try mounting them manually and see if that produces any valid output.

If you have the possibility, just boot into Windows and open and close the drives on Windows. This should also fix the issue when you boot into Ubuntu again.

---

### Post by DarinB on 2007-11-08
i tried and it would be seen by the windows box 
i re formatted it and got the same problem then i found 
this on the forums 
this helped
sudo chown -R yourusername /media/disk/
it is now copying the music and i will see if it will transfer to the windows box.
thanks everybody
D

---

### Post by DarinB on 2007-11-08
sorry can't type it was not seen by the windows box that is why i re formatted it.
it still came up no permissions.
then i tried the chown
i don't know why when it unplugged by mistake it all locked up
and lost permissions.
any ideas why????
i am trying to learn this stuff

---

### Post by skymera on 2007-11-08
try

sudo mount -a

---

