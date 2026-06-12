---
title: "No Boot after installing update"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by alanphil on 2007-07-19
I'm running Dapper (6.04) on a server. This machine has been running for over a year with no problems. This morning there was a kernel upgrade available, which I installed [going from kernel 2.15-27 to 2.15-28]. 

The upgrade proceeded normally until the install scripts threw an error and the process halted. I took a quick look in the terminal to see the error. I think it was related to a file not being writable. The upgrade process hung  and after five minutes I rebooted.

Now when I boot I see the following:

> Uncompressing Linux... Ok, booting the kernel.
WARNING: Couldn't open directory /lib/modules/2.6.15-27-686: No such file or directory
FATAL: Could not open /lib/modules/2.6.15-27-686/modules.dep.temp for writing: no such file or directory

The boot process stops at this point. Notice that the error message is referencing the 2.6.15-27 kernel, but the new kernel is 2.6.15-28. How do I fix this? :confused: This machine is my test web server and I really need to get it working again if at all possible. Any help greatly appreciated!  

Alan

---

### Post by louieb on 2007-07-20
For now you should have the option to boot the old kernel. Press escape just as grub starts to get the grub menu. Then it just a matter of fixing you menu.lst file. 
Any problems get back and I'll try to point you in the right direction. 
Probably just need to restart the update. But right now can't remember how.

---

### Post by mmichalik on 2007-07-20
I had the very same issue this morning.

My server has been running for 6 months, just fine.  I installed the gnome desktop on it as well.  This morning, I upgraded the kernel to version 2.6.15-28-server.  The upgrade appeared to go fine but when I rebooted I get the following:


Cannot start X
server (your graphical environment)
due to some external error
Please contact your system administrator
or use syslog to diagnose........


So, I am forced to a command line login.  When I put in my user name and password, I get the following:

No Directory, logging in with the home=/
--bash: no job control in this shell
--bash: cannot create temp file for here document: Read-only file system.

Is there any way around this or am I hosed?  This server is my NFS mount and the data is very important to us.

Any help would be GREATLY appreciated.  

Oh, and I have looked at the syslog but, nothing is standing out as an issue in there.

---

### Post by alanphil on 2007-07-20
Hey mmichalik, sounds like we have the same problem. My file system is now read-only also. Today I tried cleaning up the file system by running e2fsck, per the discussion at the following website:

[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

This process identified lots of problems, and was set to fix the issues. After this process, when I ran the basic

> e2fsck -C0 -p -f -v /dev/hda1

it still reported issues with the file system. 

This server is used as my work test server, so I really would like to get it working again if possible. Seems odd that there are not more people talking about this issue. Maybe there are not too many still using Dapper as a server? Or they are wise sys admins and don't apply kernel updates! :) 

I'm going to tinker with this problem for awhile longer and will post if I have a fix. If no fix I will probably go to slackware on this work server.

OH mmichalik -- I should mention that if you use a Dapper CD to boot you will be able to see all of the data on your server. I was getting odd permission issues when I attempted to copy files from the hard drive -- but there is possibly a way around that if you need to retrieve files.

---

### Post by mmichalik on 2007-07-20
Thanks for the update!

I hope that it's recoverable because of the NFS mount situation.

I will check the link out and see if anything helps me out as well.  If it does, I will post it for you to look at.

Thanks!

---

### Post by mmichalik on 2007-07-20
running the e2fsck -C0 -p -f -v /dev/md0 (and also on /dev/sda1) came back with no errors.

---

### Post by alanphil on 2007-07-20
If you're not getting any errors that's great! I think the trick now is figuring out how to remount the file system so it is read and writable. The following link discusses this issue, but I have no luck with this approach. I need to do some research on this....

[http://www.unixguide.net/linux/faq/04.15.shtml]("http://www.unixguide.net/linux/faq/04.15.shtml")

---

### Post by mmichalik on 2007-07-20
ok, something strange just happened.

the mount -n -o remount / did not mount the file systems 100%.  It did take the file system out of read only mode  though.  At least I think that's what took it out of read-only mode, which I find very strange.  

So, I tried the mount -n -o remount -t ext2 /dev/md0 / and it reported that I did not have an FSTAB file.  I, for some reason, had a back up made on the 11th of this month called fstab.old and I was able to copy it over and now, I can at least boot up to the desktop login.

I lost my home directories though, so I jumped on a desktop machine, ssh'ed into the server and created a new home directory for my user and chown'ed it over to the right user:group

I can at least get to the desktop of my user.  Which is a MAJOR milestone.  

Thank you for all the help and directions.  I really, really appreciate it.  I can at least now get the NFS files off of the machine and, worst case just do a complete re-install of the system.

I'm ordering the back up server next week.  I was lazy and have put it off because there was always something better to do but, this really put the fear of the Ubuntu God in me.

---

### Post by alanphil on 2007-07-26
A quick update -- my problem ended up being a hard drive that was going into a death spiral. I guess it started to fail just when I installed the kernel update but the drive had enough life to make it appear that the problem was in the file system. 

I knew something was odd when I did a clean install and the machine kept acting flaky. Finally I threw another hard drive in the machine and did another clean install. Problem solved! :)

Alan

---

