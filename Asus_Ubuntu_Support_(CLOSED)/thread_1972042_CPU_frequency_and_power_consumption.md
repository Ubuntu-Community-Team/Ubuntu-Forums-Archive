---
title: "CPU frequency and power consumption"
date: 2012-05-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Oblivio on 2012-05-03
Asus K50AB, dual Tamron processor, able to go at 0,5 - 1,1 - 2,2 GHz &#8594; noisy as hell and doesn't know how to save power.

Two things are really frustrating about this:
1.) That my windows 7 installation works far more silently
2.) That there was no problem with power management in Ubuntu Lucid (10.04)

So, to start at the beginning:
First I tried installing Jupiter which did just about nothing at all. Perhaps I didn't know what to look for but unless my computer was running on battery nothing changed. Even then the main problem, which is the high CPU rate, was not undone.

Next I installed cpufreq... actually, I installed cpufreqd because the +d was the only package I found via synaptic in addition to cpufreq-indicator and a plugin for xf4ce (or sth) which I don't even know what it is/does. Please correct me if I'm wrong or fill me in.

Cpufreq-indicator is completely useless because it only *shows* that my cpu is running on performance when it should be ondemand. If I try checking the ondemand option it resets to performance in a matter of seconds. If I choose any of the numbered values (0,5 - 1,1 - 2,2) it only selects 2,2 and sticks with it.

Googling for solutions I came across a way which was to change the value, given by ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` to "ondemand". I tried the upper code, sure enough gave me a "performance" value.

However, I was unable to save any changes via "gksu gedit" or "sudo gedit" due to an "inable to create security/safety copy/backup when saving /"path"/scaling_governor" issue. I am given an option to "save anyway" at that point, but even if I click on it it still doesn't save.

There was an option to```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
( &#8593; wrong code, at least now it is giving me "no file or directory" error)
``` to append a function to the general state and I think that helped but it did not survive a reboot.

[b]What I need is a way to make it permanent. Eitehr by changing the governor or some other file - in a way that will actually save the changes or by fixating the echo.[/g]

I have had problems with Ubuntu in this area since I can remember. The frustrating things are that:

1.) 10.04 did not have this problem... but in every distro afterwards the problem persists. Either the fan cooling goes from 0 to SPARTAAAAA every two minutes and a half for about 15 seconds or it just doesn't shut up.

2.) As I'm writing this I am messing around in terminal to determine the codes again and the computer has been surprisingly quiet since about "there was a code" part. Even the cpufreq-indicator is working. Or at least it's not resetting the preference - though the numerical setting still doesn't set to 0,5 when I click on it. All of which I know will change as soon as I reboot. Yesterday a similar thing happened (weird part is then I uninstalled the cpufreq packages) but today the computer was once again its old rowdy self.

So yeah... any idea on how to override the "performance" value in governor? gedit or anything else is fine, though trying through a live key didn't show the system files.

---

### Post by TBABill on 2012-05-03
Normally you can ```
sudo cpufreq-set --governor ondemand
```If you need to adjust each CPU independently, then after "cpufreq-set" just add -c 0 or -c 1, with the number denoting each CPU you are setting independently. Instead of --governor you can use a single - and do a -g, but sometimes -g did not work on mine while --governor did. They're supposed to do the exact same thing but I had tried multiple times on one computer with -g with no effect, but got success with --governor...no idea why.
 
[http://manpages.ubuntu.com/manpages/hardy/man1/cpufreq-set.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/cpufreq-set.1.html)

---

### Post by Oblivio on 2012-05-03
Thank you.
It worked; the cat command returned a value of ondemand once I entered your code... but only untill I rebooted. Now it's back to Performance.

Should we just blame it on Windows? I feel like blaming it on Microsoft. Too bad Lucid works. -.-

Still, now at least we know the input system is not at fault, it really is the retaining system... I encrypted the home folder - would that count for anything? Or could there be other circumstances?

---

### Post by TBABill on 2012-05-03
No it's a setting in a .conf file that sets it on each restart. I'm on a Windows machine today and can't research to find out which file you make the change within. I'll try to Google for it and will post back if I find the specific location.
 
Edit: Could it be _/sys/devices/system/cpu/cpu*/cpufreq/_

---

