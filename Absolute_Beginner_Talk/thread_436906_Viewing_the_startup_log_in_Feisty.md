---
title: "Viewing the startup log in Feisty"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by CCIEMD on 2007-05-08
Hi all,

Sorry for the newb question.  On startup, after the splash screen, an initialization checklist scrolls by.  This is only up for a second or two before X starts.  Everything lists "[OK]" along the right side of the screen, however, one entry lists "[FAIL]".

My question is, is this logged somewhere?  It scrolls by too fast for me to see what is failing.  I have tried looking through some of the logs in /var/log, but can't find anything that looks like the same output.  Any suggestions where to look?

Thanks in advance!
Richard

---

### Post by starcraft.man on 2007-05-08
I'm not sure but you may want "boot-chart", its available in the repos and records your boot up in a nice graphic.  Should catch everything, then you can paste the picture here and we can see what the trouble is.

---

### Post by mills on 2007-05-08
ive downloaded boot-chart but how do i use it?

---

### Post by CCIEMD on 2007-05-08
Thanks for the reply.  Is the bootup not automatically recorded in a log?  If not, is there a way to direct the output to a log without installing another app?  If not, I may consider installing boot-chart.

---

### Post by Cypher on 2007-05-08
Unfortunatley no, the boot log isn't saved, the [OK] and [FAIL] are printed dynamically by each of the startup scripts based on their own actions. It would need be nice to have a service status and possible failure logged somewhere.

You COULD take it upon yourself to visit the files in the /etc/init.d directory and add something like 'echo "<service> passed >> /var/log/bootup.log' or 'echo "<service> failed >> /var/log/bootup.log' for now at least.

I know boot-chart will give you a nice listing of times used by each service as your system comes up, but I don't know if it will record failure or success of a particular service..

---

### Post by starcraft.man on 2007-05-08
> **mills said:**
> ive downloaded boot-chart but how do i use it?

When you next reboot your computer, if its installed right it should create a graph of your boot up in 
```

/var/log/bootchart/
```

so you can look there to see how fast it takes ya to boot up :)

RE Cypher: Ya, i forgot about that... not sure if it would record failed processes. Though, maybe if something is causing the problem we will see a long hang time on a specific program? Possible, you never know :)

---

### Post by Cypher on 2007-05-08
I've run Boot-chart before and the graphs will show CPU usage/time but not really anything else. Also, if the service was indeed taking a long time and failing, I woud think the OP would be able to easily see the service name. It looks like whatever is failing is doing so very quickly..

Logging the boot-up services would be a very nice thing..maybe I'll add a feature request for Ubuntu if it isn't there already..

---

### Post by starcraft.man on 2007-05-08
> **Cypher said:**
> I've run Boot-chart before and the graphs will show CPU usage/time but not really anything else. Also, if the service was indeed taking a long time and failing, I woud think the OP would be able to easily see the service name. It looks like whatever is failing is doing so very quickly..

Logging the boot-up services would be a very nice thing..maybe I'll add a feature request for Ubuntu if it isn't there already..

Hmmm, just a thought but maybe it would be easier to get bootchart folks to code in something to catch failed processes? I'm sure the Ubuntu devs have a lot of things to do before that kinda minor thing >.>

---

### Post by Cypher on 2007-05-08
Or better yet..it might be most appropriate for "upstart" to log this info as it's the one that is spawning all the services..

---

### Post by dsb on 2007-07-09
I have found that the binary file in /var/log/boot is somewhat readable in showing some of the bootup services. 

For example when using the command less /var/log/boot, the response is that it may be a binary file. See it anyway? type y and it will show some of those boot up terminal messages.

---

### Post by sciurus on 2007-09-06
Any services that fail to start during boot will hopefully write an explanation to /var/log/messages. If you want to see messages during startup, remove quiet splash from the boot options in grub. You can do this in /boot/grub/menu.lst or by hittting e at the grub prompt during boot.

---

### Post by dunno on 2007-09-06
would dmesg not do the trick?  it prints the output messages of the kernel.

---

