---
title: "cpu temperature"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by p252 on 2006-10-21
What is the average/acceptable temperature for a cpu? Mine averages 49 degrees C to 55 degrees C. I heard linux can be bad for laptops and i don't want to ruin my hardware.

Thanks

---

### Post by DaveBorealis on 2006-10-21
> **p252 said:**
> What is the average/acceptable temperature for a cpu? Mine averages 49 degrees C to 55 degrees C.

Average temp might depend on the size of the cpu, and how intensively you're using it.  Mine isn't Linux, however my iBook G4, a 1.33 GHz PPC cpu, runs about 10 degrees cooler than yours.  I've never peeked at the temp while doing cpu-demanding chores--it's mostly for wordprocessing and similar chores--and I'm guessing that it would jump an easy 10 degrees under heavy use.

> I heard linux can be bad for laptops and i don't want to ruin my hardware.

Not certain where you heard this from, but I've never seen any such evidence.  

Best regards,
Dave

---

### Post by Anduu on 2006-10-21
It all depends on the CPU...

[http://www.heatsink-guide.com/content.php?content=maxtemp.shtml](http://www.heatsink-guide.com/content.php?content=maxtemp.shtml)

---

### Post by p252 on 2006-10-22
Thanks for the info. I followed the link to the heatsink guide and another link from there. I have a celeron M 1.6ghz which max temp according to these sites is 100 degrees C. I have yet to come close to that.

---

### Post by Ophidian on 2006-10-22
Actually I'm a bit concerned about laptop temperatures as well--I know the highest temperature for my CPU is 90C. 

Is there something in Ubuntu/Linux which monitors temperatures and will shut the system down if it reaches or before it reaches unacceptable temperatures?  I have a program in WinXP which can display hard drive / cpu temperature, is there a similar program like this in Ubuntu?

---

### Post by p252 on 2006-10-22
Ophidian,

I'm pretty new so i'm not sure on a program to control shutting down for temp. Power control is still a work in progress for linux. I think some processors automatically slow down (p4's i believe) at a certain temp so overheating is nearly impossible. To check my temp i just entered the command

acpi -t

in the terminal. Not ideal and you have to have acpi enabled (i assume you do with a laptop).

Post here if you do find such a program as i would be interested in using it too.

Best of luck

---

### Post by Anduu on 2006-10-22
> **Ophidian said:**
> Actually I'm a bit concerned about laptop temperatures as well--I know the highest temperature for my CPU is 90C. 

Is there something in Ubuntu/Linux which monitors temperatures and will shut the system down if it reaches or before it reaches unacceptable temperatures?  I have a program in WinXP which can display hard drive / cpu temperature, is there a similar program like this in Ubuntu?

Using the combination of ***lmsensors*** and ***gnome-sensors-applet*** you can set things up so an alarm will sound if a specified temperature is exeeded however I don't think there is any way to have Ubuntu automatically shut the system down.

Alot of modern bioses have an option for auto shutdown when temps get too high...mine does.

You should take a peek.

---

### Post by Kateikyoushi on 2006-10-22
My notebook automatically throttles at 60C.

---

### Post by Joco_Ultimate on 2007-03-26
That is way to much for CPU:s!!! A cpu is supposed to have a temp lesser than 45 C to survive. Else it will be worn down really fast. I have a AMD X2 3800+ that is overclocked and still it is around 30 C. Normally I have it running on about 28 C. That is good! I recomend you to have your laptop checked because that is not good.

---

### Post by mcduck on 2007-03-26
> **Joco_Ultimate said:**
> That is way to much for CPU:s!!! A cpu is supposed to have a temp lesser than 45 C to survive. Else it will be worn down really fast. I have a AMD X2 3800+ that is overclocked and still it is around 30 C. Normally I have it running on about 28 C. That is good! I recomend you to have your laptop checked because that is not good.

No, it depends on CPU model. AthlonXP's have max temp of about 80°C, my laptop (With Core Duo) is built so that the fan doesn't even start running until CPU is around 65°C, and the max temp is at 100°C.. No CPU has max temp of 45 as that would be impossible in many countries at summer time.. Even your Athlon 64 X2 has max temp of 65°C..

Anyway, I find it very hard to believe that you have overclocked CPU running at 28°C with air cooling, that would often be below room temperature.. Are you sure that you are not looking at your Motherboard temperature instead of the core sensor? And are you now telling the idle temp or the temp in full load?

---

### Post by kevinlyfellow on 2007-03-26
> **Ophidian said:**
> Is there something in Ubuntu/Linux which monitors temperatures and will shut the system down if it reaches or before it reaches unacceptable temperatures?  I have a program in WinXP which can display hard drive / cpu temperature, is there a similar program like this in Ubuntu?

Theres a simple gnome-applet that you can monitor with called "Hardware sensors monitor"

Bios will shutdown the computer if it is running way too hot.

---

