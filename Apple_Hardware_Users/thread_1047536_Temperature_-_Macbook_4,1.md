---
title: "Temperature - Macbook 4,1"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by darren1408 on 2009-01-22
Hi,

I am new to Linux and have Ubuntu 8.10 running on my Macbook 4,1.

It seems to get quite hot.

How do you install Apple SMC?

Is there anyway I can check to see if it is working and Is there a utility to check these parameters?

Thank you for your help in advance.

Darren.

---

### Post by cyberdork33 on 2009-01-22
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by darren1408 on 2009-01-22
Hi,

Thank you for your reply.

I have installed Apple SMC.

Is there anyway to check its been correctly installed?

Also can I check to see if the fan speeds etc are OK?

Thank you again.:D

Darren.

---

### Post by albesan on 2009-01-23
hey.

Not an expert but dealing with the same issue. I'm on a white macbook 4.1 running intrepid and the following worked for me. Use at your own risk.
I am supplying as many references as I can find right now. 

You can install lm-sensors if you haven't done so yet:

sudo apt-get lm-sensors

Then from the terminal run the program with:

sensors

The output of sensors on my machine right now is:

albesan@copituxredux:~$ sensors
applesmc-isa-0300
Adapter: ISA adapter
[COLOR="Red"]Exhaust  :  2999 RPM  (min = 3000 RPM)[/COLOR]
temp1:       +30.5°C                                    
temp2:       +44.8°C                                    
temp3:       +43.0°C                                    
temp4:       +49.8°C                                    
temp5:       +43.0°C                                    
temp6:       +65.0°C                                    
temp7:       +63.5°C                                    
temp8:       +42.8°C                                    
temp9:       +42.5°C                                    
temp10:      +42.5°C   

There I can see that applesmc is running and that my minimum fan speed is set to 3000 RPM.


Acording to mario, post number 4 on the link below, as long as your fans are not set to manual you should be fine applesmc should control the fans when required see :

[http://ubuntuforums.org/showthread.php?t=981280](http://ubuntuforums.org/showthread.php?t=981280)

Check the output of this command on the terminal:

cat /sys/devices/platform/applesmc.768/fan1_manual

if the output of the command is 0 , then the fans are set to automatic.
if the output of the command is 1 , then they are set to manual.

If you want to change the minimum speed of the fan so the computer runs cooler (using more power shortening your battery's autonomy) you can change by running this command:

echo 3000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min

This will set your minimum speed to 3000.

To make the changes stay and not to re-run the commands on reboot I read on a thread I can't find right now that you'll need to add the line:

echo 3000 > /sys/devices/platform/applesmc.768/fan1_min

to the file /etc/rc.local , (sudo gedit /etc/rc.local)
before the line containing "exit"


Hope this is useful 

a.

---

### Post by frikker on 2009-09-23
Thanks for the heads up about this! I am going to write a simple python / matplotlib poller to graph temp over time.

Any ideas which sensor is what hardware?

---

