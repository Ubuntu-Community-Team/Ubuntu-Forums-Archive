---
title: "Freeze then unable to reboot during Update"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by mikie_gb on 2008-04-16
Hi, I have had this problem twice in the last week, once on Gutsy 64 bit and lastnight again on Gutsy 32 bit.

On both occassions during an update, the manager freezes and after an extended period I reboot the machine and all hell breaks loose.

Last night I took a photo of what pops up on the screen and I will try and type it out as accurately as possible
> 

i/file_acl for inode 9897206 (usr/sharea1sa/cards/ens1371.conf)

/dev/hda1: Unexpected inconsistency; run fsck MANUALLY
(i.e., without -a or -p options)
                                                                                                  [failed]
fsck died with  exit status 4

* An automatic  file ystem check  (fsck) of the root file system failed. A manual FSCK should be performed and the system restarted
The fsk must be performed in maintenance mode with the root file system mounted in read only mode,

* the root filesystem is currently mounted in read-only mode,
A maintenance shell will now be restarted
After performing system maintenance , press CONTROL-D to terminate the maintenance shell and restart the system ,
bash: no job control in this shell
bash groups: command not found
bash: lesspipe: command  not found
bash: command: command not found
bash: the: command not found
bash: dircolors command not found
bash: command: command not found
bash: the: command not found
root@michael-laptop:"#


Now I wasn't sure what to do here and on rebooting the machine it pops up with the option to go in to Bios then starts on grub 1, 2 etc and black screens the H disk will run for 7 odd minutes then everything stops

I have tried booting up in safe mode but I get the same thing.

Any suggestions would be greatfully received as I have already reinstalled once this week and I am not sure that the laptop itself isn't damaged.

The laptop is a completely standard Acer Aspire 5100 with AMD Turion 64x2  I was running the 64 bit gutsy when the first instance of this problem occured but swopped to 32 bit on the reinstall in the hopes flash etc would be easier to work with (it was)

---

### Post by zvacet on 2008-04-16
You will need your live Cd,because you have to run fsck to unmounted partition.Put live Cd in drive and type in terminal

```
fsck /dev/hda1
```

---

### Post by mikie_gb on 2008-04-16
many thanks for the help. That worked after a couple of tries.

I am back in as normal, but the Update manager is wanting to down load the same two packages again and until I know what is causing Update manager to lock up part way through I will avoid down loading them for the time being.

---

