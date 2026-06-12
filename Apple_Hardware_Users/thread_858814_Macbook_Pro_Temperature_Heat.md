---
title: "Macbook Pro Temperature Heat"
date: 2008-07-13
forum: Apple Hardware Users
---

### Post by blunt.dualboot on 2008-07-13
Hi All,

I am new here. New to Mac and new to Linux. 

I purchased Mac Book Pro 15, dual core 2.4GHz 2 weeks ago. It's 4th Generation. I am dual booting with OS X, Leopard and Ubuntu Hardy Heron (64 Bit).

My macbook pro is very hot (in temperature) ;) when I am on Ubuntu. Temperature is OK when I am on Leopard. 

Not sure if it's harddisk or CPU. But it is really hot.

I am worry it gonna shorten the life span.

My questions are
Is it Normal?
If not, how should I fix it?

Any pointer or suggestion would be appreciated. 

Thanks Folks!

Dualboot

P.S. This is my first Mac and I am loving it. :)

---

### Post by hajk on 2008-07-14
High temperature on the 4,1 15" MBP normal? No, this is not normal with an up-to-date OS like Ubuntu 8.04. My own experience with this very same model is just the reverse: it runs decidedly cool, even compared with running under Mac OS X Leopard -- an experience with both Ubuntu 8.04 and Debian testing (Lenny).

From my own installation notes of Debian Lenny:> 
CPU frequency scaling works out-of-the-box, with both processors in *ondemand* mode usually ambling along at 800MHz, down from a rated 2.4GHz. The MBP stays noticeably cool under this regime, with the fans barely audible. 

The temperature of the SATA HD can be monitored through the "hddtemp" package, which should be installed with the default parameters. Processor temperature is monitored with the "coretemp" kernel module, which can be loaded by adding the following lines to /etc/rc.local,```

modprobe coretemp
sensors -s
```
and by installing the "lm-sensors" and "sensors-applet" packages. This last package allows a Hardware Sensors Monitor to be added to the lower menu bar. Make sure to enable "hddtemp" for /dev/sda using its references menu. Rebooting now shows icons for HD and CPU temperatures.

Finally, the "acpid" package allows the *acpi -V* command to display battery information plus the state of the cooling fans on a scale from 0--10, with the lowest value of 0 indicating idling at around 2000rpm.
So, you should make sure that these packages are also installed on your MBP, so that you can monitor what's going on. It is, for example, possible to manually set your fans to a higher idling rpm, if need be.

---

### Post by blunt.dualboot on 2008-07-14
Thanks hajk,

Yes, Mine is 4,1 15" MBP and temperature is much hotter than on Leopard.

My installation of Hardy Heron is plain default. I did not added any library nor package for CPU or HDD temperature controls.

I am dual booting using rEFIt. Added some drivers by following instruction from [[COLOR="DarkRed"]this wiki[/COLOR]]("https://wiki.ubuntu.com/MacBookPro/Penryn"). Not sure if those factors would make a difference. 

I will try out with the tools you suggested when I get back home. Hope I can find out something about the issue. 

Thanks for your informative reply.

P.S. And to everybody, my sincere apology if my postings are lame. I am pretty much newbie on both Mac and Linux. :)

---

### Post by cyberdork33 on 2008-07-15
This might be helpful to you too:
[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

A lot of people complain about heat issues in Ubuntu on Macs. You are not the only one.

---

### Post by kosumi68 on 2008-07-15
Hardy comes default with firefox 3, which does a lot of web loading in the background. I re-installed firefox 2, went into the special url

```

about:config

```

and switched off the network.prefetch-next parameter. Much less activity, much less heat.

---

### Post by blunt.dualboot on 2008-07-16
Hi Folks, 

Thanks for your kind replies. cyberdork33 comforts me that I am not alone. ;)

Well to get to business, I installed HDD, CPU temperature sensor and applets as hajk suggested. I can get HDD sensor working. But I can get CPU temperature on sensors.

On applet sensor list, I can only see HDD. I edited /etc/rc.local as in instruction.

my rc.local looks like following. 
> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe coretemp
sensors -s
exit 0


Anything wrong there?

Oh and my HDD temperature is [COLOR="DarkRed"][SIZE="4"]44 C[/SIZE][/COLOR]. is it too hot?

Thanks folks,

Dualboot

---

### Post by Brightbelt on 2008-07-16
Does anybody know if this works? It's from Oscar's thread ("Goodbye My Fellows"), in which the same issue is also addressed:

> 
1. Install Powersaved
2. sudo gedit /etc/init.d/rc
3. Change then Concurrency=none for Concurrency=shell

It runs much better, but the video output....grrr..can't get it right, after installing with envyg i've got the white screen.... and can't make it work....


---

### Post by blunt.dualboot on 2008-07-16
I was reading that thread too.

Not sure if it works. I am pretty much of newbie I do not have any idea what those commands means. :) Anyway I will give it a try tomorrow. It's 2:30 am here. :(

As for now...

My CPU is running at 800 Mhz, sometimes jumps to 240 when web server (Apache, Tomcat) process the request or when I open new window.

HDD is still 44 C. I have been running for 5 hours. After 2nd hours, it feel little bit uncomfortable resting wrist it because of the heat.

Not sure if this would help.

Well other variables here are I am in Singapore(which is tropical), I was using it in my living room(no air condition). I could feel the heat even when I was typing. 

hajk is using same model as mine and his/her seems to be fine.

I hope I can get heat little bit lower. :)

I will try in air conditioned room tomorrow. 

Please let me know if you have any suggestions or comment.

Night,

Dualboot

---

### Post by Brightbelt on 2008-07-16
Hi Blunt, 
  I understand the newbie thing... But that sequence Oscar put out is very, very easy once you understand how it works. 

First remember to install 'powersaved' in the Synaptic Package Manager. Do a search there to find it, then install it. 

After that, just open a terminal and type this command:

```
sudo gedit /etc/init.d/rc
```

What that basically means is that you're making a request to edit a file called '/etc/init.d/rc'

Once you do that code, it may take a second, but a new window will come up showing the actual contents of that file. 

Near the top of the file, you'll see a line that says:

> concurrency=none

There, just use your cursor and change "none" to the word "shell"
and save the file. And that's it !!

---

### Post by cyberdork33 on 2008-07-16
> **blunt.dualboot said:**
> Oh and my HDD temperature is [COLOR=DarkRed][SIZE=4]44 C[/SIZE][/COLOR]. is it too hot?
no that is fine, maybe a bit warm. I usually shoot for the 30s myself but 44 is nothing to complain about really.

Though the concurrency thing can make your system a bit snappier, IDK that it will keep the machine cooler. 

powersaved, on the other hand, is a CPU prequency scaling daemon (I think) which would help conserve power and keep things cooler.

---

### Post by Oscar Pradilla on 2008-07-16
That was the coolest config i got..

Try.... if you don't like it, uninstall it and return to your old config...that's all

---

### Post by blunt.dualboot on 2008-07-16
Thanks for the replies folks.

I still got question, How do I get to see CPU temperature. I did according to hajk advise. 

But I can only see CPU Frequency and HDD Temperature. I can't get CPU temperature.

Can someone help me out?

Thanks.

---

### Post by cyberdork33 on 2008-07-17
> **blunt.dualboot said:**
> I still got question, How do I get to see CPU temperature. I did according to hajk advise. 
Use coretemp

---

### Post by blunt.dualboot on 2008-07-17
Hi,

I tried 

```
sudo modprobe coretemp
```

and got the following error. :(
```

FATAL: Error inserting coretemp (/lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/coretemp.ko): No such device
```

I did some googling and found this thread.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119")

saying coretemp module is not installed in Hardy Heron?

Is my understanding correct? 

If so, how do I include coretemp?

Thanks.

---

### Post by blunt.dualboot on 2008-07-17
Oh,

One more question, Any one using Mac Book Air? How is the temperature? A friend of mine is planning to get one and thinking of dualbooting too.

:)

---

### Post by cyberdork33 on 2008-07-17
Did you install coretemp first? I think it is part of the lm-sensors package.

> **blunt.dualboot said:**
> One more question, Any one using Mac Book Air? How is the temperature? A friend of mine is planning to get one and thinking of dualbooting too.
There is a user named [Brightbelt]("http://ubuntuforums.org/member.php?u=293615"). He uses an MBA. There is also a wiki page:
[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

---

### Post by kosumi68 on 2008-07-17
blunt, with a bit of tweaking the temperature is not a problem. There are many recent posts regarding macbook pro, the problems are very similar. However, the lm-sensor set for MBA is not updated (on its way), so I stick with powernowd and conservative settings, rather than using powersaved.

---

### Post by blunt.dualboot on 2008-07-17
> **cyberdork33 said:**
> Did you install coretemp first? I think it is part of the lm-sensors package.


There is a user named [Brightbelt]("http://ubuntuforums.org/member.php?u=293615"). He uses an MBA. There is also a wiki page:
[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

Hi Cyber Dork,

I just did the apt-get for lm-sensors. then added in two lines in rc.local.

CPU monitor is not showing, so i did some searching and tried executing the command 

sudo modprobe coretemp and it throws an error.

:(

P.S. To all, Even I am pretty much lost in using Ubuntu, Mac and OS X, it rather fun. I really appreciate the community help and you guys here for your patients and supports so far.

You guys rock!

---

### Post by blunt.dualboot on 2008-07-17
Kosumi?

> , so I stick with powernowd and conservative settings rather than using powersaved.

Can you explain more? How do one use powersaved? How do one use powernowd and conservative settings? 

:P

---

### Post by kosumi68 on 2008-07-18
> **blunt.dualboot said:**
> Kosumi?



Can you explain more? How do one use powersaved? How do one use powernowd and conservative settings? 

:P

I believe I mistook your system (Macbook Pro) for a Macbook Air. Thus, my comments do not really apply, as the MBP seems to work fine according to the many recent posts on the subject.

---

### Post by V_incent on 2009-05-22
No the macbook pro 5.2 does not work fine... it gets very, very hot...the temperature is > 70°C...

@blunt.dualboot

try monitoring another sensor... (in preferences of the applet)

the only solution i've found is setting the fans higher manually, but i don't like that - it should do that automatically (and only when needed)

---

### Post by michaelspoonsm on 2009-05-22
the thing is in leopard the is a thermal control kext for apple coputers because apple computers have the tendency to overheat i see that someone already gave you the code but i just wanted to say and add to this

---

