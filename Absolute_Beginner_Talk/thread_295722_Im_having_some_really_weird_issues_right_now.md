---
title: "Im having some really weird issues right now"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-08
Okay well I have been using dapper now for about 2 months and have never had a problem with it yet. Well today I started up my laptop and noticed that it took a bit longer to boot than it usually would. I also see that my wireless has no connection. My wireless card must be supported seeing as ubuntu picked it up right off the bat when I first installed.

Well I tried deactivating the connection and reactivating it again, but with no luck. I then look at my system monitor and see that the CPU is running a full 100%. Something is seriously wrong here and I can't figure it out. I know it's not the modem or the router because this computer I'm typing on now is connected to the same stuff and it's working just fine.

I tried restarting but the CPU always works it's way back up to 100% and stays there, and it still won't connect.](*,)

---

### Post by voodoonirvana on 2006-11-08
Help please?

---

### Post by polly1 on 2006-11-08
Hi 

Try using the command "top" from your terminal and post the results, so that a check can be made which process is causing the 100% CPU and memory.

---

### Post by voodoonirvana on 2006-11-08
Okay well I'm having to type this because with my wireless down on that computer obviously I cant copy and paste.


top - 16:15:22 up 5 min, 2 users, load average: 1.18, 1.13, 0.54
Tasks: 76 total, 1 running, 75 sleeping, 0 stopped, 0 zombie
Cpu(s): 89.8% us, 19.3% sy, 0.0% ni, 0% id, 0%wa, .3% si
Mem: 247732k total, 244760k used, 3492k free, 3516 buffers
Swap: 722884k total, 18772k used, 70411k free, 65392k used


And below that is shows that CheckGmail is using like 98% CPU or something. I tried closing it but it wont change.

---

### Post by voodoonirvana on 2006-11-08
Okay, I got checkgmail closed finally and the CPU speed is back to normal. But now for the wireless. It's still not picking up. Ubuntu knows the card is there because when I take the card out it tells me there is no card. So that's not the issue. It just isn't picking up the signal for some reason.

---

### Post by polly1 on 2006-11-08
Hi 
Re checkgmail, something seems obviously wrong here. have you recently installed this?
 
Try killing the process with with your system monitor. For other readers benefit- System>Administration>System Monitor and right click CheckGmail and click item "Kill Process". This procedure can be dangerous generally as important processes may be lost, so should only be carried out if you know what you are doing.

If successful, reboot, to check that CheckGmail does not run again.
You could try checking this softwares configuration in addition.

The only other solution is to remove it by using the terminal command.

    Sudo rm -rf checkGmail

This will remove the directory and its files.

Perhaps you will then be able to connect to the Internet again.

best of luck

---

### Post by polly1 on 2006-11-08
Hi

Sorry about my latest post- got waylaid.

Suggest you check the forums for information on your wireless problem or await further help because it is outside of my knowledge.

---

