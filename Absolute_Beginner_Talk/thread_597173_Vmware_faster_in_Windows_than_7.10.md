---
title: "Vmware faster in Windows than 7.10?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by tmcmulli on 2007-10-30
I just got through dual-booting one of my Windows XP Pro machines to 7.10, and I did some extensive testing on running the same VM on both platforms.  My preference is to run 7.10 as the host, and windows as the guest.  Lo and behold, my testing showed that serving files (one of the VMs hosts a FTP site) to be about 180 MB per hour slower...much to my dismay.

So my real question, VMware issue, or Windows vs. Ubuntu issue?  I'm currently bringing up VirtualBox sessions as well, but I'm new to that interface, whereas I know how to move around Vmware images quite easily.

Any help greatly appreciated!

---

### Post by rbprogrammer on 2007-10-30
> **tmcmulli said:**
> 
...
one of the VMs hosts a FTP site
...

just out of curiosity, why would you want the virtual machine to host an FTP??  i use ubuntu as a server, i actually on the verge of installing an FTP on it, and it works great as is.  no need to boot up a virtual machine for me, therefore the server gets the most out of the computer (ie ram and harddrive space)..

---

### Post by rbalfour on 2007-10-30
> **tmcmulli said:**
> I just got through dual-booting one of my Windows XP Pro machines to 7.10, and I did some extensive testing on running the same VM on both platforms.  My preference is to run 7.10 as the host, and windows as the guest.  Lo and behold, my testing showed that serving files (one of the VMs hosts a FTP site) to be about 180 MB per hour slower...much to my dismay.

So my real question, VMware issue, or Windows vs. Ubuntu issue?  I'm currently bringing up VirtualBox sessions as well, but I'm new to that interface, whereas I know how to move around Vmware images quite easily.

Any help greatly appreciated!

What kind of tests did you run?

Do you have a side by side results of these test?

I run a 7.04 server with VMWARE and running a AD / Exchange. According to my users, it is way faster than before. Same hardware was used.

---

### Post by tmcmulli on 2007-10-30
> **rbprogrammer said:**
> just out of curiosity, why would you want the virtual machine to host an FTP??  i use ubuntu as a server, i actually on the verge of installing an FTP on it, and it works great as is.  no need to boot up a virtual machine for me, therefore the server gets the most out of the computer (ie ram and harddrive space)..

Agreed, not the optimum setup yet.  I don't know enough about FTP on Linux to feel secure running my ftp site... so VM allows me to ensure I have a backup ftp site up and running in case of hardware issues...

That's not the issue, the bigger one was the results of the tests.

---

### Post by tmcmulli on 2007-10-30
> **rbalfour said:**
> What kind of tests did you run?

Do you have a side by side results of these test?

I run a 7.04 server with VMWARE and running a AD / Exchange. According to my users, it is way faster than before. Same hardware was used.

Let me preface with this, my intention was to prove the speed benefit so I could ditch Windows as a platform once and for all.  My "perception" on other VMs has been faster performance on the Linux platform, but when I did download tests, that's where the issue started.

My test was done on the same hardware, a single AMD machine running dual boot Win XP Pro SP2 and 7.10 32-bit desktop.  My ftp client was a DOS prompt from the same laptop through all tests.  The file downloaded was the same in all tests, to the same directory on the laptop, deleted after each download.  5 test passes were run on each machine.  The basic difference is 513 Kb/s on the Windows machine running the VM, 463 Kb/s on the Linux machine running the VM.

I always had though Linux faster than XP Pro...now all I've done is create new frustration and variables for myself...my next test is to get a similar FTP site running on my Linux machines (I have a 32-bit and a separate 64-bit 7.10 setup) and do testing there.  But for now, that specific machine is on Windows... and suffers from the blue screen of death intermittently...

---

### Post by HermanAB on 2007-10-30
Well, the VM will be slower since it is sharing the processor with everything else.  A VM does improve security of the systema bit, since it partitions shings, but don't trust that VMs are impossible to breach, so keep working on your firewalls.

There are a number of things that you can do to speed VMware up:
Disable the floppy disk (easy to enable with a click when needed)
Disable the CDROM (easy to enable with a click when needed)
Disable background snapshots (this is an enormous hog)
Install VMware Tools
Enable dual processor mode (if you have a dual core or more)
Allocate the whole virtual disk drive at the beginning (this is an enormous improvement)

If the VM was created with a dynamic disk to begin with then it will be slow as molasses and there is no way to change this.  However, you could create a huge file to force the system to allocate space and grow the VM, and then delete the file.  Things will then be a lot faster.

For a FTP server on Linux, look into proftpd and vsftpd.  Both are easy to configure.

Cheers,

Herman

---

### Post by tmcmulli on 2007-10-30
> **HermanAB said:**
> 

If the VM was created with a dynamic disk to begin with then it will be slow as molasses and there is no way to change this.  However, you could create a huge file to force the system to allocate space and grow the VM, and then delete the file.  Things will then be a lot faster.


Thanks for the tips, I knew some of those...but not the system allocation.  I'm doing VM for portability and backup, not for security.  I keep my files on an external USB drive, and the VM is small, so I can load that VM on whatever machine is still available to me.

My bigger concern/question was about the speed differences between the two, being they're on the same hardware...

---

### Post by tmcmulli on 2007-10-30
While I still need to test on the same hardware, my first proftpd test to a separate client yielded a speed 8 times greater on downloads than anything I've previously seen on my Windows box.

Next test is to do the same test from my Linux partition on the Windows machine to really see the speed difference.  So file transfers from VMs still seem to be slower on 7.10 than on Win XP... but I can live with that, since it's really an unreal situation, right??

Tim

---

