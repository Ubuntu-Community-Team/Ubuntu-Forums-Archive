---
title: "Fan Control Causing Heat Problems"
date: 2010-03-29
forum: Apple Hardware Users
---

### Post by fletch33 on 2010-03-29
i am using a 13" Macbook Pro version 5,5 running dual boot Ubu 9.10 (64bit) with OS X 10.6.

i have spent hours looking for a straight forward answer to this problem and have had no luck. i have read so many posts with references to a script that i cant figure out or some software that no longer works that i decided i had to post this.

i am at a point where i want to use Ubu as my main OS but my Macbook gets too hot to use if i am doing much of anything on it.

would it be possible in simple terms for anyone to suggest a way to fix this or is it something that can not really be fixed on a Macbook Pro?

i greatly appreciate any help.

thanks

---

### Post by linuxopjemac on 2010-03-29
according to the [wiki]("https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sensors%20(temps%20&%20fans)"), you should add
```
coretemp
```
to the end of /etc/modules

I don't know what that does though.

Maybe you can try to set the fan manually like for the MBP 5,4 (as [here]("http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=39")).
```
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan2_min
```

---

### Post by fletch33 on 2010-03-29
thanks for the info. i have added coretemp and setting it manually seems like a lot of work as my fan needs change all the time while i am working.

i am starting to think that there is not a solution :(

i have actually been considering getting another laptop and selling this MBP just to solve this issue but i really do not want to as hardware wise it is hard to beat this laptop.

on OS X you can get all kinds of programs for this like [SMCFancontrol ]("http://www.macupdate.com/info.php/id/23049") but this doesnt seem to be an option for Ubu.

thanks again for your suggestions

---

### Post by linuxopjemac on 2010-03-30
If you ever find a soluition, be so kind to let us know.

---

### Post by linuxopjemac on 2010-03-30
here the same stuff I gave you earlier, but then applied for your machine
```

echo 1 > /sys/devices/platform/applesmc.768/fan1_manual 
echo 7000 > /sys/devices/platform/applesmc.768/fan1_min
```

[http://allurgroceries.com/mbp55/#fan](http://allurgroceries.com/mbp55/#fan)

You can have this thing done at boot you know, you just make this script to run at boot. No hassle...

like here:
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Nandux on 2010-03-30
I have the very same problem with my MacBookPro, and to increase the fan speen is not the solution for me and even if I increase the speed it looks like the laptop is going to catch fire. Also, I go from 6hours of battery life on osx to 1h30 on ubuntu so there's definitely some power management issues and not just fan issues. I'm still trying stuff such as cpufrequtils to keep the processor down but so far I havent noticed any change in temperature. I know power management is one of the weakness of Linux in general but it just means that we have to work on it!

---

### Post by Nandux on 2010-03-30
Thanks to linuxopjemac, I found this wiki which could prove useful to help with the overheating issue. I will give it a try tonight.

[http://mac.linux.be/content/improve-battery-life-macbook-ubuntu](http://mac.linux.be/content/improve-battery-life-macbook-ubuntu)

---

### Post by linuxopjemac on 2010-03-30
Nandux, I am very curious how that will work out for your MBP. Please let us know your results.

---

### Post by fletch33 on 2010-03-30
> **Nandux said:**
> Thanks to linuxopjemac, I found this wiki which could prove useful to help with the overheating issue. I will give it a try tonight.

[http://mac.linux.be/content/improve-battery-life-macbook-ubuntu](http://mac.linux.be/content/improve-battery-life-macbook-ubuntu)

i also look forward to what you find out. there are many things i can help people with but when it comes to linux i am still very much the student (for now)

this is a great community and i appreciate the help.

---

### Post by Neds Moar Salt on 2010-03-31
Try resetting your PMU if the other stuff doesn't work.

---

### Post by ouilsen on 2010-03-31
I think this is pretty serious. I had random freezes for weeks now. Finally I figured out that it might be my laptop getting too hot. I set the fan1_min speed to 4000 and voilà, no more freezes.

Previously I had openSUSE installed which worked pretty well. No temperature problems for months. This has to be fixed, because you can potentially damage your hardware.

Due to random freezes I guess that a lot of people don't even know that this is their problem.

Btw, my laptop is a Macbook 2.1

Edit:

Make your voice heard on[ launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461184?comments=all").

---

### Post by fletch33 on 2010-04-08
has anyone tried and had any success on any of the ideas mentioned here? i have had no luck and can not make the switch to full time Ubu until i figure this out and its driving me crazy. i would get another laptop but i like my OS X side as well and the Pro hardware.

thanks

---

### Post by undoIT on 2010-04-24
I have noticed these freezes off and on as well over the past 10 months or so, with both Karmic and now Lucid beta. I've got the Macbook 5,1. The thing is, I went for nearly two months without a freeze. However, during that time, I was only using the Macbook either on a table at home or on a table at a coffee shop.

I'm currently staying in a hotel now, using a pillow as desk (maybe more details than anyone cares to know :P). Sure enough, the Macbook froze up after a while. I thought back on the the times it frozen like this previously and it seems that in almost all cases I'm using a pillow or something else with poor heat dissipation as a desk.

Also, when I was having the freezes before, I tried booting into OS X and it froze up there as well. That definitely ruled out a software / driver issue in Ubuntu. I was worried that some of the hardware was failing, but now I think it is just heat related.

I'm experimenting with the command for controlling fan speed:

```
echo 3000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
```

When it froze up earlier, Core 0 and 1 were running between 54 to 64 degrees celsius and the the graphics card was running at 60 degrees and above. This doesn't seem hot enough to cause freeze but maybe it is. With the fan running at 3000 RPM instead of 2000, temperatures have dropped to 40 for Core 0 and 1, plus 45 for the GPU. I bet there won't be any more freezes and I'm glad I may have finally figured out what was causing this.

So, if this does in fact fix the problem, is there a way to have power management automatically kick in the fans when a certain temperature is reached for either the CPU or GPU?

And, does it seem abnormal that the Macbook would freeze up at those temperatures?

---

### Post by kosumi68 on 2010-04-24
> **undoIT said:**
> 
When it froze up earlier, Core 0 and 1 were running between 54 to 64 degrees celsius and the the graphics card was running at 60 degrees and above. This doesn't seem hot enough to cause freeze but maybe it is. With the fan running at 3000 RPM instead of 2000, temperatures have dropped to 40 for Core 0 and 1, plus 45 for the GPU. I bet there won't be any more freezes and I'm glad I may have finally figured out what was causing this.

So, if this does in fact fix the problem, is there a way to have power management automatically kick in the fans when a certain temperature is reached for either the CPU or GPU?

And, does it seem abnormal that the Macbook would freeze up at those temperatures?

It does seem abnormal. Also, the problem has historically been improved upon by driver changes for the particular hardwares. The newest versions (5,1 and up) have not gotten that much attention kernel-wise, so it is possible some change is needed for those models. I am also surprised about the report for a Macbook 2,1, which should be well covered by the current kernel. Perhaps the fan needs cleaning :-)

I have posted links to the old thread [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) in a couple of places recently, might just as well do it here too. Data for models MacBookPro 5,2 and later, all variants, are the ones to look more closely at.

---

### Post by hsoJoshFTW on 2010-05-02
> **linuxopjemac said:**
> here the same stuff I gave you earlier, but then applied for your machine
```

echo 1 > /sys/devices/platform/applesmc.768/fan1_manual 
echo 7000 > /sys/devices/platform/applesmc.768/fan1_min
```[http://allurgroceries.com/mbp55/#fan](http://allurgroceries.com/mbp55/#fan)

You can have this thing done at boot you know, you just make this script to run at boot. No hassle...

like here:
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)



Im running 10.4 on my MacBook 5,1 . Is it the same code for turning up the fan speed to keep the system cool?

---

### Post by alexmurray on 2010-05-02
Note you should never set fan?_manual to 1 as this overrides the automatic fan control of the smc which could damage your machine (since the smc will stop automatically trying to increase the fan as the temp rises). Instead just set fan?_min so that the fan never drops below this certain level but can still increase automatically if needed.

---

