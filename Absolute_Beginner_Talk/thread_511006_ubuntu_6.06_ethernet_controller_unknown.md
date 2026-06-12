---
title: "ubuntu 6.06 ethernet controller unknown"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by bungee_hamster on 2007-07-27
Greetings all!
apologies if this question is answered elsewhere but have searched this forum in vain so far.
I am a complete newbie but enjoying a taste of freedom from You-know-who, but having trouble getting my internet connection working:
adsl modem connected to pc via ethernet
NVIDIA MCP51 ethernet controller
I tried lspci-v  and got a message saying forcedeth probe of 0000:00:14.0 failed with error -22.

when I look at the info under 'devices' it lists the ethernet controller but says it's an unknown device 0269.
I have seen in other threads a mixture of responses about support provided/not provided for NVIDIA MCP51. I've installed 6.06lts ubuntu.
all help gratefully received!

---

### Post by bungee_hamster on 2007-07-27
further info:
I typed:  sudo ifconfig and got:

lo       link encap:local Loopback
         inet addre:127.0.0.1 mask 255.0.0.0
         inet6 adre::1/128 scope:host
         UP loopback running MTU16436 metric:1
        

also, typed: dmesg and got (amongst other things):
PCI: setting latency timer of device 0000:00:14.0
forcedeth: couldn't find register window for device
ACPI:PCI interrupt for device 0000:00:14.0 disable
forcedeth probe of 0000:00:14.0 failed with error -22

don't know if this sheds any more light on the problem?
thanks!

---

### Post by deadgobby on 2007-07-27
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by bungee_hamster on 2007-07-27
thank you deadgobby, but I started there & followed all the instructions - pity they don't tell me what to do if there is no ethernet controller found!

---

### Post by deadgobby on 2007-07-27
Please open up the terminal and type in this command

lspci -v 


 This will give list of your HW. Please copy and paste the reply from the terminal and go from there. I hope some one can help you after I log off. Need to get some sleep. 3rd shift can be so much fun. Oh if you wan to and you do not mind start from scratch. I wound if you install Fiesty Fawn or 7.04 wo;; cure this.
Gobby

---

### Post by bungee_hamster on 2007-07-27
please see first post - only listed what seemed to be the relevent line! the pc i'm working on is downstairs and I'll have to write down everything if what i put in the first post is insufficient!

---

### Post by bungee_hamster on 2007-07-27
problem solved by installing version 7.04 - thanks !!

---

