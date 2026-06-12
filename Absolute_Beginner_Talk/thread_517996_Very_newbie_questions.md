---
title: "Very newbie questions"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Ricardo Alcocer on 2007-08-05
Hello all,

I'm very new to Ubuntu and Linux in general, . as I am Windows software developer, slowly moving away from MS.  My hard drive crashed and I decided to make my computer dual-boot, use Ubuntu as my main OS, and use Windows in those cases where it's absolutely necessary.

I already have my computer dual-booting and I'm really happy.  Now, I just need to be able to sync my smartphone (Moto Q running Windows Mobile 5) with Evolution.  

I found many guides, this one ([http://ubuntuforums.org/showthread.php?t=345176&highlight=synce+moto+q](http://ubuntuforums.org/showthread.php?t=345176&highlight=synce+moto+q)) being the one that seems more complete.

Now, that guide says that I need to upgrade my kernel.  my "uname -r" returns '2.6.20-16-generic', and as I understand, I need to go up to 2.6.22.

Being new to Ubuntu, and doing this in my work computer, I don't want to go the "trial and error" route, so I went with the KernelCheck program.  I ran it, answered lots of overwelming and intimidating questions, and had to leave it running overnight...I was too tired to wait.

Next morning  it had finished, so I rebooted.  Computer booted up fine, but it didn't recognized my wireless connection immediately as it did before.  I don't know if I did something wrong during the kernel building process, or if I need to set it up manually, in which case I don't know how to do it.

Anyway, I really need to sync up my phone so I can really use Ubuntu on my day to day.

Any comments?

-R

---

### Post by fimbulvetr on 2007-08-05
Wow. Congratulations on following that guide (mostly). You did a kernel compile, patching and everything. 

Of course, one of the reasons kernel compiling gets a bad name is because of it's complexity - namely the compiling in of drivers for all of your hardware.

If you reboot into your old kernel (Should still show up on the menu, right? 2.6.20?) Does your wireless then work? 

Paste the output of going to Applications->Accessories->Terminal and typing both:

```
dmesg
``` and ```
sudo lsmod
```

Then go back into the kernel you just compibled (reboot into it, 2.6.22) and give the output from the same commands.

We will then be able to tell if your new kernel has support for your wireless card.

---

### Post by Ricardo Alcocer on 2007-08-05
Thanks for replying fimbulvetr.

Here's the output of the commands.

Hope this helps to get me back on track...and figure out if there's something else that I unknowingly messed up.

Thanks.

-R

---

### Post by sep1318 on 2007-08-05
I could be completely wrong, but you might have the wireless module in the new kernel for some reason. I did a diff of the two lsmod files, and I think there was a line in the first and not the second that was something about ieee80211, which is the wireless protocol. I could be completely wrong on most or all of this, granted, but I noticed it and figured I'd point it out, see if it helps.

---

### Post by fimbulvetr on 2007-08-05
> **sep1318 said:**
> I could be completely wrong, but you might have the wireless module in the new kernel for some reason. I did a diff of the two lsmod files, and I think there was a line in the first and not the second that was something about ieee80211, which is the wireless protocol. I could be completely wrong on most or all of this, granted, but I noticed it and figured I'd point it out, see if it helps.

You are exactly right, sep.

His new kernel does not appear to have support for the ipw2200 wireless driver. Unfortunately, this could be for a bazillion reasons, but we can try to narrow it down.

---

### Post by fimbulvetr on 2007-08-05
> **Ricardo Alcocer said:**
> Thanks for replying fimbulvetr.

Here's the output of the commands.

Hope this helps to get me back on track...and figure out if there's something else that I unknowingly messed up.

Thanks.

-R

Ricardo,

I am unfamiliar with KernelCheck but if you're up and running now for the most part it must not be that bad. I'm sorry this is so open ended, but could you try compiling again, this time looking for questions dealing with network, wireless drivers and the intel ipw2200 driver?

FYI: You shouldn't fault ubuntu for this process, it's just that it's only the latest kernel that has support for the device and ubuntu doesn't have that kernel yet. In the next release it will. If you stick within the bounds of packages on ubuntu, things are smooth sailing. Once you build custom pkgs, kernels, someone elses pkgs, the whole ubuntu process is somewhat invalidated and you're on your own for some of it.

PS Thanks for pointing me to this! I have a wm5 phone that I'd love to sync with ubuntu and now I can!

---

### Post by Ricardo Alcocer on 2007-08-05
Hello guys.  First off, thank you for your time.

Let me see if I understand.

The latest kernel version, which Ubuntu has not yet implemented, has the feature I need in order to make my device visible through the USB port.  However, during my kernel update process, I overlooked the part where I should have specified to add the wireless card to the kernel itself.  Now, to see if we're on the right assumption, I should rebuild the kernel, making sure that I do select the wireless card driver.  Is that correct?  Sorry for spelling it out, but I want to make sure that I understand what I'm doing.

I will try rebuilding the new kernel maybe by the end of this coming week or next weekend.  I'm gonna try to setup a workaround using scheduleworld, at least to go through the week.

fimbulvetr, since you're going to try and setup your own WM5 device, would you mind documenting any differences between the walkthrough found and your actuall experience?

Thanks a lot.  I'll get back to the thread shortly.

-R

---

### Post by fimbulvetr on 2007-08-05
> **Ricardo Alcocer said:**
> Hello guys.  First off, thank you for your time.

Let me see if I understand.

The latest kernel version, which Ubuntu has not yet implemented, has the feature I need in order to make my device visible through the USB port.  However, during my kernel update process, I overlooked the part where I should have specified to add the wireless card to the kernel itself.  Now, to see if we're on the right assumption, I should rebuild the kernel, making sure that I do select the wireless card driver.  Is that correct?  Sorry for spelling it out, but I want to make sure that I understand what I'm doing.

I will try rebuilding the new kernel maybe by the end of this coming week or next weekend.  I'm gonna try to setup a workaround using scheduleworld, at least to go through the week.

fimbulvetr, since you're going to try and setup your own WM5 device, would you mind documenting any differences between the walkthrough found and your actuall experience?

Thanks a lot.  I'll get back to the thread shortly.

-R

That's exactly right. Good luck. I don't plan on setting up my wm5 until the new version comes out:) I've done WAY too many kernel compiles to warrant the effort for this. I have linux running on mine (HTC Apache/ UT Starcom 6700) so that's good enough for me!

---

### Post by Ricardo Alcocer on 2007-08-05
Glad I understood everything correctly.

As for Sync of WM5, I just created a free account on ScheduleWorld.com, and installed the WM5 client.  I've already synched everything up the SheduleWorld.  I will now try and setup the SyncEvolution plugin ([http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)), and decide if I should go ahead and rebuild the kernel, or wait until Ubuntu releases it.

I'll report back.

-R

---

### Post by Ricardo Alcocer on 2007-08-05
Ok.  I successfully, after lots of failed attempts, configured SyncEvolution with ScheduleWorld, and installed the Funambol plugin on my phone.  At first my contacts got duplicated, but a little cleanup and re-sync, and everything's synching fine as far as I can see.  

Now, since I decided to keep my old kernel, the one that came with the Ubuntu distribution, I now want to remove the one I compiled myself from the boot manager.  I think they're taking up space on my drive, and I won't really use them.

Is there a way of removing it?

Thanks,

-R

---

