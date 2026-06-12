---
title: "Slow and unresponsive Ubuntu"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by 3ntity on 2006-11-23
Hey,
I've been running Edgy Eft for about a month without problems (well, there was one during installation - Edgy chose to format the partition where i had Dapper installed on, even tho i explicitly chose a different partition for Edgy, and also avoided formatting the partition with Dapper on, so i could still run that, but it was all gone upon booting Edgy :/). 
So, everything has been running quite smoothly, until today. Problems started with Opera, which chose to repeatedly close itself for no apparent reason. I then used FireFox for a bit, which gave me no problems. 

After using the computer for about an hour or so, applications started running and closing very slowly; the general responsiveness of the system was gone. Upon rebooting, the login from the user screen to the GNOME-desktop took enormously long, over a minute when usually it takes +/-20 seconds. And again, programs are starting slowly, and responsiveness is slow. System monitor doesn't show any programs using ridiculous amounts of RAM. Even running programs like gedit or running a terminal take long, as in 20+ sec.
My specs are: PIV 3.0GHz, 1GB RAM, GeForce 6600. Things ran quite a bit better until today. All i installed in the past few days was Skype and .RAR compatibility for FileRoller as explained on [www.ubuntuguide.org](www.ubuntuguide.org), and enabled Ctrl+Alt+Del to open System Monitor.
Any ideas what has gone wrong or what i could try?
Thanks in advance for any help :)

---

### Post by Charles Hand on 2006-11-23
Run System Monitor and see if there's anything eating up all the cpu cycles. Assuming your System Monitor is gnome-system-monitor, click on the Processes" tab. Go to the View menu and make sure "All Processes" is checked. Click on "% CPU% to sort the list according to % cpu usage with the highest usage at the top. What's there? If you're not actively running anything else, the busies thing should be gnome-system-monitor consuming a very small amount of CPU.

If you don't have gnome-system-monitor, open a command shell and run "top".

---

### Post by nickburns on 2006-11-23
Open a terminal and run

ps -ef

and it will show you all the processes that are running and how much cpu they are using.

to kill a process type:

kill -9  "the process number from above"

---

### Post by 3ntity on 2006-11-23
> **Charles Hand said:**
> Run System Monitor and see if there's anything eating up all the cpu cycles. Assuming your System Monitor is gnome-system-monitor, click on the Processes" tab. Go to the View menu and make sure "All Processes" is checked. Click on "% CPU% to sort the list according to % cpu usage with the highest usage at the top. What's there? If you're not actively running anything else, the busies thing should be gnome-system-monitor consuming a very small amount of CPU.

If you don't have gnome-system-monitor, open a command shell and run "top".

It is indeed like that: gnome-system-monitor uses about 2-5%... 
"top" shows heavy memory usage: about 900MB used, but the processes listed only account for 1-5% of memory usage :/ Displaying virtual memory usage in gnome-system-monitor also shows this, (with 10 processes using 50MB+ virtual memory) although normal memory usage is low (~200MB total). Is this normal?
Cheers

---

### Post by Charles Hand on 2006-11-23
> **3ntity said:**
> It is indeed like that: gnome-system-monitor uses about 2-5%... 
"top" shows heavy memory usage: about 900MB used, but the processes listed only account for 1-5% of memory usage :/ Displaying virtual memory usage in gnome-system-monitor also shows this, (with 10 processes using 50MB+ virtual memory) although normal memory usage is low (~200MB total). Is this normal?
Cheers

The CPU usage seems correct. The 900MB might not be too unreasonable. The gnome-system-monitor memory readings are quite reasonable.

So there's no clue there to why your system is sluggish.

Is it just GUI stuff? For example, when you do operations from the command line such as top and ls -la, is the response sluggish?

---

### Post by mployee8 on 2006-11-25
I'm having same issue. Using 2ghz Athlon 64 processor, 2GB memory, ATI Xpress 200 onboard video adapter. Apps take forever to open, even teminal. HELP?!

---

### Post by jerrykenny on 2006-11-25
Make sure your session manager is starting with a fresh session every time you log in . . . . as opposed to restarting your old session . . . 

try df to see what your disk usage is like . . . 

Configure your system to flush /tmp and /var/tmp every time you boot.

Look at your boot manager to see what services are being started at boot time (   bum is the boot up manager)

Is it a 64 bit bug ?

---

### Post by 3ntity on 2006-12-02
Yesterday i gave Edgy a try again since i have more time now, and it started up insanely slow, taking a long time to load 'Window Manager', 'Nautilus' and 'Update Notifications'. Today i logged in again, no problems. Everything was back in running order, working as smoothly as before. Any ideas what could have caused this though? The problem lasted more than 1 reboot, by the way. 

> **jerrykenny said:**
> Make sure your session manager is starting with a fresh session every time you log in . . . . as opposed to restarting your old session . . . 
How do i check this?

> try df to see what your disk usage is like . . . 
The ubuntu partition has 25+GB left so that shouldn't be the problem :)

> Configure your system to flush /tmp and /var/tmp every time you boot.
Again, at a loss as how to do this...

> Look at your boot manager to see what services are being started at boot time (bum is the boot up manager)
Will check try this soon, i'll disable all the things i don't need in the process, should come in handy :)

> Is it a 64 bit bug ?
System is not 64 bit, so no.

> **Charles Hand said:**
> Is it just GUI stuff?
Yes, when i had this problem, it seemed to be just GUI stuff. As soon as they were running, they ran OK, but anything graphical taking time.

Thanks for the help guys, and sorry for replying so late, didn't have time this week to look into the problem :)

---

### Post by 3ntity on 2006-12-05
And... the problem has returned... I'll try to figure out how to make sure my session manager is starting with a fresh session every time i log in and to configure ubuntu as to flush /tmp and /var/tmp every time i boot, any advice for this are more then welcome.

Here's a screenshot of the bootup manager, which seems to be loading a sensible amount of services. Could samba or usplash be slowing my system? I honestly don't think the latter, since the problem begins when loading my session till i shut down :/ 

Anyways, thanks for any help :)

---

### Post by wpshooter on 2006-12-05
> **3ntity said:**
> Hey,
I've been running Edgy Eft for about a month without problems (well, there was one during installation - Edgy chose to format the partition where i had Dapper installed on, even tho i explicitly chose a different partition for Edgy, and also avoided formatting the partition with Dapper on, so i could still run that, but it was all gone upon booting Edgy :/). 
So, everything has been running quite smoothly, until today. Problems started with Opera, which chose to repeatedly close itself for no apparent reason. I then used FireFox for a bit, which gave me no problems. 

After using the computer for about an hour or so, applications started running and closing very slowly; the general responsiveness of the system was gone. Upon rebooting, the login from the user screen to the GNOME-desktop took enormously long, over a minute when usually it takes +/-20 seconds. And again, programs are starting slowly, and responsiveness is slow. System monitor doesn't show any programs using ridiculous amounts of RAM. Even running programs like gedit or running a terminal take long, as in 20+ sec.
My specs are: PIV 3.0GHz, 1GB RAM, GeForce 6600. Things ran quite a bit better until today. All i installed in the past few days was Skype and .RAR compatibility for FileRoller as explained on [www.ubuntuguide.org](www.ubuntuguide.org), and enabled Ctrl+Alt+Del to open System Monitor.
Any ideas what has gone wrong or what i could try?
Thanks in advance for any help :)

How did you go about enabling Ctrl+Alt+Del to open system monitor ?  Did you use Automatix ?

---

### Post by 3ntity on 2006-12-07
> **wpshooter said:**
> How did you go about enabling Ctrl+Alt+Del to open system monitor ?  Did you use Automatix ?
Nope, [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME")

---

### Post by ]Nbx*cmD[ on 2006-12-07
900 Mb!!! Wow! I don't even have that huge amount of RAM to spend! Who says this is reasonable? This might be reasonable if you were using windows vista or similar ram-wasting stuff! 

In my laptop I have 512Mb and when running the GUI i spend less than 5 Mb counting X.org and ratpoison (my wm).

There is SURELY a way to make it spend less RAM, I simply can't believe Gnome takes 900 Mb!

Anyway, if it's Gnome's fault... why don't you give a try to other desktops (xfce?) or window managers?

---

### Post by 3ntity on 2006-12-08
> **']Nbx*cmD[ said:**
> 900 Mb!!! Wow! I don't even have that huge amount of RAM to spend! Who says this is reasonable? This might be reasonable if you were using windows vista or similar ram-wasting stuff! 

In my laptop I have 512Mb and when running the GUI i spend less than 5 Mb counting X.org and ratpoison (my wm).

There is SURELY a way to make it spend less RAM, I simply can't believe Gnome takes 900 Mb!
That's 900MB swap used, ~200MB RAM

> Anyway, if it's Gnome's fault... why don't you give a try to other desktops (xfce?) or window managers?

Might just do that... I'm getting fed up with this ridiculous problem, and i have a Kubuntu 6.06 CD lying in front of me... It could become Xubuntu. Or, I may chose to switch back to Ubuntu 6.06. Even if there's a way of downgrading, i guess there'd be no point trying... :@ either way, that'll be the 4th completely fresh Ubuntu install in less than a year's time. :/

---

### Post by robbieatsooke on 2006-12-09
I had very similar nightmare for months,checked all kinds of things including power supply.Finnaly I droped in an extra memary card that was laying arownd and shazam!!! all my problembs became a distant memary.

---

### Post by 3ntity on 2006-12-14
> **robbieatsooke said:**
> I had very similar nightmare for months,checked all kinds of things including power supply.Finnaly I droped in an extra memary card that was laying arownd and shazam!!! all my problembs became a distant memary.

I'm glad that solved the problem for you, but with 1GB RAM already i don't really think adding more RAM will really make that much of a difference. I'm confident many Ubuntu users with less RAM have it running quite a bit better then I do...

---

### Post by andrew frank on 2006-12-18
i have the same problem - ubunty 6.10 ran very nicely - then it slowed to a crawl (5 - 10 minutes to start) on a 1ghz machine. i have automatix installed - is this the cause?

i observe:
- when shuting down, i see the ubuntu screen with the disappearing orange. when it is all gone, then it reappears again and a small piece of orange is disappearing again.

when startup i have /dev/null  open failed...

loading windows manager and nautilus etc. takes very long (several minutes)
afterwards the system is not ready - when i click on places or system-admin-monitor
an indication 'starting monitor' appears, but then disappears without anything happening (the system monitor window does not appear).

i think i have the problem since i tried sleep (failed) and hybernate (seemed to have worked).

i have the impression some tasks i execute later does clean up the problem - but i do not know which one.
any hints (please be specific - i am a beginner with ubuntu)

any help appreciated!
andrew

---

### Post by andrew frank on 2006-12-19
some of the trouble seem to have been solved by uninstalling beagle. (i found error message in its logs). now it started quickly and is responsive. programs start etc.

i wish there were better tools to clean up after a system crash, failed sleep/hibernate etc. and methods to detect errors (error logs are widely spread...)

i hope this helps others as well!
andrew

---

