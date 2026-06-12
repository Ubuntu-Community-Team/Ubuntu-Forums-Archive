---
title: "slow rtorrent"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Geir102 on 2007-12-07
Hi im running rTorrent on a ubuntu server, but when it downloading it makes the whole system realy slow. Any one know whats wrong?

---

### Post by hyper_ch on 2007-12-07
What do you mean by "makes the whole system really slow"?

while rtorrent is running, also run "top" or "htop" on the server (htop must be installed first through the repos). It will show you how much cpu, memory et al. the individual processes are using. That helps to determine whether it's really rTorrent.

---

### Post by Geir102 on 2007-12-07
the system is only slow when rtorrent is running if i stop it it woks fine

---

### Post by hyper_ch on 2007-12-07
And still rtorrent might not be the cause... it just could trigger something else to go haywire...

---

### Post by Geir102 on 2007-12-07
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+ COMMAND
25229 xxxx      15   0  174m  27m  24m S  0.2  3.1   2:40.93 rtorrent

---

### Post by banewman on 2007-12-07
What are the system specs? :)

---

### Post by Geir102 on 2007-12-07
CPU[*                                                                          0.3%]     Tasks: 34 total, 1 running
  Mem[||||#******************************************************************40/884MB]     Load average: 0.15 0.33 0.50 
  Swp[|                                                                      0/2957MB]     Uptime: 05:14:23


Dosent seem to be overloaded.

Its a 1.8 mhz 884mb somthing like that

---

### Post by hyper_ch on 2007-12-07
--> > **hyper_ch said:**
> What do you mean by "makes the whole system really slow"?

---

### Post by Geir102 on 2007-12-07
when im logd inn evry thing is super slow. When i type a command i have to wait for it to show up.

---

### Post by mellowd on 2007-12-07
1.8Mhz?

Could you check again? I'm sure you got this wrong.

---

### Post by Geir102 on 2007-12-07
i just set a limit to the bw and now its all good:-)

---

### Post by nikoPSK on 2007-12-07
I'm sure it's not that that's causing all of this.... I would say maybe reinstall it and if the problem persists when it's uninstalled it's not that.

---

### Post by Geir102 on 2007-12-07
Im have reinstalled it, but its no problem when its not running. But evrything is fine now that i limited the upload

---

### Post by nikoPSK on 2007-12-07
glad to hear it. Please mark this thread as SOLVED

---

### Post by hyper_ch on 2007-12-08
it's a remote box?
Well, that's also good to know because if all upload is used, you can't do much. Limit the upload to abot 90% of your upstream speed.

---

