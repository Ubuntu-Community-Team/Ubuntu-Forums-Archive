---
title: "Have I filled up my root partiton with a backup?"
date: 2012-02-22
forum: Any Other OS
---

### Post by gyozu on 2012-02-22
Running a dual boot system Win7 Mint 12 64bit fresh install from CD.

Have a 30 GB partition for /    <dev/sda2>
Have about 600 GB for /home  <dev/sda5>
Have a 750GB external HDD Maxtor onetouch.

Was using Crashplan for Backup. Was not comfortable with it and uninstalled it yesterday.

Yesterday and today, I got a "Volume Filesystem root has on 413.7 mb of disk space remaining"
Gparted Live confirms this

In looking around past threads for full disk problems, I think that crashplan may have written a file to the "/" partition. Possibly when the Maxtor was offline.

How can I confirm this and if I did it, what is the best/safest way to fix it?

Here is an image of Nautilus as superuser
It shows a 22 GB file in media in "/"

---

### Post by Perfect Storm on 2012-02-22
Moved to Other OS/Distro Talk.

---

### Post by sunfromhere on 2012-02-23
Should we become suspicious? I also got a message 2 days ago that root is running out of space, while in fact it shouldn't (20GB for /root, plenty of space left, disk usage analyzer never shows anything, partitioned on 500GB drive for other). Note I'm running Ubuntu currently, will try to boot other Linux distros to check.

---

### Post by jpm100 on 2012-02-25
I'm here because of this problem.

What happened to me is that Crashplan runs before the external drive mounts.  It then forces the creation of a local directory structure the same name of the mounted drive path.  

The drive seems  to mount on user login instead of at boot.  So Crashplan starts working before you login.   When your external drive mounts it create the same name but with "_" appended.  If you go to /media you may see both the mounted drive and the Crashplan created directory.  

I'm here to try to figure out how to mount the drive at boot, instead of login.

Also you basically have to become root to remove the directory structure and files Crashplan created.  

I ran into trouble really quickly as my boot drive is barely big enough for ubuntu.

---

### Post by gyozu on 2012-02-25
Yes, I noticed the problem right away when the morning BU said it needed to transfer 150GB which it had done the day before.

In my case the "_" was added to the External HD.

I had problems running the "Uninstall.sh", in that it did not completely remove the program. I got the uninstall  to work by rerunning the install script and then immediately running the uninstall script.

To remove the large file in root, I shut down my computer, disconnected the 
BU drive for safety reasons, and used gksudo nautilus  to navigate to the directory folder.

I then opened the folder and used Shift delete to rmove the BU files inside and make sure they did not get hidden in the trash folder and then used shift delete to remove the directory folder.

I am sure It could have been done in terminal.

I like Crashplan and was thinking of reinstalling it and making it a manual backup scenario. I don't send my files offsite. 

Let me know what you find.

---

### Post by gyozu on 2012-02-26
> **jpm100 said:**
> I'm here because of this problem.

What happened to me is that Crashplan runs before the external drive mounts.  It then forces the creation of a local directory structure the same name of the mounted drive path.  

The drive seems  to mount on user login instead of at boot.  So Crashplan starts working before you login.   When your external drive mounts it create the same name but with "_" appended.  If you go to /media you may see both the mounted drive and the Crashplan created directory.  

I'm here to try to figure out how to mount the drive at boot, instead of login.

Also you basically have to become root to remove the directory structure and files Crashplan created.  

I ran into trouble really quickly as my boot drive is barely big enough for ubuntu.


I ran across this link that may address the problem, but I am not knowledgeable to confirm this.
Maybe you will have better luck.
[http://blog.jonkeane.com/post/2011/03/08/Towards-a-less-thought,-robust-backup-solution](http://blog.jonkeane.com/post/2011/03/08/Towards-a-less-thought,-robust-backup-solution)

I have not joined the Crashplan forums, but that is on the list for solving this annoyance.

---

### Post by jpm100 on 2012-02-26
> **gyozu said:**
> I ran across this link that may address the problem, but I am not knowledgeable to confirm this.
Maybe you will have better luck.
[http://blog.jonkeane.com/post/2011/03/08/Towards-a-less-thought,-robust-backup-solution](http://blog.jonkeane.com/post/2011/03/08/Towards-a-less-thought,-robust-backup-solution)

I have not joined the Crashplan forums, but that is on the list for solving this annoyance.
I sent an e-mail to support, but they have a warning that their support is behind in responding, and add the fact I'm not a paying customer, I'm not holding my breath.  The forums is probably a better option.

About the above linked solution, I think its looks like it solves the problem.  But has extra stuff since the drive he's looking to mount is encrypted native to linux.  Not savvy enough to know if it works across all distros and pull out the extra stuff right away.  

I think as a quick fix the

**sudo update-rc.d -f crashplan remove**  (<--- had this line incorrect previously)

line will disable the auto run of the Crashplan Engine.  Then you could run the engine manually after you are sure the drive is mounted properly.

**sudo /etc/init.d/crashplan start**

I'm sort of waiting on a reply from crashplan before even trying that. But overall the solution you found seems like it may be a way.

I was more interested in just getting the drive mounted ahead of running crashplan.  I like the idea of just powering on the machine and not needing to login.

---

### Post by jpm100 on 2012-02-28
Well, I'm going down the path of trying to get the drive to mount as opposed to preventing Crashplan from running.  I like being able to power up the machine and not log in and still have Crashplan work.

I'm using ubuntu, so I installed the Storage Device Manager (aka PySDM) which allowed me to add the removable drive to

/etc/fstab.

After a couple of reboots it seems to mount the drive and Crashplan no longer creates a local directory where the mounted drive should be.  However, I'm concerned about permissions.  And CP is not scheduled to execute a backup, yet, to that machine.  So I need to check further.  

However, from what I've read, PySDM is becoming obsolete.  Also the PySDM way adds your external drive to fstab is not reliable.  because the name of your device can change depending on what port your drive is installed in, other devices, etc. 

From what I read, I need to identify the drive in fstab by its uuid.  

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

2nd post in this thread has some good links
[http://ubuntuforums.org/showthread.php?t=1926125](http://ubuntuforums.org/showthread.php?t=1926125)

---

