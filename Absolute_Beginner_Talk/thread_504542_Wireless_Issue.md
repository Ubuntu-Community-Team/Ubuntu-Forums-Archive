---
title: "Wireless Issue"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-19
Well, after 4 days of tackling my wireless problems I finally had a breakthrough last night! I run a 64-bit system and someone mentioned in a post that the following command would work:


sudo apt-get install bcm43xx-fwcutter
then
sudo modprobe bcm43xx

sure enough after I ran it I opened my wireless assistant and it kicked right on and connected me to the internet and it was freaking fast as hell which made me happy as well.

So I played around installing some things and enjoying the non-wired glory of kubuntu. I had to restart my computer to get firefox to appear, so I restarted and after booting up again when I opened wireless assistant it was offline again and not finding my wireless card. I re-ran the command above and again it worked...

long story short, when I logged on this morning, I ran the command again but now it finds the access points but wont connect.

So 2 questions:

1. Is there a way to set my konsole to automatically run those commands when I log in?
2. Any Ideas as to why it is not connecting to the access points now?
__________________

---

### Post by Frak on 2007-07-19
[https://help.ubuntu.com/community/AddingProgramToSessionStartup?highlight=%28startup%29](https://help.ubuntu.com/community/AddingProgramToSessionStartup?highlight=%28startup%29)

---

### Post by ukulele_ninja on 2007-07-19
Apparently if im plugged in via ethernet and run the commands it will work....how do i make it work without doing this?

---

### Post by Frak on 2007-07-19
Open KWrite or Kate
```
#!/bin/bash
sudo modprobe bcm43xx

exit
```
Save it as **wifi** to your ~/ (home) directory.
Then run
```
sudo chmod +x ~/wifi
```
When you boot up, run
```
sudo ./wifi
```
tell me if it doesn't work

---

### Post by ukulele_ninja on 2007-07-19
worked like a charm! Thank you so much! :guitar::guitar:

---

### Post by Frak on 2007-07-19
Oh just so you know
```
sudo apt-get install bcm43xx-fwcutter
```
Tells Ubuntu to go to the internet and reinstall the driver, just running **modprobe** would have done it, but I instead decided to give you an easier to remember bash script.
:guitar:

---

### Post by kevdog on 2007-07-19
Im glad your solution worked, however probably the real reason you even have to run this script is because the module is blacklisted at boot.

gksu gedit /etc/modprobe.d/blacklist

Look for a line that states ```
blacklist bcm43xx
```.  Put a # sign in front of it.  You will probably be able then to reboot  are your wireless startup automatically without the use of a script.

---

