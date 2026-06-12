---
title: "Super Nubie--Need Help with the wireless..."
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by nuubuntu on 2006-02-07
I have an emachines M6809 with a broadcom wifi card built in. I just installed Ubuntu on it and it is awesome. Everything seems good so far, but I am really having a hard time installing the wifi device. I followed a bunch of other threads on the Ubuntu forums, and still can't get it to work. Can anybody help me work through this thoroughly. For example, what is the procedure to get it seen. Also, I used Synaptics to install ndiswrapper. It is there and when I use the wireless utility, it shows that there is a hardware device.

[ATTACH]5940[/ATTACH]

Thanks.

---

### Post by bscbrit on 2006-02-07
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

The best thing that you can do is to start following the guide in the link above until you hit a brick wall and then come back to this forum with a specific problem.  There will be plenty of help but, at this stage, all anyone can do is to instruct you to do what is in the guide, one line at a time. That would not be terribly efficient for you and prevents your helper from providing much assistance to anyone else.

Give it a try and ask for help when you get stuck.

---

### Post by rawkasaurus on 2006-02-07
Truthfully, I have that same driver on my laptop and after numerous attempts at getting it to work with [ndiswrapper]("http://ndiswrapper.sourceforge.net/"), I gave up.  I ended up trying out a free month trial of [linuxant]("http://www.linuxant.com/company/") and that worked perfectly, but it's something like $15 to buy it.

I'd say either get linuxant or get a cheap pcmcia wireless card.

---

### Post by bscbrit on 2006-02-07
I have the 'a' version working on my system, are you sure that you have installed the correct driver according to the WifiSetup guide?

---

### Post by nuubuntu on 2006-02-07
Thank you bscbrit and rawkasaurus for the help. I will look into it immediately. \\:D/

---

### Post by nuubuntu on 2006-02-07
I think I almost got it. The drivers are installed and it seems ok, but the light on laptop that shows that the wireless card is on, is turned off. And usually, in windows, I have to press Fn+F2 to turn it on, and in Ubuntu, it isn't responding. Is there any way to enable it?

---

### Post by d1337 on 2006-02-07
Try, in a terminal

sudo modprobe ndiswrapper

and see if that'll kick it on.  Also, you may need to open System--> Admin--> Network Setting and insure that it is listed as active.  When I first got mine going on m eMachine M6805, I had to deactivate the Ethernet connection.

d1337

edit: [http://www.ubuntuforums.org/showthread.php?t=69382](http://www.ubuntuforums.org/showthread.php?t=69382) is a thread I started and worked through everything.  Maybe some helful hints and links...maybe not.  But it will work with ndiswrapper.

---

### Post by Danni on 2006-02-07
If those work, then here's a command that's very helpful:

sudo ndiswrapper -m

It ensures that your wireless comes on at startup if it doesn't automatically (which took me 2 days to get working :P)

---

### Post by nuubuntu on 2006-02-07
I have tried all the above, and when I do that, i get this.

user@ubuntu:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

user@ubuntu:~$

I honestly have no clue were to go from here. It seems that the driver is working.

This is some of the info associated with it when i enter:

user@ubuntu:~$ sudo gedit sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5a/*.conf


NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|Broadcom,06/26/2004, 3.70.17.0

antdiv|-1
BadFramePreempt|0
BTCoexist|0
ccx_rm|1
ccx_rm_limit|300
Channel|11
Country|
EnableAutoConnect|0
EnableLeap|0
EnableSoftAP|0
frag|2346
FrameBursting|0
gpio0|-1
gpio1|-1
gpio2|-1
gpio3|-1
Interference_Mode|3
NetworkAddress|
NetworkType|-1
PLCPHeader|0
PowerSaveMode|0
PwrOut|100
RadioState|0
Rate|0
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
SSID|
WEP|

Thank you all for the help.

---

### Post by nuubuntu on 2006-02-07
Ok, I think I messed up the installation by changing all the RadioState's by hand, according to another thread, and when I changed it to 1, that seemed to turn the module off. I am currently reinstalling the OS. I really appreciate everybody's help. I am very lost when it comes to Linux commands. I was a total windows user, and all I know is the cmd prompt, ms-dos,  commands, and pressing ok many times.

---

### Post by d1337 on 2006-02-07
You probably don't need to do a reinstall.  Your screenshot looks like a pretty fresh install anyway, doubting that you've changed much.  If you give me a few minutes, I'll get out my laptop and see if I can help you out.

d1337

---

### Post by HokeyFry on 2006-02-07
once you finish reinstalling ubuntu, follow the directions in this thread

[http://www.ubuntuforums.org/showthread.php?t=112526]("http://www.ubuntuforums.org/showthread.php?t=112526")

---

### Post by nuubuntu on 2006-02-07
Here is an interesting thing. I installed the drivers, and everything seemed ok. Now, when I do lspci, to see if it is there, this is what I get:

0000:00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Askey Computer Corp.: Unknown device 7050
        Flags: fast devsel, IRQ 9
        Memory at d0000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

If this means something to someone, I could sure use the help. I have been at this thing for two days now. More than eight hours spent doing this. Again, thanks to everyone.;)

---

### Post by nuubuntu on 2006-02-07
[QUOTE=d1337]You probably don't need to do a reinstall.  Your screenshot looks like a pretty fresh install anyway, doubting that you've changed much.  If you give me a few minutes, I'll get out my laptop and see if I can help you out.

d1337[/QUOTE]

Thanks d1337, your help is much appreciated.

---

### Post by d1337 on 2006-02-07
Sorry, I took the delayed response as a sign that you were done for awhile or doing a reinstall.  So, now, did you reinstall Ubuntu?  Can you provide a link to the howto that you have followed to this point so that we can have a closer look?

d1337

---

### Post by nuubuntu on 2006-02-07
yes, here is the link, 

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=m6805+emachines+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=m6805+emachines+ndiswrapper)

---

### Post by nuubuntu on 2006-02-07
It is exactly the same .inf/device driver file that I used.

---

### Post by d1337 on 2006-02-08
Did all of the steps from that link complete without issue?  Step 3 gave me grief the first two times that I tried to get this going.  In both instances, I started again at step 3 and it completed fine.  My guess is that I wasn't able to key it correctly.  I am assuming that you did reboot your PC (as opposed to just restarting /etc/init.d/networking).  Have you added any additional software packages such as wifi-radar?  As much as a hassle it may seem, and maybe you've already done this, taking a breather to lessen your frustrations and following step-by-step once more may do the trick.  Your lspci does look a bit off, mine doesn't have the subsytem/flag etc...but the device is definately there and recognized.  Did you have your ethernet cable connected while you went through these steps (I disconnected after getting the packages)?  Are you dual-booting and, if so, is the card functioning correctly on the other side?  I apologize that I maybe wasn't much help, when I saw this thread a couple hours ago I thought I'd be able to get you fixed right up. As it stands, I've gotta get to work rather early in the morning...but I will check back in then.

d1337

---

### Post by nuubuntu on 2006-02-08
Thank you for all your help. I will try again tomorrow. I am going to take a little breather from it.

---

### Post by nuubuntu on 2006-02-08
Stil, today, it is not working. I tried multiple times, and still nothing. I am starting to believe that there is a problem with the bios. I read some recent posting about the emachines M6809 and they are not going to release any BIOS updates. They feel that the one that it shipped with is just fine. I will continue my quest to make this happen. I thank you all for your generous help, and if anyone gets an idea about how to make it work, let me know. Thanks.

:-|

---

### Post by nuubuntu on 2006-02-08
I got this far, so if anyone has any answers to this please feel free to post, please.


dragan@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
dragan@ubuntu:~$ for confile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $confile | sed -e 's/RadioState|1/RadioState|0' > $confile; done
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
dragan@ubuntu:~$ sudo ndiswrapper -d 14E4:4318:1028:0005.5.conf bcmwl5 Driver 'bcmwl5' is used for '14E4:4318:1028:0005.5.CONF'
dragan@ubuntu:~$ sudo ndiswrapper -m modprobe config already contains alias directive

dragan@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
dragan@ubuntu:~$ sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper > $confile
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
dragan@ubuntu:~$ sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper > :confused: $confile
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
dragan@ubuntu:~$

---

### Post by d1337 on 2006-02-08
The bios update, from what I know, has more to do with acpi and the keyboard freaking out the kernel for some reason.  When you started today, did you start from the very beginning of the how-to that you are using?  It makes certain that you have cleared any prior conf files etc so that you are getting a nearly new start

I asked last night, but don't think I really got an answer, is this a dual boot machine?  If so, does the wireless work on the other side?
```

dragan@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
{ -e file [...] | -i | -s | <command> }
```not sure what you were trying to do there.  To hold sudo status after logging in, try "sudo su"...if that's what you were trying to do.  In fact, from your "Permission Denied" errors...that may be just what you need to do.
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```
When you key/copy the above three lines from the howto by jonny, do each line separately and hit enter after each line.  I don't think that these need to run into each other...but it has been a couple months since I've done this.

d1337

---

### Post by adi-beg on 2006-02-09
Look at /usr/share/doc/ndiswrapper-utils/README.Debian

Maybe it will help.

---

### Post by nuubuntu on 2006-02-09
It is strictly a Linux Machine. So, no dual boot. I wanted to make it just that so I can use it just like I would a Windows machine. Learning things as I go. Also, I had done that "script" just like you said. One by one, pressing enter after each line. But now I got this with the permission denied stuff. Thanks.

adi-beg: I tried doing that and it says permission denied.

---

