---
title: "Is Feisty Fawn a cooker??"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by ela04cz on 2007-08-14
I have installed feisty fawn for 2 month, generally it is doing a good job, the speed, eye candy (Beryl, i installed) security... Jut one thing I am not satisfied with: it is cooking my computer!

My machine is sony´s VAIO VGN S26, Intel 1.5GHz, 256MB Memo, and 40GB Hard drive. As it is old, I dual boot it with XP and Feisty Fawn, looking for more speed (indeed the XP home edition was very slow on it, especially when I open a series of firefox tabs, it is like a slug).

But after testing both system temperature (acpi -t for feisty and speedfan for xp) I found under feisty the temperature is way out of XP level, around 50 C while XP is around 30 C (of course, both under the similar condition: open a few firefox tabs). Also from the sound of the fan and finger feeling I can tell that the feisty temp is a lot higher than XP, at least in low load condition. 

Although I remember XP use to cook my machine too, before I installed feisty, sometimes it drove the fan to an extreme speed. However I have to say that XP is doing better on system temperature than feisty ( in my case, Xubuntu 7.04). Someone says it is due to a critical bug inside the kernel, I don´t know. Or is it because of an unsuccessful installation? As I re-installed xubuntu 704 few days ago, and it seems to me that before this, it worked quite silently.

I bought a 3 fan cooler pad and put it under the machine, helps a bit. But still I want to know a  way to improve it.

---

### Post by ThinkBuntu on 2007-08-14
Linux isn't as good at managing power (yet) as Windows and Mac OS. That's why our batteries don't last as long and why our systems run hot, making for quite a bit of fan noise. I guess we'll just have to give it time...

---

### Post by Alterax on 2007-08-14
My batteries used to get really hot on my iBook G4 that is running Ubuntu PPC.  I was able to make some changes to the powernowd daemon so that it only used 60% of the processor at a time.  This significantly cut power consumption and heat production without really sacrificing much performance (in fact, I say it runs faster now because it's having less heat effects).

Try tuning your powernowd settings and see if that helps.

--Alterax

---

### Post by ela04cz on 2007-08-14
So what change did you make to powernowd? And how?

---

### Post by ThinkBuntu on 2007-08-14
You should use this brief article if you want to be able to scale your processor performance. It worked for me, although I've left it in "On Demand" mode because I'm plugged into the wall.

Ubuntu Geek: [Howto Change CPU Frequency Scaling in Ubuntu]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html")

---

### Post by matburton on 2007-08-14
You can change the frequency governor like this:
```

sudo cpufreq-selector -g conservative
sudo cpufreq-selector -g powersave
sudo cpufreq-selector -g ondemand
sudo cpufreq-selector -g performance

```
I use conservative when on AC (its keeps my laptop pretty cool and quiet while keeping it responsive) and powersave when on battery because I don't want my lap cooked or my battery raped!

EDIT: Oh and you can change the gnome panel frequency applet to have a drop down list with governor and frequency options by giving it root access and reconfiguring the package as such:
```

sudo chmod +s /usr/bin/cpufreq-selector
sudo dpkg-reconfigure gnome-applets

```
Then just place a copy on your panel and click it when you want to change it ;-)

---

### Post by ela04cz on 2007-08-14
Thanks a lot for helping guys! I got it!

---

### Post by gn2 on 2007-08-14
Remember that most Windows temp monitors aren't very accurate, this one works though: [http://www.thecoolest.zerobrains.com/CoreTemp/](http://www.thecoolest.zerobrains.com/CoreTemp/)

---

### Post by operator207 on 2007-08-15
> **gn2 said:**
> Remember that most Windows temp monitors aren't very accurate, this one works though: [http://www.thecoolest.zerobrains.com/CoreTemp/](http://www.thecoolest.zerobrains.com/CoreTemp/)

I agree with this statement, not the URL since I have not tested it, but the fact that temp monitors (in general) need to be configured.

Does your bios have the ability to tell you what your temp is? Some do, other do not.

I found that I had to configure my temp monitor (mbm i think it was in windows) so it would show the correct temp. If I had not, mbm was telling me my temp was around 50F. Ya, I doubt that, with air cooling. I would imagine the same goes for linux temp monitors. 

I have done what other have done, with setting the scaling on my P4 laptop, it helps, but my laptop is tarded when it comes to bios and acpi, so it just runs the fans full tilt regardless of temp. I imagine when its not running at full load, its got a pretty cool cpu. 

Might check out this link: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

May give you better sensor abilities. Who knows.

---

### Post by Hobo Joe on 2007-08-15
> **gn2 said:**
> Remember that most Windows temp monitors aren't very accurate, this one works though: [http://www.thecoolest.zerobrains.com/CoreTemp/](http://www.thecoolest.zerobrains.com/CoreTemp/)

Also remember, the fact that you are running apps such as beryl or compiz would play a huge part in that, because they are pretty CPU/GPU intensive programs.

---

### Post by gn2 on 2007-08-16
> **Hobo Joe said:**
> Also remember, the fact that you are running apps such as beryl or compiz would play a huge part in that, because they are pretty CPU/GPU intensive programs.

Agree completely, my desktop PC is noisier using 3D effects which is why I don't use them.

Silence is golden. 

[www.silentpcreview.com](www.silentpcreview.com)

---

