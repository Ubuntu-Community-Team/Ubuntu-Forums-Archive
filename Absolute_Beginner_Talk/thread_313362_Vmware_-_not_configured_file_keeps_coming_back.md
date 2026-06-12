---
title: "Vmware - not_configured file keeps coming back"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by LDRoamer on 2006-12-05
I installed Vmserver on my machine (so I could run windows in Linux) but it keeps putting a file "not_configured" in /etc/vmware. If I delete the file it runs fine but as soon as I exit and reboot the file is re-created. When this file is present vmware will not run until I manually delete the file. Is there some way I can stop this from happening?

---

### Post by nickburns on 2006-12-05
You may want to look at these install instructions for vmware:

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

I have installed this on many systems with no problems, it smell like you have an installation problem to me.

---

### Post by mhancoc7 on 2006-12-05
> **LDRoamer said:**
> I installed Vmserver on my machine (so I could run windows in Linux) but it keeps putting a file "not_configured" in /etc/vmware. If I delete the file it runs fine but as soon as I exit and reboot the file is re-created. When this file is present vmware will not run until I manually delete the file. Is there some way I can stop this from happening?

I had this same problem. Here is how I fixed it.
[http://www.ubuntuforums.org/showpost.php?p=1821789&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1821789&postcount=15)

I hope that helps.

Jereme

---

### Post by LDRoamer on 2006-12-06
Thanks for the pointer. I did have VMPlayer installed but I unistalled it completely. Unfortunately the two files you deleted did not exist on my system so the problem must be else where. I have tried uninstalling and and reinstalling, reconfiguring, dancing around the computer and mumbling incantations but so far nothing has worked. It is properly configured but even though I delete it the file keeps coming back every time I re-boot. Once the file is deleted it runs fine. If I reconfigure it I always get a message that the re-configuration was successful but the problem continues. I am guessing there is still something hanging around somewhere but I don't have enough familiarity with linux to know where or what to look for.

---

### Post by nickburns on 2006-12-06
go to the directory of where the file is you delete and see what the permission settings on the file are.  If you are using the graphical directory view, right click the file and look at the properties.

If you are using the terminal, then run a ls -l on the directory and post back what the results of the file's permission properties are.

My feeling is that maybe vmware cannot delete this file as part of its usual clean up processed during closing.

---

### Post by LDRoamer on 2006-12-06
ls -l returns this:

-rw-r--r-- 1 root root 0 2006-12-06 22:56 /etc/vmware/not_configured

The graphical tool tells me the owner is root.

---

### Post by LDRoamer on 2006-12-06
An update on my "condition".  If I delete the file and don't run the VMWARE program the file will return as soon as I re-boot. If I delete the file I can run the program but as soon as I reboot the file returns. I am in some kind of loop from hell.

---

### Post by dehuszar on 2006-12-19
Anyone figure this out?  I've been having the same problem.

---

### Post by cephlon on 2007-01-09
Yes, I third that. Same issue. Vmware works great, but I have to delete this file each time I reboot into Kubuntu.

---

### Post by cknight725 on 2007-04-02
Yep -- me too ... persistent not_configured file, VMWare Server on Edgy.

---

### Post by weekdaysailor on 2007-09-27
+1 - same in Gutsy

---

### Post by PiEp on 2007-10-26
I have the same problem running Mepis 7 beta4. The problem does not seem to be limited to Ubuntu...

---

### Post by webbsd on 2007-11-03
This worked for me in Gutsy:

[http://www.braincells.com/debian/2004/05/](http://www.braincells.com/debian/2004/05/)

Steve.

---

### Post by webbsd on 2007-11-04
Broke again today. I'm not sure why.

Steve.

---

### Post by langabe on 2008-03-04
In my case the vmware services started by the /etc/init.d/vmware script were not all starting correctly,

```
Starting VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Bridged networking on /dev/vmnet2                                  failed
```

And as a result the script is always touching the /etc/vmware/not_configured file.

I had a working vmware just by not using /dev/vmnet2 but had to modify the vmware script to get rid of the annoying file.

Hope it helps,
Alex

---

### Post by scananza on 2008-05-06
I had the same issue, for what I found out it's due to vmware startup routine starting too soon when ubuntu boots; try the following:

purge actual vmware init scripts:

```
# update-rc.d -f vmware remove 
```

reinsert init scripts at the very end of init process:

```
# update-rc.d vmware defaults 99
```

Hope this works for you too, it fixed for me both in gutsy and hardy

---

### Post by heloma on 2008-06-13
remove vmware from your startup services, reboot your computer and you're done.

heloma.

---

