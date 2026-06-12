---
title: "Ubuntu 6.06 64-bit shutdown problem"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by mmarkvillanueva on 2006-07-10
I've tried Ubuntu 6.06 live CD. The sound (Intel HDA) is now working. I have sound problems from the previous version of Ubuntu (i.e., 5.10). However I still have shutdown problems. Everytime I shutdown from GNOME, the screen turns black and nothing happens next. SUSE 10.0 also has this kind of problem. Ubuntu 5.04 and Slamd64 10.2 do not experience this shutdown problem. How will I fix this? Thanks

---

### Post by lordlollo on 2006-07-10
> **mmarkvillanueva said:**
> Everytime I shutdown from GNOME, the screen turns black and nothing happens next.

Can you be a bit more precise on that?
When you shut your box down, the screen should turn black :p 
Anyway, what happens first? Is the power still on?

---

### Post by mmarkvillanueva on 2006-07-10
When I log-off and select shutdown or restart, GNOME shutsdown and the screen turns black. I think X shuts down giving me a blank screen, a terminal without any prompt. I also tried doing CTRL+ALT+F1 in GNOME so that I'll go to the terminal. When I use shutdown -h now, the shut down process goes on, giving me messages on the screen, after few seconds, a lot of characters (hexadecimals) and error messages were displayed in my screen... so i have no choice but to press the power button in my CPU. :(

---

### Post by lordlollo on 2006-07-10
Sorry, you have to wait for someone smarter than me :oops: 

Good luck...

---

### Post by mmarkvillanueva on 2006-07-10
Everything is doing fine except shutting down :(

---

### Post by Kilz on 2006-07-10
> **mmarkvillanueva said:**
> Everything is doing fine except shutting down :(
Let me guess you have ati radon x200 graphics or another in the radon express family? The shutdown is a bug with the 8.25.18 drivers if you do. [There is a work around.]("http://ubuntuforums.org/showthread.php?t=197471&highlight=fix+fglrx") It is kind of legnthly but its the only way I have found to rid yourself of the black screen and have the drvers work.

---

### Post by mmarkvillanueva on 2006-07-11
there is another thread that has the same issue with me: [http://tinyurl.com/fw3qd](http://tinyurl.com/fw3qd)

anyway, below is my computer specs:

OS: Ubuntu 6.06
CPU: Intel 4 64-bit
Motherboard: ASUS P5GL-MX
Sound: Intel HDA
Video: Intel 82915G/GV/910GL Express Chipset Family (from windows device manager)

---

### Post by absurdist on 2006-07-11
This isn't caused by ati drivers.  We're both using intel i810 drivers and getting this problem.  Has anyone got an ASUS board with onboard intel graphics without this problem?  Is there a workaround for this without screwing up our graphics?

---

### Post by stupidkid on 2006-07-11
What if you type halt in the command line?

---

### Post by mmarkvillanueva on 2006-07-11
sudo halt gives me a lot of messages...
"Unable to handle kernel paging request"

---

### Post by absurdist on 2006-07-11
> **stupidkid said:**
> What if you type halt in the command line?

sudo halt gives me the same result as any other shutdown method

---

### Post by mmarkvillanueva on 2006-07-12
Just tried SUSE 10.1 Live DVD. No shutdown problem :(
How do we fix this in ubuntu? any suggestions from the experts?

---

### Post by mmarkvillanueva on 2006-07-12
just checked distrowatch. suse 10.1 has kernel 2.6.16.13 ubuntu 6.06 has 2.16.15. you think, the kernel has something to do with the issue or there is a way (configuration) to fix the problem?

---

### Post by absurdist on 2006-07-13
> **mmarkvillanueva said:**
> just checked distrowatch. suse 10.1 has kernel 2.6.16.13 ubuntu 6.06 has 2.16.15. you think, the kernel has something to do with the issue or there is a way (configuration) to fix the problem?

Ubuntu just upgraded their kernel.  It didn't solve the problem.

---

### Post by mmarkvillanueva on 2006-07-16
i added acpi=off as a boot parameter before booting the live cd.
There was no shutdown problem when i tried to log-off from GNOME. Except that it didn't shutdown automatically. I have to manually press the power button on the CPU. Any ideas?

---

### Post by absurdist on 2006-07-30
I posted a bug report on this problem:

[https://launchpad.net/bugs/54495](https://launchpad.net/bugs/54495)

If you're having the same problem, add your comments to the report.

---

### Post by mmarkvillanueva on 2006-08-08
check this out: 
[http://www.suseforums.net/index.php?showtopic=21690&st=0&#entry123197](http://www.suseforums.net/index.php?showtopic=21690&st=0&#entry123197)

thanks to pvh513. he found a solution to our problem!

---

### Post by smile-its-smiley on 2006-08-08
I have had the same problem with windows were it didn't want to shut down properly all what id id to fix this problem was update the bios and all works well.

---

### Post by be4truth on 2007-02-13
I installed Ubuntu and Kubuntu dapper 32bit with a 82915G/GV/910GL chipset and have the same problem. Spent already hours on this without success. If I can't find a solution I need to look for some other distro for this machine. The forum help is extensive but in my case it fails - all of it. 
All works fine if I go down with the resolution to 800x600. Everything higher causes either a black screen before the login. With low resolution I get the black screen at logout.
Did someone succeed installating Ubuntu (which?) on 82915G/GV/910GL?

---

