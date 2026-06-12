---
title: "Help: How do I backup &amp; restore apps &amp; settings between Ubuntu containers"
date: 2019-05-19
forum: Any Other OS
---

### Post by jdrch on 2019-05-19
Problem: I run Linux on DeX on my Galaxy Note9 (Android 9.0). Unfortunately, there [doesn't seem to be any way of updating the container version in-place]("https://www.reddit.com/r/LinuxonDex/comments/bdztgj/how_do_i_update_my_lod_container_inplace_from_v15/"). 

Therefore, I'm trying to transition from v015 of the container image provided by Samsung to v016, but I'd rather not have to set up my apps and settings from scratch in v016. I'd like to backup my v015 apps and settings and restore them to v016.

Anyone have a clue how to do this? I followed [these instructions]("https://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages") and literally the only thing that carried over was my apt sources. Settings, etc. didn't. Ideas?

---

### Post by DuckHook on 2019-05-19
*Thread moved to **Any Other OS** as the more appropriate forum.*

---

### Post by TheFu on 2019-05-20
Do you really mean "container" or do you mean chroot?  I've run Linux desktops in a chroot on Android.  There's no reason a container couldn't be used. They are supported on any hardware using a Linux kernel, but really nobody used then until the 3.x line of kernels.

Outside this Samsung world, containers are meant to be built, configured, packaged, launched, do their job, then destroyed.  A 1 week lifespan is really odd for any container.  Most should last less than 1 day.  

I've never seen any containers used like a normal desktop. Perhaps my experience is limited.  I use them to run a few desktop applications in highly restricted environments, to avoid being hacked from outside, but if the container had a full OS inside it, no way would I do that.  Breaking out of containers, especially if the container has developer tools installed has never been too hard.  It is a huge risk.  The mitigation for that problem is only to have the specific program inside container to meet the purpose.  If you need a web server, only put the web server application inside. No shells. No wget, curl, nothing else except the web-server program and data for it, probably the data should be read-only if it isn't remote too.

If the configuration needs to change, then a build, configure, package, launch series is the best practice. Most places automate this. I bet Samsung has, which is why they only provide a way to get a fresh, complete, image. Some places spin up new containers for every new task, picking up the newest code and config just as the container spin-up happens.
 
Of course, be careful where you get any pre-build containers: [https://threatpost.com/alpine-linux-docker-images-unlocked/144542/](https://threatpost.com/alpine-linux-docker-images-unlocked/144542/)

A conference a few years ago had a bunch of Container best practices: [https://www.youtube.com/playlist?list=PLvG1nXgsl22FhL55suZtb7RIjEJtkYYC5](https://www.youtube.com/playlist?list=PLvG1nXgsl22FhL55suZtb7RIjEJtkYYC5)  Enjoy, if you learn this way.

Ok, so after all that background, I suspect you still just want a way to have your data and settings and packages backed up, then be able to quickly reinstall everything into a fresh DevX container provided by Samsung?  My normal linux backup technique should work, even for ARM-based systems.

Use **apt-mark** to get a list of manually and automaticly installed backups. Keep 2 lists. Put those into your backup storage area.
```
 apt-mark showauto | tee /root/backups/apt-mark.auto
 apt-mark showmanual | tee /root/backups/apt-mark.manual

```

Use a good backup tool to backup any files that might have been changed manually by you anywhere on the system.
> /etc/
/home/
/root/
would be the main places, but there are many others depending on the programs, services, and DBs installed.  You need to know where those are located. If you installed anything outside the package manager, backing that up is up to you too. I usually put those things into /usr/local/. I use **rdiff-backup** for remote backups. It works over **ssh** and is very efficient after the initial backup is made.  If there is a DBMS, it needs to be quiesced for the backup to be consistent.  That means either dump it to a format that can easily be restored or shutdown the DBMS.
A general command for rdiff-backup, assuming the ssh root-to-root userid access is properly configured using ssh-keys.  ssh should only allow remote root access without-passwords and only from the backup server, not the entire world.  Put those settings in the sshd_config file for this.
On the backup server (not the ARM device), 
```
sudo rdiff-backup --exclude-special-files --include root@{IP-of-Samsung-Container}:/etc \
 --include root@{IP-of-Samsung-Container}:/home \
  --include root@{IP-of-Samsung-Container}:/root \
  --exclude **/.cache \
  --exclude / \
 /Backups/{hostname-of-Samsung-Container}/
```
Note the trailing slash where I have it. I didn't test this command. The actual one I use is build using a 200 line script that is customized for each computer I "pull" backups from.  "Pull" backups over ssh is important for many reasons. Never make backup storage directly available to any client computers.  The backup server needs to "pull" the data, never push it.

To restore on a new system, put the data back, then reload the list of manually installed packages and have them installed.  It is important that the data and settings be in place before the packages installed.  Use the rdiff-backup restore option.  To re-install the packages from that list, use:
```
 sudo apt-mark manual $(cat /root/backups/apt-mark.manual)
 sudo apt-get -u dselect-upgrade
```

I've written a bunch about backup and restore in these forums. Don't think rehashing them in more detail here would be productive. If you need more details, start by looking for rdiff-backup and my userid.

Also, check the manpages for any commands or command options you don't understand. AFTER doing that, if you don't understand, please ask.

Anyways, hope this is sufficiently clear.  We cannot tell the Linux level of a poster, so I tend to assume intermediate level and above.

---

