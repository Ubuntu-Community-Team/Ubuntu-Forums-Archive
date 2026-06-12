---
title: "Bus error"
date: 2013-09-12
forum: Any Other OS
---

### Post by Manoj_Singh on 2013-09-12
Hi everyone,

I am not sure if this is right place to ask my question.

I checked with all other bus error threads but none helped.

My skype is not starting.

When I run it in terminal I get "Bus error".

I uninstalled and then installed but it did not help.

I cleared all cache using "sudo apt-get clean all" and BleachBit but none of them helped.

This problem is happening with some other applications also. some are  working and some are not. The ones that are not working, are giving bus  error.

They all were working around week back. I only did automatic update and nothing else around that time.

What could be the problem? Can someone please help?

I am using Linux Mint 13.

Thanks,
Manoj

---

### Post by Manoj_Singh on 2013-09-12
Hi All,

I forgot to mention that this problem is hapening for  last 1-2 weeks. Earlier it was working alright. I don't remember making  any custom installation.

Automatic software update crashed though  and was not updating. It was giving 'error reading database' but got  resolved automatically after few days. I guess I am having this problem  since then.

Any help or guidance is lot appreaciated. 

Thanks,
Manoj

---

### Post by Manoj_Singh on 2013-09-13
Hi,

I just tried boot-repair [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/) and deleting and restoring /dev/null but they did not help.

Somewhere I read that it might be because of broken filesystem. So, I am trying fsck. But I am getting this error there:

> fsck.ext2: No such file or directory while trying to open /dev/sda1 possibly non-existent device?

Apart from this when I try to update some package or install a new one, I get these warnings: I feel these are also related to the problem somehow:

> dpkg: warning: files list file for package `librpm2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdrm-intel1:i386' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `w64codecs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mintinstall' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-regdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0:i386' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `transmission-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wget' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rpm-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librpmio2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-system-adjustments' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `activity-log-manager-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `whiptail' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libunistring0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wamerican' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `whois' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3:i386' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssl1.0.0:i386' missing, assuming package has no files currently installed.


Please let me know if you think I should do something that could help.

Thanks,
Manoj

---

### Post by Manoj_Singh on 2013-09-13
Hi,

I tried to clean the acrhive files [http://www.webupd8.org/2009/04/clean-unnecessary-temporarily-files-in.html](http://www.webupd8.org/2009/04/clean-unnecessary-temporarily-files-in.html) but that also did not help.

Thanks,
Manoj

---

### Post by grahammechanical on 2013-09-13
May I point something out to you? This is the Ubuntu+1 section of Ubuntu forums. It is here allow those of us who are running the Ubuntu 13.10 development branch to share experiences. In a couple of months we will switch to Ubuntu 14.04 development branch.

This thread should be in the Other OS/Distro Support section of the forum. You may find in that section others who are using the same distribution you are using. By the way, in a situation like this I would reinstall. I would not be surprised if your attempts to fix things have actually made things worse. It happens to me.

Regards.

---

### Post by pqwoerituytrueiwoq on 2013-09-13
last time that was happening to me it was the [SSD](http://www.newegg.com/Product/Product.aspx?Item=N82E16820211717) acting up
a firmware update fixed it, updating it wiped the drive and i loaded a backup

---

### Post by cariboo on 2013-09-13
I missed the Mint 13 in the first post. Moved to Other OS/Distro Support.

---

### Post by Manoj_Singh on 2013-09-15
Thanks Cariboo for guiding to the right section.

[ 						 							]("http://ubuntuforums.org/member.php?u=1087323")[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"): I already did reinstall of skype but that did not help. Are you suggesting, total OS reinstall?

[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458"): Can you please give me a bit more details on this?

Thanks,
Manoj

---

### Post by pqwoerituytrueiwoq on 2013-09-16
a bus error basically means there is a problem connecting to the HDD/SSD it can tell the drive is there but it can't get data in/out without corruption
i don't know much about it, but it was throwing the system into read only mode, updating the SSDs firmware fixed the issue
basically it is a hardware issue, if you can run the disk utility and get some info from your hdd/ssd it may help
check the smart attributes
gsmartcontrol is a good tool for that

---

### Post by Manoj_Singh on 2013-09-19
Thanks pqwoerituytrueiwoq. I will work on this and let you know the results. Yesterday I tried to run fsck after running this in terminal > sudo touch /forcefsck.

This did not solve the problem but I guess this showed us what the problem is. Please see the output of fsck that I ran after entering in recovery mode while rebooting.

> fsck from util-linux 2.20.2
Error reading block 62915093 (Attempt to read block from file system resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsk MANUALLY. (i.e. ; without -a or -p options)

mountall: fsck/[808] terminated with status 4.
mountall: File system has errors: /
mountall: Skipping mounting / since plymouth is not available

Finished: Please press ENTER.


Do you think this is helpful and now I can do something to fix it?

Thanks a lot for help.

Regards,
Manoj

---

