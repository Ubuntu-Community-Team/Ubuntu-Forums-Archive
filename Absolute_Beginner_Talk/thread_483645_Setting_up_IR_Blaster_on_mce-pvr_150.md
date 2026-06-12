---
title: "Setting up IR Blaster on mce-pvr 150"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Shawger Lager on 2007-06-25
Hi, I have been setting up Mythtv on my Ubuntu 7.04 machine and I am having some problems getting the IR blaster working. I have following a Lirc howto found [here]("https://help.ubuntu.com/community/Install_Lirc_Feisty").
The part I seem to be stuck on is where it says the usage for the MCEUSB2 is the same as serial transmitters. 
Then I follow the serial transmitters part and it doesn't work. Any help in getting this going would be appreciated.
Thanks

---

### Post by BillDozer on 2007-06-25
I have the same problem. I have remote working in mythtv, but when I try to send something to the blaster I get the following message:
```
irsend: timeout
```
And after that the remote stops responding, I have to restart lirc and mythtv before mythtv responds to the remote again.

---

### Post by Shawger Lager on 2007-06-25
Yup, thats about the same thing I am getting. I guess what i am confused about is that I seem to be missing something. I thought doing this would somehow involve telling the blaster what frequencies were needed to change channels.

---

### Post by rogerh on 2007-07-18
Post back if you are still having problems with this. 

I've just set up a mythtv mceusb2 remote + blaster for a satellite box in lirc and it seems to mostly work OK - am still having trouble preventing lirc from acting on the IR signals it gets from the real remote the blaster is emulating.

The main thing seems to be to remember to disable the inbuilt serial port:
sudo setserial /dev/ttyS0 uart none

---

### Post by BillDozer on 2007-08-06
Found out that the community documentation for the blaster part was not working for me. After I downloaded another remote than using the one specified in the documentation it worked ok. See other [thread]("http://ubuntuforums.org/showthread.php?t=483828")

---

### Post by Abishye on 2007-11-11
> **rogerh said:**
> Post back if you are still having problems with this. 

I've just set up a mythtv mceusb2 remote + blaster for a satellite box in lirc and it seems to mostly work OK - am still having trouble preventing lirc from acting on the IR signals it gets from the real remote the blaster is emulating.

The main thing seems to be to remember to disable the inbuilt serial port:
sudo setserial /dev/ttyS0 uart none

Hi there rogerh, you didn't happen to document what you did to get this to work did you?  I have my lirc recognizing input from the remote but I'm confused after reading so many different ways to configure the blaster part.

I have Ubuntu 7.10 + Mythbuntu installed on top of it.  I can watch live TV fine.  I can change channels on the satellite STB and it comes through ok to MythTV.  I'm using a single PVR-150 with a silver USB Windows Media Center remote plus there's 2 ports on the IR receiver for a blaster.  Looks like I have a very similar setup to yours.

---

