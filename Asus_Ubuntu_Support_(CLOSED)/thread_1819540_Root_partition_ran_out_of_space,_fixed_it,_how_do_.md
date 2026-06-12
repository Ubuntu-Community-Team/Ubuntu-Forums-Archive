---
title: "Root partition ran out of space, fixed it, how do I prevent this in future?"
date: 2011-08-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by SolipsistWriter on 2011-08-06
I have an Eee PC 901. I set up the 4GB SSD to act as the root partition and the 8GB SSD to act as the home partition.

However, I was just unable to log into my system as I got an error about GNOME Power Management. Some Googling told me this was due to low space in the root partition, so I ran sudo apt-get clean which cleared up the cache, but df tells me that 89% of my root partition is used up, so it's only a matter of time before this happens again.

Can anyone tell me how to set my computer up to avoid this in the future? Can I get it to clear the cache out automatically or store certain things on the home partition instead? Or is there some other method of preventing this issue?

Thanks :)

---

### Post by haqking on 2011-08-06
> **SolipsistWriter said:**
> I have an Eee PC 901. I set up the 4GB SSD to act as the root partition and the 8GB SSD to act as the home partition.

However, I was just unable to log into my system as I got an error about GNOME Power Management. Some Googling told me this was due to low space in the root partition, so I ran sudo apt-get clean which cleared up the cache, but df tells me that 89% of my root partition is used up, so it's only a matter of time before this happens again.

Can anyone tell me how to set my computer up to avoid this in the future? Can I get it to clear the cache out automatically or store certain things on the home partition instead? Or is there some other method of preventing this issue?

Thanks :)

yeah make it bigger ;-)

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html) you can see towards the bottom it recommends 4Gb as minimum.

depending on how many apps you install and the like then other folders such as /usr could be mounted seperately.

My / or root is 8 gb, but actually only 1 gb is used.

i mount /tmp /usr /var and /boot also as seperate partitions.

Everyone has a different setup.

---

### Post by SolipsistWriter on 2011-08-06
Thanks for the useful info :)

This will sound really n00bish, but does the setup I have now mean all the system folders such as usr and var are on the same disk as root? If so, is there a way I can change the partitions without reinstalling Ubuntu, so I can unload a bit of the system stuff onto a partition of my 8GB SSD, freeing up the 4GB?

---

### Post by oldfred on 2011-08-06
Generally you want all system partitions of / in one partition so they can share available space as you otherwise have to allocate based on your usage and invariably over allocate to one or the other. But you may be an exception to the rule as 4GB is very tight. You can house clean on a daily basis.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

You can also install smaller packages. OpenOffice or LibreOffice are large as is Firefox. Some of the lightweight distributions default to Gnumeric and AbiWord and Chromium. Or you could just consider one of the lighter weight versions.

---

### Post by SolipsistWriter on 2011-08-07
Yeah, I did also think I could install Xbuntu on my system instead, but I'd like to avoid that if possible.

I think the most sensible thing for me to do is move more system folders to my user memory and do housekeeping once a week. Having to do is every day would get very irritating.

I just installed Gparted but it won't run, though. It asks for admin permissions then nothing happens.

---

### Post by Irihapeti on 2011-08-07
I have an EeePC 900 with 4GB root (system) partition and /home on the 16GB one. I keep a strict eye on the space available and run "sudo apt-get clean" regularly. This removes all downloaded deb files. 

Another trick is to either remove programs you don't need, or start with a minimal install and build up from there. I'm currently running 10.04 with Gnome-core plus other packages as required. This installation has been running for months with no problems with space.

---

### Post by oldfred on 2011-08-07
I find anytime I have to run more than a couple commands more than once to list history to show all the commands, copy into a bash file and just run the bash file.

I would copy the housekeeping commands into a bash file and run that whenever you want or schedule it with cron to totally automate it.

Someone had previously posted this, but I am not bash expert. I did find apt-get moo an interesting command.:)

You have to change from my home to yours.
```
#! /bin/bash
reset
echo -e '\E[34;47mTaking the Trash out.'; tput sgr0
rm -rf  /home/fred/.local/share/Trash/files/*
rm -rf  /home/fred/.local/share/Trash/info/*

echo -e '\E[34;47mPerform repository update.'; tput sgr0
apt-get update

echo -e '\E[34;47mPerform any upgrades.'; tput sgr0
apt-get upgrade

echo -e '\E[34;47mFixing Apt.'; tput sgr0
dpkg --configure -a
apt-get -f install
apt-get dist-upgrade

#echo -e '\E[34;47mKilling Orphans.'; tput sgr0
#people with external repos tend to have orphaned packages they acually need. 
#deborphan --guess-all | xargs apt-get -y remove --purge

echo -e '\E[34;47mAutoremove.'; tput sgr0
apt-get --yes autoremove --purge


echo -e '\E[34;47mAuto clean.'; tput sgr0
apt-get --yes autoclean --purge

echo -e '\E[34;47mMoooo'; tput sgr0
apt-get moo

```

---

### Post by wb8nbs on 2012-02-03
I have found every kernel update leaves cruft in /boot/ and in /usr/src/  Removing older kernel version files frees up significant space on the 4G root partiton.  I only keep the two newest kernels.  

You can do a recursive remove from a shell to get rid of obsolete files but _be aware that this is a VERY dangerous thing to do as root_.  Always do a recursive ls before the recursive remove to see what will be deleted.  Another way is to open a shell and do "sudo nautilus", then you can navigate to /boot or /usr/src and click-delete on the files you no longer need.  Again, this is _dangerous_, so be sure you are only deleting old files. If you screw up, you can end up reinstalling the distro from scratch.

---

