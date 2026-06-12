---
title: "[SOLVED] Overheating laptop, desperately need cpu turned down"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-17
I'm crippled because I can't turn down my cpu, as I could with the little program toshiba included for the OS this machine came with. Within seconds of opening an ogg it blacks out, adept upgrades and anything other than a firefox session are lucky to finish without a power cut. Toshiba stuck a cpu in a laptop that doesn't belong there. 

A certain ciscosurfer said I need a cpufreq with a low power governor. They suggested p4_clockmod and cpufreq_powersave, but I can't find these through adept although I've enabled unverse, all be it with upgrade errors. 

I think powernowd might be the key. I thought maybe kpowermanager too, but I'm quite sure that just refers to the thing in the system tray which only lets me adjust what to do when the battery's low or the laptop lid is closed. It shows me that cpu frequency is at 1600 MHz, about halfway up it's bar, but frustratingly doesn't let me edit that. 

In kde system settings it says powernowd should start at boot but that it is not running. I tell it to start, it says done, but goes on saying not running. I do

> sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit: -- 1 'CPU' per scalable unit
powernowd: cpu0: 1600Mhz - 3067Mhz (2 steps)

and don't know what that info's worth. Not even sure what powernowd is or if it will do what I want. I can't really tackle anything else until this is problem is sorted out. 

Thank you!

---

### Post by dmizer on 2006-11-17
humm i have several toshiba's all with heat problems that i've solved ... what model are you running?  does the fan come on at all?

---

### Post by leetrefz on 2006-11-17
It died as I was writing this with nothing but firefox open. This is a Satellite A70, from 2004. The 2 fans do come on, and I've got a cheap usb fan tray under it to help.

---

### Post by dmizer on 2006-11-17
well, you can force the fans to come on all the time with the following command:
```
sudo su
echo "force_on:1" > /proc/acpi/toshiba/fan
```
which is what i've done to most of my older toshiba laptops.
if that helps, you can add the echo line to /etc/rc.local right above the "exit 0" line.

might be a little more noisy that way, but it's preferable to a meltdown in my opinion.

there's also a utility that i've used successfully on some systems called toshutils: [http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html) ... it's in synaptic, and it does support cpu scaling.

---

### Post by leetrefz on 2006-11-18
Well, I get
> root@chief-laptop:/home/chief# echo "force_on:1"> /proc/acpi/toshiba/fan
bash: /proc/acpi/toshiba/fan: No such file or directory


So I went in with konqueror and found /proc/acpi/fan, with nothing in it, and no toshiba folder, though a sony one for some reason, also empty. There's a thermal_zone folder that also appears empty (showing hidden files). There are some interesting though empty document files in /proc/acpi/processor/CPU0 called limit, power & throttling. 

Having no luck with that buzzard.me.uk link, is it just me? what to look for in symantec?

Thanks a lot eh

---

### Post by localuser on 2006-11-18
Have you tried a bios upgrade?  Its a long shot, but that's how I fixed a similar problem.

---

### Post by scrooge_74 on 2006-11-18
I also have a toshiba a SAT PRO 6100, from time to time the fan will start by itself, but I usually do it by myself.

sudo toshset -fan 6 for low speed

it keeps my PC cool enough with not to much noise

At install time the toshset utilites got install automatically, I did install later the toshutils, but I just use the command above

---

### Post by leetrefz on 2006-11-18
Maybe I should upgrade bios again. The 2 fans are always running low, too low. I think I really need to regulate the cpu frequency. 
Anyway, 
> chief@chief-laptop:~$ sudo toshset -fan 6
Password:
required kernel toshiba support not enabled.


does that mean I enable somewhere or download a package? I'd like to take this opportunity to post my package update problems. From synaptic, 'could not download all repository pachages':
> [http://mo.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://mo.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://mo.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:](http://mo.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

I had problems in windows too. I kept the cpu on low in the toshiba power manager or there was no hope. I can't play an ogg here without it dying before I hear anything. adept updates are a hazard too. Even poops out sometimes when I've only been on firefox for a while. The fan speed does vary, though not as much as with windows. I think in win I was running less than the 1600Mhz I am now... and I was still having trouble.

---

### Post by scrooge_74 on 2006-11-18
I read somewhere that some Toshibas have a different BIOS, which does not support toshset or toshutils.  It seems Toshiba got those BIOS from someone else. Sorry I can't be of much help here


[http://schwieters.org/toshset/](http://schwieters.org/toshset/)
[http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html)

---

### Post by dmizer on 2006-11-18
interesting ... see if you can do this:
```
sudo modprobe toshiba_acpi
```

the toshiba_acpi module is your required kernel support.

i also had problems with the computer overheating in windows.  i used this utility: [http://www.almico.com/speedfan.php](http://www.almico.com/speedfan.php) to regulate my fan speed and cpu temperature.

i've always had the toshiba_acpi module loaded by default in my ubuntu installs.  not sure why you didn't get it.  once it's installed though, then you'll have the /proc/acpi/toshiba/ directory.

---

### Post by junglepeanut on 2006-11-18
[http://ubuntuforums.org/showthread.php?t=301995](http://ubuntuforums.org/showthread.php?t=301995)

---

### Post by richiewrt on 2006-11-18
This wont help solve your problem, but I know there is an ongoing class action lawsuit pending against toshiba for the a70 laptop. I know because i had one die on me. Just got a letter in the mail on the lawsuit, but dont have the laptop anymore. Maybe something you want to look into.

---

### Post by leetrefz on 2006-11-18
whoa, > chief@chief-laptop:~$ sudo modprobe toshiba_acpi
Password:
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.17-10-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device
chief@chief-laptop:~$


---

### Post by junglepeanut on 2006-11-18
What happened when you tried the option I suggested in the thread I linked to earlier?

---

### Post by leetrefz on 2006-11-19
I don't think the second link is working. 
I took apart my fan tray and taped the 2 fans from it to the fans under the computer spaced with cut up toilet paper tubes. I think that might be hepling. 

Ya that 
[http://ubuntu.wordpress.com/2005/11/...uency-scaling/]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/") link isn't going anywhere for me.

---

### Post by dmizer on 2006-11-19
okay ... that just happened because your toshiba doesn't have the right chipset/bios for the toshiba module.

try this:
```
sudo aptitude install fnfxd
sudo fan -n
```
which i believe is independant of bios and acpi support.

---

### Post by leetrefz on 2006-11-19
Not having much luck here.
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  fnfxd
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.6kB of archives. After unpacking 127kB will be used.
Writing extended state information... Done
Get:1 [http://mo.archive.ubuntu.com](http://mo.archive.ubuntu.com) edgy/universe fnfxd 0.3-7ubuntu2 [19.6kB]
Fetched 19.6kB in 16s (1161B/s)
Selecting previously deselected package fnfxd.
(Reading database ... 83144 files and directories currently installed.)
Unpacking fnfxd (from .../fnfxd_0.3-7ubuntu2_i386.deb) ...
Setting up fnfxd (0.3-7ubuntu2) ...
Starting Toshiba hotkeys utils: FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).

invoke-rc.d: initscript fnfxd, action "start" failed.


So I guess I somehow enable the kernel's acpi Toshiba option? or is that what we've been through around the 13th post?

Thanks richiewrt, by the way, [http://www.toshibaa70classaction.com/]("http://www.toshibaa70classaction.com/")

---

### Post by dmizer on 2006-11-19
> **leetrefz said:**
> or is that what we've been through around the 13th post?

yes, that is what we went through around the 13th post.  sorry.

what happens when you do this:
```
sudo su
cat /proc/acpi/processor/CPU0/throttling
cat /proc/acpi/processor/CPU0/info
exit
```

---

### Post by leetrefz on 2006-11-19
Hey, this looks promising
> root@chief-toshiba:/home/chief# cat /proc/acpi/processor/CPU0/throttling
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%
root@chief-toshiba:/home/chief# cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
root@chief-toshiba:/home/chief# exit
exit
chief@chief-toshiba:~$                           

Should I do the first command and type in T2 or something?

---

### Post by dmizer on 2006-11-19
close ... 
```
sudo su
echo -n # > /proc/acpi/processor/CPU0/throttling
exit
```
where "#" is the single digit in T0 - 7.  and since i'm having a hard time making that clear, i'll give you a couple of examples:
if you want 50% cpu frequency scaling the command will read:
```
echo -n 4 > /proc/acpi/processor/CPU0/throttling
```
for 25%:
```
echo -n 2 > /proc/acpi/processor/CPU0/throttling
```

where 0 is full power and 7 is 87% of full power.

if you're able to throttle your cpu with this command, i'll give you directions on how to make it happen on boot.

there's a huge range of things that you can do with your computer by using the acpi tools.  might start here:
[http://acpi.sourceforge.net/documentation/processor.html](http://acpi.sourceforge.net/documentation/processor.html)
also found a nice script and more information here: [http://skull.piratehaven.org/~mike/index.cgi?gateway](http://skull.piratehaven.org/~mike/index.cgi?gateway)

---

### Post by junglepeanut on 2006-11-19
I use the CPU Frequency Scaling Monitor on my panel to see the speed of my CPU. I have a centrino laptop. Ubuntu automatically increases the speed (frequency) of my laptop when the demand is more, and manages things very well.

However, when I am plugged in, I want to run my laptop at the maximum possible frequency at certain times. It turns out that the CPU Frequency Scaling Monitor can also have the functionality to change the Frequency, by “Governing” the CPU frequency. However, by default, on my laptop, left-clicking on the Monitor in the Panel did not give me the option to change the frequency.

In order to be able to change the operating frequency, your processor should support changing it. You can find out if your processor has scaling support by seeing the contents of files in the /sys/devices/system/cpu/cpu0/cpufreq/

For example, on my system:

```
$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
gives:

    1300000 1200000 1000000 800000 600000

Which means that the above frequencies (in Hz) are supported by my CPU.
and…
```
$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
gives:

    userspace powersave ondemand conservative performance 

All those are the different “modes” I can operate the CPU at. Userspace, for example, regulates the frequency according to demand. Performance runs the CPU at max-frequency, etc…

On the Ubuntu Forums, I read that one can manually change the frequency by executing commands like:
```
$ cpufreq-selector -f 1300000
```
which will set the frequency to 1.3 GHz.

Now, I was interested in being able to change the power mode (between the different values listed in the “governors” above, manually by using the Cpu Frequency Panel Monitor.

I found out from the Forums, again, that changing the permissions of the cpufreq-selector binary by doing a:
```
$sudo chmod +s /usr/bin/cpufreq-selector
```

will allow me to acheive this. However, I was curious as to why Ubuntu does not, by default, allow me to choose the frequency using the CPU Frequency Panel Monitor, and what the “right” or “correct” way of enabling this is.

With a little bit of detective work, I found the reason why things are the way they are in Bug #17604 :

    Oh, please, not another setuid root application if we can avoid it. Which file does cpufreq-selector need access to to change the CPU speed? And why should a normal user be able to change the CPU speed in the first place? The automatic CPU speed works well enough for the majority of users, and control freaks can always use sudo to manually set the speed, or deliberately shoot themselves in the foot by making the binary suid root (as explained in README.Debian).

Anyways, since I really want to “shoot my self in the foot” using my CPU ;), so I read the readme:
```
$cat /usr/share/doc/gnome-applets-data/README.Debian
```

and as suggested in it, I did a
```
$ sudo dpkg-reconfigure gnome-applets
```
and answered “Yes” to the question regarding setting the suid of the cpufreq-selector executable. Now, by left-clicking on the CPU Frequency Monitor Applet, I can choose the frequency for my processor, and things couldn’t be better!!

P.S.: A lot of my detective work could have been avoided had I read the README in the first place. Stupid me.

---

### Post by junglepeanut on 2006-11-19
Above is a cut and paste from the website you could not open...hmm it opens fine for me.

---

### Post by leetrefz on 2006-11-19
Weird. Maybe China's blocking that site by mistake. They're zealous. I'm on KDE eh, so I don't know how much of that is relavant for me, but here's what I have found. First in response to dmizer, > root@chief-toshiba:/home/chief# echo -n 3 > /proc/acpi/processor/CPU0/throttling
root@chief-toshiba:/home/chief# echo -n 2 > /proc/acpi/processor/CPU0/throttling

nothing came up after that, just went back to prompt so I tried again same thing. As for junglepeanut's code, > root@chief-toshiba:/home/chief# $cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies: Permission denied
root@chief-toshiba:/home/chief

So with konqueror I found that scaling_available_frequencies says "3067000 1600000", the lower number reitterated by cpuinfo_min_freq, scaling_min_freq, & scaling_cur_freq. 
scaling_available_governors says "userspace powersave ondemand conservative performance", and scaling_governor is blank.

In the toshiba power manager that came with windows I had more like 5 options for processor speed.

---

### Post by dmizer on 2006-11-19
> **leetrefz said:**
> I'm on KDE eh, so I don't know how much of that is relavant for me, but here's what I have found. First in response to dmizer, 
nothing came up after that, just went back to prompt so I tried again same thing.

it won't matter if it's kde or gnome xfce or any number of others.

once you've run the command i gave you, your cpu is throttled to the percentage you input (there will be no feedback to indicate that the command worked ... only an error if it didn't work).  keep an eye on your cpu temperatures with something like gkrellm and expiriment with the setting that gives you the best performance to temperature range ratio.

---

### Post by leetrefz on 2006-11-20
Ok, great, thanks!!

I can put the setting into boot somehow?

& the k power manager still says 16000MHz, I guess that's just its problem?

---

### Post by dmizer on 2006-11-20
yeah ... but that's the easy part.
just add the line to /etc/rc.local before the "exit 0"

i'm sitll trying to toy with it and figure out if there's a way you can confirm that the setting has both changed and is working.

---

### Post by leetrefz on 2006-11-20
I'm not so sure it's working actually, still dies when I start a music file or supertuxkart when set to 2.

---

### Post by leetrefz on 2006-11-21
Switched to xfce, huge improvement, can even play audio!
xfce is really more my taste anyway, glad I tried it. 
Those others are just too busy, like they're trying too hard. 
This is sharp and efficient.

---

### Post by scrooge_74 on 2006-11-21
Glad to hera you manage to work a solution...I think I will take a look at xfce this weekend just to have fun. I love puzzles and challenges.

Have fun

---

### Post by leetrefz on 2006-11-21
You might be disappointed, this is no challenge, it beats kde, gnome, mac, & windows in instinctive ease of use as far as I'm concerned. I'd say it looks better too, more elegant, less bombastic. I guess i can't set a desktop image, but think I'll survive. it's absolutely perfect for me. pretty much every problem I had in kde is magically solved and I don't feel like I lost anything. i'm in love.

---

### Post by junglepeanut on 2006-11-21
You can set the desktop image look under settings in Xfce.
User Name

---

### Post by leetrefz on 2006-11-22
figured it out, don't see how this one can be so much easier on resources than kde.

---

### Post by junglepeanut on 2006-11-25
It was for me, I then tried fluxbox and icewm and the other variations. I decided the best one for daily usage was icewm. Why you ask? Specifically for one reason, Start up time, icewm start instantly on my system, I cant even count the time, everything else takes at least 3 seconds. If I want to show off then xgl. Maybe with feisty aiglx will finally work for me?

---

### Post by slush1000 on 2006-11-25
This may be a little late of a response, I skipped through most the messages  so I hope this hasn't been suggested already.

I also have the Toshiba A70 with Kubuntu and was plagued with the same problem of constant overheating.

The solution that I found was to install cpufrequtils through adept and with every reboot I open a root console and enter both:
 
cpufreq-set -c 1 -u 2400000
cpufreq-set -u 2400000
(sometimes twice for good measure :-D )

This effectively scales the cpu to what the Toshiba control in XP calls 'med' I believe. I haven't suffered a single shutdown since. Even while modeling/rendering scenes in Blender 3D.



Hope this helps.

---

### Post by leetrefz on 2006-11-27
> chief@chief-toshiba:~$ cpufreq-set -c 1 -u 2400000
wrong, unknown or unhandled CPU?
chief@chief-toshiba:~$ cpufreq-set -u 2400000
Error setting new values. Common errors:
- Do you have proper administration rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set an invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   or because the userspace governor isn't loaded?
chief@chief-toshiba:~$ sudo cpufreq-set -u 2400000
chief@chief-toshiba:~$ 


well maybe that second one is working.
You saved me 600$!!

---

### Post by leetrefz on 2006-11-28
hey JP, is icewm the very lightest of the bunch? I could care less how many features the de/gui has as long as it doesn't look like windows 3.1 or apple 2 or something. if it looks pleasant and is taking less resources that my actual tasks can use I see no reason to go on with a blood-sucking one.

---

### Post by junglepeanut on 2006-11-29
Icewm, fluxbox, fvwm, blackbox are all pretty light weight as they are window managers not desktop enviroments. I recall initially I really liked the looks of fluxbox, but something about it did not feel just right. And when I went to icewm I was like ugh this is not pretty at all. So I kept going back to xfce because it had just the right amount of looks, but I never forgot the speed which with icewm started. So I started searching for themes (note the default which I was like no way originally in my opinion is much much better than some of the others in it.) The next thing is it is highly customizable. I am not into that too much, but sometimes I like it. You can have transparency too. So now I use icewm almost all the time.

I would play with all of the ones I listed above and even see if you can get some more to find the one that fits you perfect. Then you will know for sure what you want. Then you can uninstall them or leave them on just in case one wasn't feeling just right but after some more experience you may realize there was a benefit to that other one.

Whats really great is since I have them all installed if for some reason I just want to use nautilus or thunar, I can, (note nautilus some times messes with preferences for the current setting.) 

Please also remember I spend most of my time on this computer studying and writing numerical code, so I am looking at terminals a lot. Not all the pretty stuff.

Here is a link to some themes for icewm I let you look for all the other wm's. You can get most of the themes from the repositories (read as => almost all in one package) Note Icewm is often called the impersonator as many people make it look like mac or windows replicas.

[http://themes.freshmeat.net/browse/925/](http://themes.freshmeat.net/browse/925/)

---

### Post by leetrefz on 2006-11-29
ok, thanks, guess i'll get sucked into one of these lighties sooner or later. fluxbox seems wierd to me too, I think i need to know keyboard commands or something to get so much as a terminal. there's some great looking icewm setups on lynucs.org.

---

### Post by wulf on 2006-11-29
Have you checked the state of your heatsink? Earlier this year, I noticed that my laptop (Packard Bell) was overheating (to the point of shutting down) more and more frequently. Then I opened it up and undid a few more screws than the previous time I had looked and discovered I could pull the whole heatsink out:

[[img]http://static.flickr.com/71/189981273_36048dbc27_m.jpg[/img]](http://www.flickr.com/photos/wulf/189981273/)

In the end, all it needed was a bit of cleaning and then the fan could actually succeed in blowing air over the heatsink and cooling the CPU: sorted!

Wulf

ps. XFCE rocks! :)

---

### Post by leetrefz on 2006-11-29
that's probably a good idea. 

Will probably help but with the class action suit against toshiba over this model I doubt its the main issue. 

I am quite happy with xfce.

---

