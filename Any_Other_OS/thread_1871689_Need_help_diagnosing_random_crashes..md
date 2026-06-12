---
title: "Need help diagnosing random crashes."
date: 2011-10-29
forum: Any Other OS
---

### Post by LinuxFan999 on 2011-10-29
I have a Laptop running Windows 7 which is experiencing random crashes.
 
Here are the specifications:
Make/Model: Gateway MX8738
CPU: Pentium dual core @1.73 GHZ
RAM: 2 GB DDR2-667
HDD: 160 GB SATA
Graphics: Intel GMA 945/950
Display: 17 inch 1440x900
Current OS: Windows 7 SP1
 
This computer origionally came with Windows Vista and only 1 GB of RAM.
 
Here are the 3 main problems I am having:
1. When Internet explorer crashes, the entire system sometimes locks up- especially when a lot of tabs are open.
2. Internet explorer sometimes crashes while trying to close it.
3. Random BSODs which I can't read because the text is compressed at the top opf the screen.
 
A secondary problem:
4. Long boot and shutdown times. about 1 min 30 sec for boot, and 35-45 sec for shutdown. Shutdown hangs where the system quits open/hung programs before clearing the desktop and shutting down, but no programs are open when I shutdown.
 
Problems 1, 2, and the first half of #4 happened with Vista too, but problem #3 and the second half of #4 only occurs with Windows 7.
 
I would like some help diagnosing these problems, because i can't get a new laptop right now, and I should diagnose the problems untill I get a new laptop.
 
Things I have already done, and their results:
Virus scan. Result: no viruses
Check disk. Result: Clean filesystem. No errors. No bad blocks.
 
Remember that the crashes i experience occur at random times (problems 1, 2, and 3), but problem 4 occurs on every boot and shutdown.
 
I am personaly thinking that this laptop may have bad hardware, but I would like to here what you think, including suggestions for software to test the hardware with.

---

### Post by BillyBoa on 2011-10-29
You should try reinstall win explorer or upgrade to win explorer 9, just to see if it's working better.

---

### Post by BillyBoa on 2011-10-29
And something more, just clean the computer with something like ccleaner and remove from autostart all the junk programs installed  making startup slower. Defrag the hard drive.
In any case your computer resources aren't sufficient to work with Win7. It needs more than 1g RAM on idle.

---

### Post by 2F4U on 2011-10-29
Since you upgraded memory did you replace the existing memory or just add modules? Did you already run a memtest?

---

### Post by mips on 2011-10-29
Check the hard drive for defects (bad sectors), use MHDD.
Run diagnostics on the hardware using Microscope diagnostics suite.
If the above come up clear then format & reinstall Win7

---

### Post by LinuxFan999 on 2011-10-29
> **BillyBoa said:**
> You should try reinstall win explorer or upgrade to win explorer 9, just to see if it's working better.
This laptop is currently running Internet explorer 9, and upgrading from IE8 did not help at all. IE9 also uses more memory. 
> **BillyBoa said:**
> And something more, just clean the computer with something like ccleaner and remove from autostart all the junk programs installed making startup slower. Defrag the hard drive.
In any case your computer resources aren't sufficient to work with Win7. It needs more than 1g RAM on idle.
There is only 2 items in the startup folder, which I installed myself. I have already tried defragmenting the hard drive, but that didn't help ether.
> **2F4U said:**
> Since you upgraded memory did you replace the existing memory or just add modules? Did you already run a memtest?
The existing modules were replaced. I upgraded the memory before installing Windows 7. I have considered running memtest, but I don't think this is a memory issue, since 3 of the 4 problems I am having also happend with Vista, which was what I used before upgrading the memory.

---

### Post by Blaqksheep on 2011-10-29
Hi there.  I'm an A+ Certified Tech with expertise in Windows OS.  

First, let me establish that while the tools included in "Windows Tune-Up Tools" like CCleaner, Glary Utilities, etc are useful in maintaining a healthy computer, their effects on computer performance are often minimal.  Registry Cleaners are, by far and wide, the most overrated tool on the market.  Windows NT based systems (such as XP, Vista, and 7) aren't affected in any noticeable way with broken or unused keys.  The only time your registry can cause a problem is if a virus has added a key, if a key an application needs is broken, or if a key needed by the OS is removed (which can be the fault of a virus OR a vaunted registry cleaner).

If you're comfortable, let me guide you through a manual diagnostic.

-----

1)  Shut your computer completely down and Reboot into Windows 7.
2)  Immediately after your desktop appears, hit CTRL + ALT + Del and launch taskmanager.
3)  Switch to the "Processes Tab" and hit "Show processes from all users" in the bottom left corner of the window.
4)  Click the column divider label that says "CPU" until it shows the highest usage processes first (Should require two clicks).
5)  Ignoring System Idle, make a note of the top 5 processes and post them here.
6)  Leave taskmanager open and let your computer idle for 5 minutes.
- This step allows services set to "Delayed Start" time to come online
7)  After 5 minutes, click the "Memory" column label until it shows your highest usage first.
8)  Make a note of the top 10 processes and post them here.
9)  Open IE9 and make a note of how much memory it utilizes at launch.
10)  Let it idle for 10 minutes.
11)  Make a note of how much memory its using now.
- This step will reveal a possibly memory leak.
12)  Hop over to the performance tab and post the total/average Memory and CPU usage (% and/or bytes).

-----

The first 12 steps will give me a general idea of the state of the software on your computer.  If there are no anomalies here, we'll go on to a manual hardware diagnostic.

---

### Post by LinuxFan999 on 2011-10-30
> **Blaqksheep said:**
> Hi there. I'm an A+ Certified Tech with expertise in Windows OS. 
 
First, let me establish that while the tools included in "Windows Tune-Up Tools" like CCleaner, Glary Utilities, etc are useful in maintaining a healthy computer, their effects on computer performance are often minimal. Registry Cleaners are, by far and wide, the most overrated tool on the market. Windows NT based systems (such as XP, Vista, and 7) aren't affected in any noticeable way with broken or unused keys. The only time your registry can cause a problem is if a virus has added a key, if a key an application needs is broken, or if a key needed by the OS is removed (which can be the fault of a virus OR a vaunted registry cleaner).
 
If you're comfortable, let me guide you through a manual diagnostic.
 
-----
 
1) Shut your computer completely down and Reboot into Windows 7.
2) Immediately after your desktop appears, hit CTRL + ALT + Del and launch taskmanager.
3) Switch to the "Processes Tab" and hit "Show processes from all users" in the bottom left corner of the window.
4) Click the column divider label that says "CPU" until it shows the highest usage processes first (Should require two clicks).
5) Ignoring System Idle, make a note of the top 5 processes and post them here.
6) Leave taskmanager open and let your computer idle for 5 minutes.
- This step allows services set to "Delayed Start" time to come online
7) After 5 minutes, click the "Memory" column label until it shows your highest usage first.
8) Make a note of the top 10 processes and post them here.
9) Open IE9 and make a note of how much memory it utilizes at launch.
10) Let it idle for 10 minutes.
11) Make a note of how much memory its using now.
- This step will reveal a possibly memory leak.
12) Hop over to the performance tab and post the total/average Memory and CPU usage (% and/or bytes).
 
-----
 
The first 12 steps will give me a general idea of the state of the software on your computer. If there are no anomalies here, we'll go on to a manual hardware diagnostic.
I did all 12 steps and here are the results:
 
Top 5 processes immediately after boot:
explorer.exe
taskmgr.exe
svchost.exe
wmpnetwk.exe
dwm.exe
 
Top ten processes by memory usage after 5 minutes:
MsMpEng.exe - 31,948k
svchost.exe - 27,624k
svchost.exe(2) - 7,904k
explorer.exe - 5,844k
spoolsv.exe - 5,844k
dwm.exe - 7,788k
svchost.exe(3) - 4,816k
svchost.exe(4) - 4,528k
sidebar.exe - 3,676k
svchost.exe(5) - 2,812k
 
IE9 memory usage at launch: 25,332k
IE9 memory usage after 10 minutes: 25,256k
 
Used memory: 650MB
Used memory+cache: 1,374MB
 
Average CPU usage: 2%

---

### Post by Blaqksheep on 2011-10-30
Interesting.  You did an upgrade from Vista to 7, not a fresh install I see.

MsMpEng.exe is used by Windows Defender for Windows Vista.  It's not used in 7 as far as I know, but it's not obtrusive enough to kill you.

I have a strong hypothesis.

According to Gateway's Website, your HDD is using the AHCI driver.  This is normally a good thing.

Run one more test for me.

1)  Go to Start Menu > Right click Computer > Manage > Device Manager.
2)  Look for any devices that are unidentified, have yellow deltas, or have a red x and let me know if there are any
3)  Then locate IDE ATA/ATAPI Controllers and tell me what's there.
4)  THEN locate Storage Controllers and tell me if there is anything with the term "RAID".

Here's my hypothesis.  The reason Vista took over a minute to boot is because it had 1 GB of DDR2 RAM to work with.  DDR2 on average operates at about half the average speed of current DDR3 modules and by only having 1 GB, the system had to acquire, dump, then reacquire the OS during boot.  You can alleviate this problem using SD cards or USB Flash Drives and Windows Ready Boost but it's not the same.  You still have the same problem with Windows 7 with 2 GB of RAM.

As much as I hate to say it, if you're not in the market for a new laptop yet, go ahead and drop $40 on upgrading to 4GB of DDR2 RAM.  [This](http://www.newegg.com/Product/Product.aspx?Item=20-161-339&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=4&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=%28keywords%29#scrollFullInfo) is a fairly inexpensive pair of 2GB sticks with 800MHz clock rates, faster than the 667MHz on what you have now.

The other possibility is your SATA drive is being bottlenecked by a RAID controller with AHCI.  I'll know when you post results.  =)

The reason IE9 crashes with tabs open is actually because of something known as the Desktop Window Manager (dwm.exe).  If you have the default Aero or effects settings, then that's a major contributer.  IE9's tabs are actually individual windows.  The benefit to this is that each page you have open has it's own environment and allows you to integrate them neatly WITH Windows.  The drawback is that each tab, especially with its support for so many different protocols and code, means that each tab you open eats deeper and deeper into your memory by itself, and then when its done eating your RAM, it gives the leftovers to dwm.exe to eat which is very well explained [here](http://www.howtogeek.com/howto/windows-vista/what-is-dwmexe-and-why-is-it-running) (I'm lazy).

That said, if you don't mind the boot times, disable as many Windows Aero effects as you can and still be happy with the looks (there are only a few of the dozen or so checkboxes that are needed for it to look like Aero, the rest are bonus gravy) and switch to a lighter web browser like Mozilla Firefox, or if you're feeling squirrelly, try [Opera](http://www.opera.com/).

---

### Post by LinuxFan999 on 2011-10-30
> **Blaqksheep said:**
> Interesting.  You did an upgrade from Vista to 7, not a fresh install I see.

MsMpEng.exe is used by Windows Defender for Windows Vista.  It's not used in 7 as far as I know, but it's not obtrusive enough to kill you.

I have a strong hypothesis.

According to Gateway's Website, your HDD is using the AHCI driver.  This is normally a good thing.

[B]Run one more test for me.

1)  Go to Start Menu > Right click Computer > Manage > Device Manager.
2)  Look for any devices that are unidentified, have yellow deltas, or have a red x and let me know if there are any
3)  Then locate IDE ATA/ATAPI Controllers and tell me what's there.
4)  THEN locate Storage Controllers and tell me if there is anything with the term "RAID".[/B]

Here's my hypothesis.  The reason Vista took over a minute to boot is because it had 1 GB of DDR2 RAM to work with.  DDR2 on average operates at about half the average speed of current DDR3 modules and by only having 1 GB, the system had to acquire, dump, then reacquire the OS during boot.  You can alleviate this problem using SD cards or USB Flash Drives and **Windows Ready Boost** but it's not the same.  You still have the same problem with Windows 7 with 2 GB of RAM.

As much as I hate to say it, if you're not in the market for a new laptop yet, go ahead and drop $40 on **upgrading to 4GB of DDR2 RAM.**  [This](http://www.newegg.com/Product/Product.aspx?Item=20-161-339&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=4&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=%28keywords%29#scrollFullInfo) is a fairly inexpensive pair of 2GB sticks with 800MHz clock rates, faster than the 667MHz on what you have now.

The other possibility is your SATA drive is being bottlenecked by **a RAID controller** with AHCI.  I'll know when you post results.  =)

The reason IE9 crashes with tabs open is actually because of something known as the Desktop Window Manager (dwm.exe).  If you have the default Aero or effects settings, then that's a major contributer.  IE9's tabs are actually individual windows.  The benefit to this is that each page you have open has it's own environment and allows you to integrate them neatly WITH Windows.  The drawback is that each tab, especially with its support for so many different protocols and code, means that each tab you open eats deeper and deeper into your memory by itself, and then when its done eating your RAM, it gives the leftovers to dwm.exe to eat which is very well explained [here](http://www.howtogeek.com/howto/windows-vista/what-is-dwmexe-and-why-is-it-running) (I'm lazy).

That said, if you don't mind the boot times, disable as many Windows Aero effects as you can and still be happy with the looks (there are only a few of the dozen or so checkboxes that are needed for it to look like Aero, the rest are bonus gravy) and switch to a lighter web browser like Mozilla Firefox, or if you're feeling squirrelly, try [Opera](http://www.opera.com/).
I actually am not near this computer right now, but I remember looking through the device manager, and seeing 2 devices with yellow symbols next to them: a mass storage controller, and an HP C309 printer (4 instances for 1 printer, which is weird. using Readyboost might be a possibility. This computer is actually maxed out at 2GB, so I cannot add more. This laptop also does not have a RAID controller, just a standard Intel SATA controller for the hard drive, and a PATA controller for the DVD drive. I could disable some aero effects. I do have Firefox and Google Chrome installed, but I don't use them very much. I may switch to Chrome on this computer, since it is much more stable than Internet Explorer.

---

### Post by mips on 2011-10-31
> **Blaqksheep said:**
> 
Here's my hypothesis.  The reason Vista took over a minute to boot is because it had 1 GB of DDR2 RAM to work with.  DDR2 on average operates at about half the average speed of current DDR3 modules and by only having 1 GB, the system had to acquire, dump, then reacquire the OS during boot.

No offence but that's a load of nonsense.

---

### Post by Blaqksheep on 2011-10-31
That storage controller's missing driver is probably the problem with boot time.  Just right click it and reinstall the driver from device manager if you can, otherwise go [here](http://global-download.gateway.com/GDFiles/Driver/AHCI/AHCI_Intel_6.2.0.2002_Vistax64Vistax86_A.zip?acerid=634182981218794780&Step1=NOTEBOOK&Step2=MX%20SERIES&Step3=MX8730&OS=ALL&LC=en&BC=GATEWAY&SC=PA_6G) and manually install it.  That link is directly to Gateway's own driver support website.  The fact that you haven't mentioned problems with Ubuntu's boot time leads me to believe that it's able to properly recognize your storage controller, while 7 is in need of some help.

You're on your own with the HP Printer (not a fan of them) but that should at least hopefully solve the boot problem.

As for disabling Aero settings, there are a few that you'll probably never even notice (like Mouse and Window Shadows) that are gone, but they also make minuscule differences.


mips please don't take a segment of my post out of context if you plan to critique it.  While I admit, this isn't the cause of his boot grief, it does contribute to the IE9 issue.  If you want to critique me, then explain your reasoning, otherwise PM me next time so we can discuss it.

Not even on the subject of boot [here's](http://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) why Windows 7 has such high memory usage and why use of ReadyBoost is actually helpful.

Ultimately though, he's not going to see rocket speeds with that computer.  He knows that as well as we do.  The goal is only to ensure that his computer sufficiently meets his expectations.

---

### Post by LinuxFan999 on 2011-10-31
> **Blaqksheep said:**
> **That storage controller's missing driver is probably the problem with boot time.**  Just right click it and reinstall the driver from device manager if you can, otherwise go [here](http://global-download.gateway.com/GDFiles/Driver/AHCI/AHCI_Intel_6.2.0.2002_Vistax64Vistax86_A.zip?acerid=634182981218794780&Step1=NOTEBOOK&Step2=MX%20SERIES&Step3=MX8730&OS=ALL&LC=en&BC=GATEWAY&SC=PA_6G) and manually install it.  That link is directly to Gateway's own driver support website.  The fact that you haven't mentioned problems with **Ubuntu's boot time** leads me to believe that it's able to properly recognize your storage controller, while 7 is in need of some help.

You're on your own with the HP Printer (not a fan of them) but that should at least hopefully solve the boot problem.

As for disabling Aero settings, there are a few that you'll probably never even notice (like Mouse and Window Shadows) that are gone, but they also make minuscule differences.


mips please don't take a segment of my post out of context if you plan to critique it.  While I admit, this isn't the cause of his boot grief, it does contribute to the IE9 issue.  If you want to critique me, then explain your reasoning, otherwise PM me next time so we can discuss it.

Not even on the subject of boot [here's](http://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) why Windows 7 has such high memory usage and why use of ReadyBoost is actually helpful.

Ultimately though, he's not going to see rocket speeds with that computer.  He knows that as well as we do.  The goal is only to ensure that his computer sufficiently meets his expectations.
The storage controller I was referring to is actually the controller for the built in memory card reader, not the AHCI controller. I have tried reinstalling the printer driver, but it seems to keep uninstalling itself. By the way, I have never run Ubuntu on this computer, but I think I will burn a Cd of it and use it to see how Ubuntu runs in comparison to Windows 7.

---

### Post by LinuxFan999 on 2011-11-05
I tried disabling several minor Aero effects, but I am noticing no difference. Any other ideas?
 
**Update #1: **Youtube has started to become somewhat unreliable on this computer, giving a message saying "an error has ocurred. please try again later." at random. I don't know whether this is a site problem or a computer problem.

---

### Post by LinuxFan999 on 2011-11-14
Do you have any other Ideas?

---

### Post by LinuxFan999 on 2011-11-27
I also disabled the sidebar, but this compter is still too slow.

---

### Post by LinuxFan999 on 2011-12-17
I will mark this thread as solved since I just got a new computer last night. I probabaly won't be doing much with the old one now.

---

