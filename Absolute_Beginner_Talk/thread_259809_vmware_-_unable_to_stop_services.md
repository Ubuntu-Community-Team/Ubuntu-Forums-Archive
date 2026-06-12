---
title: "vmware - unable to stop services"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Izzrit on 2006-09-17
Hello,

I would like to say thanks for all the helpful information I have found on this forum. 

My ubuntu sever lost power the other day and I am trying to startup vmware. I sudo /usr/bin/vmware-config.pl this was not able to stop the Virtual ethernet  service. Do I need to manually stop this service? If I do can some please tell me how to. 

support@srub:/$ sudo /etc/init.d/vmware stop
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
support@srub:/$

-------------------------------

support@srub:/$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

-------------------------------------



Thanks

---

### Post by Izzrit on 2006-09-17
I copied over some additional info thanks, again

---

### Post by daxLeet on 2006-10-17
hey how'd you fix this?  i'm having this problem too

---

### Post by madcow72 on 2006-11-13
I'm looking around to see if anyone has found a fix for this, however for the meantime, (as stupid as this is, it works), you have to restart your computer (2X!) and then invoke this command:```
sudo vmware-config.pl
```
Like I said...stupid.  Every time I shut down my computer, I have to restart it 2X and then re-configure vmware.  Dont' know why.  If I find a fix, I'll come back here and re-post.

---

### Post by ztirffritz on 2006-11-28
Have any solutions for this yet?  I'm having the same problem.

---

### Post by wdaniels on 2006-11-30
Same problem here!  Any solution?

---

### Post by Bachstelze on 2006-11-30
Have you tried simply uninstalling and reinstalling VMWare ? If will just take a minute and won't delete your VMs.

---

### Post by BiggoCharley on 2006-11-30
reboot - and run the config command <sudo usr/bin/vmware-config.pl> before starting vmware again -once its restarted the services can't be stopped without reboot. At least I haven't been able to figure another way to do it.

---

### Post by eilker1917 on 2006-12-02
i have same problem too...

---

### Post by melon2006 on 2006-12-03
Quick fix:

```
sudo gedit /etc/init.d/rc.local
```

and at the end of file add this:

```

#vmware quick fix
vmware-config-network.pl

```


This fix is not perfect (as all quick fixes): it will resets your virtual network settings, but this is small price for get things working. On slower computers you will probably notice a slowdown at system start, script takes few moments to configure.

I hope someone will find a better solution soon :)

---

### Post by mango.muncher on 2006-12-04
This post may help: It helped me.
[http://ubuntuforums.org/showthread.php?p=1842730#post1842730](http://ubuntuforums.org/showthread.php?p=1842730#post1842730)

---

### Post by novocaine7 on 2007-09-23
Hi,

Seemingly related, I was unable to run vmware-config-network.pl, receiving:

james:~$ sudo vmware-config-network.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

the solution is to kill vmnet-natd, which apparently the perl script is too dumb to do itself!

james:~$ ps -e | grep 'vm'
 6085 ?        00:00:00 vmnet-natd
james:~$ sudo kill 6085

hope this helps

---

### Post by sopvkore on 2007-09-27
I had the same problem (could not stop vmware service). The reason was that I upgraded from vmware player 1.04 to 2.0. See the folloving post:
[http://www.debuntu.org/vmware-server-not-starting-after-reboot](http://www.debuntu.org/vmware-server-not-starting-after-reboot)

Valentin

---

### Post by dmizer on 2007-10-12
> **sopvkore said:**
> I had the same problem (could not stop vmware service). The reason was that I upgraded from vmware player 1.04 to 2.0. See the folloving post:
[http://www.debuntu.org/vmware-server-not-starting-after-reboot](http://www.debuntu.org/vmware-server-not-starting-after-reboot)

Valentin

fixed me ... thanks.

---

