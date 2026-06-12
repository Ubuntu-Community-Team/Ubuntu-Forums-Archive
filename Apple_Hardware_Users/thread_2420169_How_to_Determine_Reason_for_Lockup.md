---
title: "How to Determine Reason for Lockup"
date: 2019-05-31
forum: Apple Hardware Users
---

### Post by alias5 on 2019-05-31
I am running Ubuntu on an older Mac Mini.  It is being used as a Plex server.  Several times now, it's become unresponsive.  When I touch the top of the Mac Mini, it's very warm.  I haven't been able to reach it via SSH.  I have not been able to wake it up via keyboard nor mouse either.  I've tried Ctrl+Alt+F-keys to reach another terminal.

So, my question is, how can I determine what process is causing this?  At this time, the hardware is still locked up.  Normally, I have to power it off and back on.  But, when I do that, I don't know how to tell which process caused the problem.  Got any idea how to know what has it locked up?  Or, how to access it to run top?  Or, do you have any idea how to turn on debugging?  I suspect the problem is the plex media server.  But, I don't know how to prove it.  Maybe Plex has debug logging.  Hmm.  That's an idea.

You're probably wondering specific versions of everything.  I don't know right now and can't really tell because I left it locked up.  However, it's a recent installation.  I believe it's 19.04, but I'm not positive.  Until this year, I don't believe Apple has changed the mac mini in years.  Mine is about 5 years old.  I can edit this to provide specifics later if required.  But, I believe my question can be answered in generic terms.

TIA

---

### Post by TheFu on 2019-05-31
For a media server, it is probably best to only use LTS releases. After all, you don't want to be installing a new OS every 6 months, right?  So, if it were me, I'd go back to 18.04 and wait until at least 2020 - say September - before considering a move to the next LTS which will be 20.04.  My Plex Server runs on 16.04 and I don't plan to move until 2021-ish.  

I had a Mac Mini with a Core i5 CPU for about 2 weeks. Work. Those are basically NUC systems which always had cooling issues, so you probably want to turn off many of the things that Plex enabled by default which make it hot.  

So, the easy way to get system information is with the **inxi -bz** command.  Run that, post the command AND output inside code tags so everything lines up like it does in the terminal.

Next would be to look at the log files for any issues.  The old way to do that was **sudo egrep  -i 'err|warn' /var/log/*g**  - look for disk issues, hardware issues, overheating/thermal problems.  There's a new-fangled command **journalctl** that will search the binary version of the logs and it is more able to limit to critical, emergency, warnings, boot, .... types of logs.  I haven't needed to learn that.  The issue with log files is that the buffers holding the last message doesn't always get flushed to disk when there is a lockup.  Anyway, you can learn about journalctl and the amazing things it can do by google or checking out the manpage.

So ... ignoring the plex aspects of the system, first, I'm not convinced that the system is really locking up.  Have you tried to ssh in from another system when it happens?  Can you force the issue to happen?  A GUI lockup isn't the same as a full system lockup.  In theory, using a different pty should get around that, but sometimes not. 

If you can make it happen, what do you do to cause it?

Besides hardware faults, running out of real and virtual RAM will cause a system lockup.  Use the **free -hm** command to see it.  **top** can also show it, but with the free -hm, you can easily redirect the output to a file every 5 minutes and watch what happens over time.

Any partitions low/out of space on the system?  Low disk space is bad for every Unix OS. **df -hT** will show that.  We don't need to see any "loop" stuff.  I have this alias for df .... 
```
alias dft='df -hT|egrep '\''^/dev|[:/]/'\'' |grep -Fv loop'
```
 which only shows stuff I care to see. Drop that into your ~/.bash_aliases file if you like it.

GPU drivers.  Do you use the system to actually watch video?  My plex server is a pure server. I never actually watch video on the screen connected to it. It streams to other devices connected to the network around the house and over the internet through my VPN.

Then there's the world of unknown issues.  Look for the plex log and check it for errors and warnings. In the plex web-gui, there are ways to turn up the log level for more detail.  I'd search for it using **locate log|grep plex**
Oh how I hate, hate, hate, the plex programming team.  They insist on putting stuff 50 characters deep for no good reason. Sorta like how Unix people name a command "rm", but Microsoft names it "Remove-Item -Path /full/path/to/the/object/deep/inside/some/subdirectory -Force" in powershell - the plex guys setup their directories like the second one - but much, much, worse.

---

### Post by alias5 on 2019-05-31
Thanks.  Lots of good info there and some things that I can play around with. However, it's really locked up.  I'm looking for a way to access the computer so that I can run some diagnostic commands.  In the past, I've just been doing a hard reset.  But, the problem is that I can't catch the problem.  I have tried SSH and accessing another pty with the Ctrl+Alt+Fkey command.  I gave it a few minutes to respond.  I've found that if you're patient, sometimes the commands get make it through the queue and will eventually get processed.  I am running mine like yours.  I do have an HDMI cable connected to it.  But, I don't watch anything on it directly either.  It's a backend server for my Plex clients.

---

### Post by TheFu on 2019-05-31
> **alias5 said:**
> Thanks.  Lots of good info there and some things that I can play around with. However, it's really locked up.  I'm looking for a way to access the computer so that I can run some diagnostic commands.  In the past, I've just been doing a hard reset.  But, the problem is that I can't catch the problem.  I have tried SSH and accessing another pty with the Ctrl+Alt+Fkey command.  I gave it a few minutes to respond.  I've found that if you're patient, sometimes the commands get make it through the queue and will eventually get processed.  I am running mine like yours.  I do have an HDMI cable connected to it.  But, I don't watch anything on it directly either.  It's a backend server for my Plex clients.

If that is the situation, I'd guess it is low RAM. How much RAM is available and what is the swap use?  Systems running low on total memory, including virtual memory, get slower and slower over time.  My last install, the automatic installer only created a > 1G swap partition. I had lots of issues.  Changed that to 4.1G and haven't seen any issues since.  This is a common issue for me. I've seen it on a few different "desktop" installs.

free -hm
swapon -s


For a pure server, one that isn't used for any GUI, doesn't have any GUI libraries even loaded, then I strive to have no swap necessary as I tune the amount of RAM each system gets. Since those are mostly virtual machines, changing the RAM setting isn't hard.

---

### Post by alias5 on 2019-06-01
Memory, hmm?  I have been suspicious of a runaway process or a memory leak in the Plex code.  But, suspecting it is one thing, verifying is another.  I wish I could catch it when it becomes unresponsive.  As luck would have it, my power went off at my house for no good  reason and powered off the mac (no electrical storms or anything).  Our power really never goes out without something triggering it like a bad storm.  So, I  won't be able to see if my request to get a terminal ever made it  through the queue.  However, I did run the commands you requested.

free -hm
```

backdoc@macmini:~$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           7.7G        1.1G        121M        165M        6.5G        6.1G
Swap:          2.0G          0B        2.0G

```

swapon -s
```

backdoc@macmini:~$ swapon -s
Filename                Type        Size    Used    Priority
/swapfile                                  file        2097148    0    -2



```

I also ran gdisk -l
```

backdoc@macmini:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Model: ST9750420AS     
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 790B27B5-9897-4191-A9DB-1E0924CB3EE6
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 8-sector boundaries
Total free space is 263893 sectors (128.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      1145378815   546.0 GiB   AF00  Untitled
   3      1145640960      1146910719   620.0 MiB   AF00  Recovery HD
   4      1146910720      1157945343   5.3 GiB     8200  
   5      1157945344      1465147391   146.5 GiB   8300  

```

---

### Post by TheFu on 2019-06-01
Well, the memory seems fine at that instant. My plex server uses about 1.5G of RAM, when it isn't transcoding.  Transcoding is memory and CPU intensive.

I've never, ever, used gdisk.  There was a time when it could corrupt disks.  **fdisk** supports gpt the last 5 yrs, so the reason NOT to use fdisk is long ended. Or people use parted and gparted.

swap file? Guess ubuntu decided to change?

Well, if you have any hope of catching the issue, some standard monitoring will be necessary.  I use munin, but lots of people use cacti, zabbix, Nagios or even custom sar scripts.  With monitoring, you'd already have the issue nailed.

---

### Post by alias5 on 2019-06-06
Thanks for your help.  I will have to check out the monitoring tools.

---

