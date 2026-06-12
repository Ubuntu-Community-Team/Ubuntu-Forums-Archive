---
title: "How to get wireless to work with Ubuntu Live CD 10.04 on PB G4?"
date: 2010-05-17
forum: Apple Hardware Users
---

### Post by G33shooter on 2010-05-17
So I have been testing out the Ubuntu Live CD 10.04 on my PowerBook G4 and most everything seems to be working fine (with the exception of wireless and the dim/brighten buttons.)  When connected to the internet via ethernet cable, I was able to download the broadcom hardware (I guess needed to make wireless work??)  This is pictured below.  However, even after the hardware thing was activated, when I unplugged the ethernet cord and clicked on the icon for wireless internet under wireless, it says, "Device not ready."  Any tips? Can you get wireless to work with the live cd?

[IMG]http://i3.photobucket.com/albums/y64/mywytefeet/linuxWirelessIssue.png[/IMG]

---

### Post by Ravernomina on 2010-05-18
Hey :D!!!!

Do This Code and tell me the results Please 
```
lspci
```
```
uname -a
```

Once done try a Reboot of your Computer. I Think the Driver just needs a Reset

---

### Post by G33shooter on 2010-05-18
So, I ran the live cd again.  plugged the ethernet chord in and downloaded/activated the new driver (doesn't activate without ethernet plugged in.)  Then I ran the code you told me to.  What printed out in terminal is below.  I then unplugged the ethernet chord and under wireless it still says "Device not ready."  I then restarted the live cd and it was back to square one--comp told me there was a new driver ready (the same broadcom driver I activated before.)

My thinking is this, I can't really restart and run the live cd again because anything I do (such as download a driver) really isn't saving to my HDD since everything's running off the live cd, correct?  So essentially, every time I restart the live cd, I am starting over.  


[IMG]http://i3.photobucket.com/albums/y64/mywytefeet/code.png[/IMG]

On a side note, is it true with the ubuntu installer, you can choose to partition the drive so that I can dual boot OS X and Ubuntu 10.04?  If I could dual boot OS X and Ubuntu, would there be a screen when I turn on the comp asking whether I want to boot into OS X or Ubuntu?  Also, assuming I could partition my drive to have Ubuntu too, how many partitions are needed? and what are they called, and how much space should be for each one?

Here are my specs:

12" Aluminum PowerBook G4
Mac OS X 10.4.11
1.5 GHz PowerPC G4
1.25 GB DDR SDRAM
Macintosh HD:
Capacity:    74.41 GB
Available:    46.22 GB
Writable:    Yes
File System:    Journaled HFS+
BSD Name:    disk0s3
Mount Point:    /

Based on my specs, could you give me advice on how you would dual boot OS X and Ubuntu and how you would allocate space for each partition etc.?

Thanks for all the help.  My thinking is as long as I can dual boot, I'll worry about wireless internet on the Ubuntu side later.


> **Ravernomina said:**
> Hey :D!!!!

Do This Code and tell me the results Please 
```
lspci
``````
uname -a
```Once done try a Reboot of your Computer. I Think the Driver just needs a Reset

---

### Post by Saul Perdomo on 2010-05-18
Hi guys, I'm in the same situation as the OP, I also have a PowerBook G4 here with an Airport card and the wireless only lists the available networks, but doesn't connect when selecting one.

At the moment this is my only computer, and I would be thrilled to get wireless to work in Ubuntu, I really really miss linux. Ravernomina, please let me know if you think of something else I could try out ok? I don't want to install it yet if I can't be sure I'll be able to use it -- since I only have wireless access, an ethernet cable is not an option.

And if anyone knows the answer to G33shooter's last question please share it, I'll still need to have OS X in this old girl for the wife's Adobe products..

---

### Post by G33shooter on 2010-05-19
Here's an update on what's going on:

I figured out how  to dual boot OS X and Ubuntu 10.04.  I just shrunk my HDD with OS X and during the install process of Ubuntu, chose the option to install to the largest continuous free space.  Everything worked fine after restart.  After messing around for a while I was told there was an update for my broadcom driver (at the moment, wireless wasn't working.)  I updated, and restarted.  After restart, Ubuntu would only show  text for a split second then crash to a black screen.  Tried everything but couldn't get Ubuntu back.  Then I reinstalled Ubuntu a 2nd time off the live cd--worked fine again. Prior to installing the broadcom driver, I messed around after a restart--fine.  Did a couple of power downs to test if it would reboot perfectly--done deal--everything worked fine.  Then I installed the broadcom driver again, same problem.  After reboot--text, then black screen.  Couldn't get back into Ubuntu again.  This lead me to believe there is something up with my computer when I install the broadcom hardware.  I decided to try installing Xubuntu the third time to see if anything was different.  Install was fine. Updates were fine.  Restarts were fine.  Sound doesn't work at all.  I just installed the broadcom hardware update and low and behold--it works!  I am using Xubuntu 9.04 with the working broadcom hardware update.  Sound still doesn't work, and brightening/dimming the screen doesn't work.  Besides that, Xubuntu seems to be working fine.  The kicker is, I haven't restarted after the broadcom update.  I will restart now and let you know if I am back in Xubuntu or OS X in my next post.  Hopefully this works!

---

### Post by G33shooter on 2010-05-19
Welp, after restarting, I am still good to go!  Wireless works great!  Restarts are no problem--yaboot asks me if I want to boot OSX or Xubuntu.  OS X still works great!  The only two issues I haven't figured out yet are how  to make sound work in Xubuntu 9.04 with my PB G4 and how to make dim/brighten work for the screen.  Other than that, things are not half bad.  I got swf-player (I beleive that's what it's called) to play flash--does an *okay* job--wish it was a bit better. Now I just need sound (hell I could even live without the dim/brightening.)

---

