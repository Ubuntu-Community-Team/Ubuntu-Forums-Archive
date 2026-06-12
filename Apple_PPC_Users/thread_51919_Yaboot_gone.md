---
title: "Yaboot gone?"
date: 2005-07-25
forum: Apple PPC Users
---

### Post by mdipi on 2005-07-25
Hey all, I updated OS X recently and now when i reboot, yaboot doesnt show up, it just goes into OSX. 

Is there a workaround for this?

---

### Post by DJ_Max on 2005-07-25
I had the same incident, OS X borked the bootup sequence. Hold down 'option' right after you press the power button. It will show your OS X and Linux partitions.

---

### Post by mdipi on 2005-07-25
[QUOTE=DJ_Max]I had the same incident, OS X borked the bootup sequence. Hold down 'option' right after you press the power button. It will show your OS X and Linux partitions.[/QUOTE]

DJ did you get it to return to normal or did you have to keep going like that? 

I'll try it out, thanks!

---

### Post by DJ_Max on 2005-07-25
[QUOTE=mdipi]DJ did you get it to return to normal or did you have to keep going like that? 

I'll try it out, thanks![/QUOTE]
 Well, shorty afterwards, I bought a new HD, so I haven't got a chance to install Linux again. So when i do, I'll tell you how to fix it.

---

### Post by calum on 2005-07-25
[QUOTE=mdipi]DJ did you get it to return to normal or did you have to keep going like that? 

I'll try it out, thanks![/QUOTE]

Once you've used that method to get back into Linux once, check that your /etc/yaboot.conf file is still there.  Assuming it is, running 'sudo ybin' should regenerate the boot menu for you.

---

### Post by mdipi on 2005-07-25
[QUOTE=calum]Once you've used that method to get back into Linux once, check that your /etc/yaboot.conf file is still there.  Assuming it is, running 'sudo ybin' should regenerate the boot menu for you.[/QUOTE]

Thanks so much guys. Im in Ubuntu right now, and just ran that command, so I'll report back and tell you how it went when i reboot later tonight. 

-Mike

---

### Post by mdipi on 2005-07-25
Worked good as new! 

Thanks so much again!

---

### Post by mdipi on 2005-07-30
[QUOTE=mdipi]Worked good as new! 

Thanks so much again![/QUOTE]
 Seems as though this didnt solve the problem again, it did for a short while, then my Mac went back to booting into OS X right from the get-go again.

Although this does seem like the fix whenever it "breaks".

---

### Post by zxee on 2005-07-31
[QUOTE=mdipi]Seems as though this didnt solve the problem again, it did for a short while, then my Mac went back to booting into OS X right from the get-go again.

Although this does seem like the fix whenever it "breaks".[/QUOTE]

Are you doing "sudo ybin" after you've edited yaboot.conf?
Can you copy and paste your /etc/yaboot.conf  perhaps someone here can
offer suggestions after seeing that.
Another idea would be to check that open firmware is the latest version.

---

### Post by DJ_Max on 2005-08-01
In OS X open terminal, and do:
```

sudo pdisk

```

Then type "L". That'll give your complete HD map. The problem is probably the "Apple_Boot eXternal booter".

---

### Post by daladheri on 2007-08-08
I am having very similar trouble. First of all I have 2 HDs and the 2nd HD (without OS X on it) has 2 main partitions: A Mac OS formatted partition and the Linux partition, linux swap, boot partitions. I changed the formatting of the Mac OS formatted partition to UNIX filesystem in Disk Utility. I reboot my compy and it doesnt show yaboot. It boots OSX. Then I read your suggestions and press option as I boot. I get the apple boot menu and select Linux. It takes me to the yaboot menu wierdly enough. I press "l" and instead of going to linux it goes back to the apple boot menu. I cant get it to boot ubuntu. Please help. I have the yaboot.conf code if your interested. :(

---

### Post by Lord Shank on 2007-08-10
You have to put your partition for linux first, leave it as free space.  The best way to do this is to take a firewire drive, back up os x with super duper, and then boot from that drive.  Go into disk utility, make two partitions.  The top one for linux, leaving it as free space, then the second for os x.  Super Duper your os x install onto the new  hfs+ partition, install linux in the free space, voila.  You will get the yaboot loader everytime.

---

