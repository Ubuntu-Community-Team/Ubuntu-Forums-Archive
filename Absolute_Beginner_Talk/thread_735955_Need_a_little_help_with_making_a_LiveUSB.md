---
title: "Need a little help with making a LiveUSB"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by xRW on 2008-03-26
I'm running of a LiveCD right now of Ubuntu 710 and i'm kind of stuck with some terminal commands. I'm following this guide: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I'm on step number 8 which asks me to unmount the partition but whenever I try to enter the command it says "/dev/sdb1 is not in the fstab (and you are not root)"

I cannot go any farther without unmounting so any help would be appreciated.

Note: I skipped step 6 which is also the same commands and also gave me the same message but I guess that step wasn't necessary.

---

### Post by kesman on 2008-03-26
Did you follow the step 4 correctly? You should be root during the whole procedure.

---

### Post by wormser on 2008-03-26
You need to put sudo infront of the command to get super user permissions.

```
sudo umount /dev/sd**[COLOR="Red"]x[/COLOR]**1
```

I think you are going to have to do step 7 again.  Somebody else can confirm it.

---

### Post by xRW on 2008-03-26
Whoa, didn't even notice step 4, Well i guess there's my problem. This is my very first time using Linux so bear with me. Thanks a bunch.

---

### Post by kesman on 2008-03-26
NO!
In step 4, **sudo su** you go to root's terminal and are root whole time, no need for any sudo.

EDIT: Ok, try again then =D

---

### Post by fela on 2008-03-26
there's a nice little tutorial [here]("https://help.ubuntu.com/community/Installation/FromUSBStick")

it involves using a shell script, but it's from the ubuntu website so i trusted it. it works anyway :)

---

### Post by xRW on 2008-03-26
Ok, one more thing, On step seventeen I copy and pasted that ridiculously long command but i got a totally different error message than what that tutorial was expecting:

"cp: target `/media/ubuntu710/' is not a directory: No such file or directory"

---

### Post by kesman on 2008-03-26
Did you do step 12? Removed and inserted the usb-stick back? It should mount as ubuntu710 in /media if you set the name correct.

---

### Post by xRW on 2008-03-26
Ok, i've been messing with this for quite some time now. All previous errors have been fixed (had to remove and re-insert a couple of times for it to show as ubuntu710).

My latest problem, I get "Boot Error" when I try to boot from it. That's all it says. I've tried the lilo commands as well to no avail.

---

### Post by kesman on 2008-03-26
I cannot help you with that, sorry...

---

