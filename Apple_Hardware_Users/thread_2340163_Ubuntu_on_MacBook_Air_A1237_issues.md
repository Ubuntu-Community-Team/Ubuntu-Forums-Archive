---
title: "Ubuntu on MacBook Air A1237 issues"
date: 2016-10-16
forum: Apple Hardware Users
---

### Post by brodinocaldo on 2016-10-16
Hello, I installed the LTS version of Ubuntu on this Mac, it works ok but there are some problems that I can't solve. I'm new to Ubuntu,so please try to be as clear as possible. So the problems I have are basically 2. The first is that when I fold down the screen and the Mac goes to sleep mode I won't be able to move my cursor again and I'll need to restart the computer. The second problem it's a Wi-Fi issue: sometimes when I turn on the computer I can't use wireless connectivity because I don't find any connection available. I've got one more question too... When I turn on the computer it takes me to a black screen where I can choose beetween Mac OS and Ubuntu. Is there a way to remove that screen? It's useless because if I click on Mac OS the computer crashes. Thanks to everyone who will help me :)

---

### Post by randym-axcess on 2016-10-22
> **brodinocaldo said:**
> Hello, I installed the LTS version of Ubuntu on this Mac, it works ok but there are some problems that I can't solve. I'm new to Ubuntu,so please try to be as clear as possible. So the problems I have are basically 2. The first is that when I fold down the screen and the Mac goes to sleep mode I won't be able to move my cursor again and I'll need to restart the computer. The second problem it's a Wi-Fi issue: sometimes when I turn on the computer I can't use wireless connectivity because I don't find any connection available. I've got one more question too... When I turn on the computer it takes me to a black screen where I can choose beetween Mac OS and Ubuntu. Is there a way to remove that screen? It's useless because if I click on Mac OS the computer crashes. Thanks to everyone who will help me :)

I'm new around here but, maybe I can offer some solutions to a couple of your problems; while your Mac is awake and operating in Ubuntu, go into settings and adjust settings for screen timeout and hibernation/turn off disk.

Intermittent problems that "sometimes happens" are hard to diagnose and, more than likely are not hardware problems; I would look more towards the environmental and location influences that might cause this problem.

I am not sure what options you used when you installed Ubuntu but, sounds like you may have corrupted the boot .efi(?) for the Mac OS-X; do you have any Time Machine backups to restore your Mac to a point when the OS-X worked. Is there a recovery partition that you can boot into to restore your Mac operating system?

.

---

### Post by brodinocaldo on 2016-10-24
I'm sorry I haven't been really clear. OSX works flawlessly as long as I boot it holding the "alt"/"option" key. Thanks for your answer I'll try in a couple of hours what you said :)

---

### Post by sulobanks on 2016-11-13
I recently restored one of these macbooks. It was disappointing to find out it only supports 2 versions of mac os, and only 10.6.8 is usable. I don't have solid answers, but I've at least got some direction if you're still trying to do this.

On the wifi issue, I'm finding that it works when the power adapter is plugged in, but not on battery. This seems to be a problem with the wifi power management in ubuntu. Try this:
sudo iwconfig wlan0 power off
replace 'wlan0' with whatever your wireless card is named.
See these links:
[http://seperohacker.blogspot.com/2015/09/turning-off-wifi-power-management.html](http://seperohacker.blogspot.com/2015/09/turning-off-wifi-power-management.html)
[https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/](https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/)

On the touchpad issue, it looks like the answer is to find out what driver is being used for the touchpad. Find the sleep settings (I think /etc/pm/sleep.d) and remove the driver before sleep and add it again on resume.
See this post. Not the right model, but the idea seems to be correct.
[https://ubuntuforums.org/showthread.php?t=1952532](https://ubuntuforums.org/showthread.php?t=1952532)

I plan on trying this stuff out tomorrow. I'll update with my results.

---

### Post by sulobanks on 2016-11-14
I fixed the trackpad issue with help from this thread: [https://ubuntuforums.org/showthread.php?t=1952532](https://ubuntuforums.org/showthread.php?t=1952532)
I created 99_trackpad in /etc/pm/sleep.d with the following contents:
```

#!/bin/bash
case $1 in
   hibernate)

       ;;
   suspend)

       ;;
   thaw)
       rmmod bcm5974; sleep 2; modprobe bcm5974
       ;;
   resume)
       rmmod bcm5974; sleep 2; modprobe bcm5974
       ;;
   *)
       ;;
esac

```

Adding 'sleep 2' between unloading and loading the module made it work for me. Maybe I could sleep for 1 second instead, but it worked so I didn't mess with it further. Without the sleep statement, it didn't work for me.

On the wifi front, I have mixed results. Wifi didn't work for me on first install. But after running all the updates, I reinstalled the wifi drivers with: apt install --reinstall bcmwl-kernel-source
After reboot, my wifi works. I've noticed that sometimes it doesn't. If I put the machine to sleep and wake it back up, the wifi shows up again. It's an old machine and I have a cheap aftermarket battery in it. Maybe the wireless card is going bad. Then again, I didn't have any of these problems on snow leopard. I'll probably switch to a lighter desktop. Maybe that will make a difference

Anyway, things are working for me now, at least in an acceptable enough form for me to use the machine on a regular basis.



> **sulobanks said:**
> I recently restored one of these macbooks. It was disappointing to find out it only supports 2 versions of mac os, and only 10.6.8 is usable. I don't have solid answers, but I've at least got some direction if you're still trying to do this.

On the wifi issue, I'm finding that it works when the power adapter is plugged in, but not on battery. This seems to be a problem with the wifi power management in ubuntu. Try this:
sudo iwconfig wlan0 power off
replace 'wlan0' with whatever your wireless card is named.
See these links:
[http://seperohacker.blogspot.com/2015/09/turning-off-wifi-power-management.html](http://seperohacker.blogspot.com/2015/09/turning-off-wifi-power-management.html)
[https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/](https://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/)

On the touchpad issue, it looks like the answer is to find out what driver is being used for the touchpad. Find the sleep settings (I think /etc/pm/sleep.d) and remove the driver before sleep and add it again on resume.
See this post. Not the right model, but the idea seems to be correct.
[https://ubuntuforums.org/showthread.php?t=1952532](https://ubuntuforums.org/showthread.php?t=1952532)

I plan on trying this stuff out tomorrow. I'll update with my results.

---

