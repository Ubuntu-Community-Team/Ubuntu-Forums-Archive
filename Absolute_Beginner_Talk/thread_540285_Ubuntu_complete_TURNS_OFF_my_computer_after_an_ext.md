---
title: "Ubuntu complete TURNS OFF my computer after an extended period of no use"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by SSB on 2007-09-01
Similar situation to this thread which got no attention: [http://ubuntuforums.org/showthread.php?t=375201](http://ubuntuforums.org/showthread.php?t=375201)


After a certain amount of time, the exact amount I do not know as it usually happens when I go to bed or am out for a few hours, Ubuntu will completely power down my system. From there, if I try to turn on the computer, only the fans start up for a few seconds and then turn back up. To get it to finally go back on, I have to turn off the soft switch, fiddle with the wires in the computer (just wiggle them around, really. No idea why I need to do that) and THEN it goes on as if nothing happened. This DOES NOT HAPPEN IN WINDOWS.

I'm baffled as to why this happens. It just started happening one day with no warning after no particular changes in the system. In the power options, it only lists turning off the monitor after 25 minutes. Sleep mode is OFF. I know this happens after some time because I can leave it running for shorter periods (that are longer than 25 minutes, mind you) and come back to it with no problems. The only thing I can think of that I did recently was add a new hard drive, but if I recall properly, this started just before the new drive.

Note that I'm running 7.04

I should also clarify that this only happens during periods of inactivity. I can use it as long as I want with no problems. It's when I leave it that it goes off.

---

### Post by Kitsun on 2007-09-01
Try loading into the BIOS menu, have that run for the amount of time it takes for your PC to shutdown.
That would be a good plan to determine if its a hardware or a software problem.

---

### Post by SSB on 2007-09-01
Well I can leave Windows on for days. I'm assuming it's a Ubuntu problem.

---

### Post by sailor2001 on 2007-09-01
go to system/preferences/screen saver/power management and put slider to 'never' (put to sleep)

---

### Post by SSB on 2007-09-01
"Sleep mode is OFF."


ahem.

---

### Post by RomeReactor on 2007-09-01
Hi. Seeing as you can work with Ubuntu for long periods, and the shutdown only occurs when the system is idle, we can asume for the moment the problem is not hardware-related. Try disabling ACPI in **/boot/grub/menu.lst** and see if it makes a difference:
```
gksudo gedit /boot/grub/menu.lst
```
then scroll down to his section:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs
```
which is just shy of the middle of the file, and add **acpi=off** so it looks like this:
```
]### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
acpi=off
## DO NOT UNCOMMENT THEM, Just edit them to your needs
```
save the file and close gedit, then reboot.

I'm not sure this will work, but it doesn't hurt to try.

---

### Post by SSB on 2007-09-01
OK, I'm getting back into Ubuntu now. While I reboot, care to explain what ACPI is?

---

### Post by RomeReactor on 2007-09-01
It's a specification that defines, among other things, the power management of your system; I'm not knowledgeable enough to explain how exactly it accomplishes that, and the best I can do is point you to its [Wikipedia entry]("http://en.wikipedia.org/wiki/Acpi"). Sorry. However, as your system seems to shutdown while it's idle, disabling the power management seemed like a good idea to try. As I said before, I don't know if this will solve your issue, but trying this might help. If you find it doesn't, you can revert the changes made to the **/boot/grub/menu.lst** file.

---

### Post by SSB on 2007-09-02
Well. Didn't work. Computer shut off again.

---

### Post by GSF1200S on 2007-09-02
Lack of ACPI support can be devastating. Ive heard of overheating and such as the fans may not go on when they are supposed to. Maybe the BIOS detects his core is too hot and shuts the system down?? Ive heard of crazy stuff like that. I know ACPI is used to monitor the computer, and protect it. Maybe he could try and set up lm-sensors just to see if thats his issue?

To the author of this post- you are experiencing the side effects of a hardware company not supporting Linux. ACPI support has to be at least a consideration for companys in terms of Linux. I would suggest searching the "Hardware to Boycott" thread, which has a list of Linux friendly and not so friendly companys.

---

### Post by RomeReactor on 2007-09-02
> **GSF1200S said:**
> Lack of ACPI support can be devastating. Ive heard of overheating and such as the fans may not go on when they are supposed to. Maybe the BIOS detects his core is too hot and shuts the system down??

Yeah, I thought the same thing a little while after posting. Maybe installing **lm-sensors** or **sensors-applet** could be of help in determining the cause of shutdown:
```
sudo apt-get install lm-sensors sensors-applet
```
SSB, after installation you can find sensors-applet by right-clicking in either the top or bottom panel and selecting "Add to Panel...->System & Hardware->Hardware Sensors Monitor".

---

### Post by Gone fishing on 2007-09-02
I just wondering what happens if you gksu gnome-power-preferences 

what do the sliders look like?

---

### Post by SSB on 2007-09-02
To people citing hardware concerns, I don't think that's it at all\, considering i've had the same hardware for over a year with no problems until very recently, and even still it only shuts off WHEN IT'S INACTIVE.

I HAVE had problems before with my CPU overheating, actually. I know exactly what that looks like, and when I had the problem it affected both ubuntu AND windows, and it usually shut off within minutes of booting up. To fix that I just had to readjust my heat sink.

Power preferences has sleep set to off and monitor set to 20 minutes.

The only thing I can think of that could possibly be the cause is the recent addition of a hard drive, but as I stated earlier, memory tells me the problem was here before adding the drive. I'll try starting it up with the drive unplugged, but really, how would another hard drive affect this?


Also, to clarify the soft switch thing, what happens is I have to turn off the switch, and when I wiggle the wires I hear this really faint sound that starts off high pitched and kind of falls to a lower pitch over about half a second. After that, it all boots up.

---

### Post by sailor2001 on 2007-09-02
adding another harddrive is putting an extra load on your power supply and it may not be able to handle that.  Disconnecting the extra drive would give you the clue

---

### Post by darksidedude on 2007-09-02
have you tried takeing the side off of the computer, also does your processor suport speed-step? that could be part of your issue, it could be over heating, when I took a side of my case off and put it over a air vent, never did that again:popcorn:

---

### Post by SSB on 2007-09-03
You guys keep going on about various hardware issues that I have already put to rest. I know the cpu is not overheating, I just tested without the hard drive plugged in and it still didn't work. My computer is completely uncovered with max airflow because when my CPU WAS overheating, I had to mess with it a lot.

As my last effort I am disabling the monitor shutdown in power options.

---

### Post by Lucifiel on 2007-09-03
Maybe you could check the logs(I think it's under System: Admin, maybe... it's been some time I used Gnome) and see if there's some kinda daemon or software that's triggering the shutdown. 

Try searching for "error", "failure", "fail" and other terms in the logs. That's all I can think of and I don't think it's a hardware failure or system overheating. If that's the case, you'd be getting a lot of sirens and beeps and stuff when you try to turn on the pc again.

Edit: From my knowledge, if a computer overheats repeatedly, then it would have problems even starting up: not to mention running even a program.

---

### Post by SSB on 2007-09-03
Here are the last entries in every long between when it shut off last night while I slept and when I just turned it back on:

auth.log:
no error, a bunch of "session opened/session closed"

daemon.log:
no wireless networks notice

debug:
no errors

kern.log:
no IPv6 routers

messages:
--MARK-- at 2:37, which is a good hour after any message I saw so far

syslog:
php cron at 2:39

user.log
resolved xml address at 1:47

x.org.0.log:
nothing of importance.

Looks like it went off roughly an hour after I went to bed. I disabled both power saving options to no avail.

---

### Post by SSB on 2007-09-03
Went off yet again.. I tried messing with some of the wiring in my computer which didn't help at all.

Figured it was wroth a shot. I'm officially out of ideas.

---

### Post by Officer Dibble on 2007-09-03
Please don't get frustrated at my mentioning the BIOS, there is a perfectly legitimate reason for my doing so. :)

In certain model motherboards the BIOS has various Power Management options that probably Ubuntu is responding to that XP doesn't have a clue how to deal with and thus doesn't.

If it is something you have tried already then I'm sorry to mention it, I didn't notice it mentioned in the thread. But, would you like to go into your BIOS and disable your Power Management options? Make a brief note of current settings if you like, and then just disable it.

Alternatively, I'm just taking a look at your motherboard's manual now... I think it's this one isn't it?

[http://www.albatron.com.tw/English/product/mb/pro_detail.asp?rlink=Specification&no=113](http://www.albatron.com.tw/English/product/mb/pro_detail.asp?rlink=Specification&no=113)

BRB... :)

---

### Post by Officer Dibble on 2007-09-03
Yep, go into your BIOS and disable power management if you have no use for it. Or, if you do have a use for it follow a process of elimination - and start by disabling your suspend mode.

Hope this solves your problem... let us know either way, please. :)

---

### Post by SSB on 2007-09-03
I'll try tinkering around in the bios. I wish I could get some more immediate results.. tough to troubleshoot when I'm on the computer a lot and the only way to know for sure is to wait!

I still don't get why it would suddenly start, though. Could it be something in the last kernel update that changes how power management works with my motherboard?

---

### Post by SSB on 2007-09-06
bumping this.. need help still.

---

### Post by Officer Dibble on 2007-09-07
I'd suggest doing some hardware diags then, especially as you have ruled out automated power management features of Linux and the BIOS by disabling them.

When you leave your computer running, what is it doing in the background? Why would you leave it on? Could the problem be down to any applications you are running? What do you use the computer for?

Is your wife finding the computer too noisy and turning it off while you're not there? Do you sleep walk? :)

---

### Post by SSB on 2007-09-08
Yep, disabling all power management didn't help at all. When I leave it running, as far as I know, nothing is going on in the background.. I leave gaim and amsn on usually and that's about it. When I'm on Linux I generally only use it for casual stuff.. all hardware intensive stuff (music production, gaming) happens in Windows..

I doubt the problem is my wife seeing as, 1) I'm only 17, 2) The computer is in my room, and 3) I heard the computer go off a few times after getting off to go to bed and watching some tv beforehand.

Another interesting thing that I should mention, however, is that when I fiddled with the BIOS I tried turning it to an automatic power-on when power is lost. As expected, when it crashed, the power went right back on, but as I mentioned before, I have to wiggle around the wires before it will actually start up when this happens. So when I woke up, I found the LED on my computer giving off a lovely hue, but no activity in the machine, so following the normal procedure, I flipped the  switch on the PSU to start messing with wires, but I found that switching the PSU off entirely left the blue LED on, and it didn't go off until I heard that little sound that I described in an earlier post.

Strange happenings, indeed. If it comes down to it I might just do a fresh install and pray that fixes it :\

---

### Post by SSB on 2007-09-14
bump for the hell of it.

---

### Post by igknighted on 2007-09-15
Have you tried another distro?  Or more specifically, another kernel version?  I've had issues with certain kernels not supporting certain pieces of hardware I have, so it's always worth it to try a different version.  Either try out the new Gutsy alpha (or there is a script if you search the forum to upgrade your kernel if feisty to the gutsy kernel), or maybe go back to Dapper (it has a 2.6.15 kernel).  Or, if you want you could try compiling your own (its actually really simple... search for the master kernel compile thread).

---

### Post by alienexplorers on 2007-09-15
This may sound off the wall, but I had a simular problem.  It happened after a kernel update.  My machine would reboot when not in use due to the screen savers.  My graphics card was causing the machine to reset because of an opengl problem.  After reloading my drivers using ENVY the reboots went away and never came back.

---

### Post by SSB on 2007-09-22
Actually, I've managed to get them to stop by completely disabling the screensaver/lock screen mechanism.

I'll for sure try reloading the drivers, though.

---

