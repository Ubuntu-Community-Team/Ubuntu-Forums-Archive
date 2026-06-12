---
title: "Apple keyboard FN keys configuration problem"
date: 2011-12-17
forum: Apple Hardware Users
---

### Post by ubix on 2011-12-17
While in Ubuntu 10.10 Maverick the configuration of Apple keyboard was possible since the special directories and files existed:

```
root@vUbu:/sys/module/hid_apple/parameters# ls -l
total 0
drwxr-xr-x 2 root root    0 2011-12-12 15:17 ./
drwxr-xr-x 7 root root    0 2011-12-12 15:17 ../
-rw-r--r-- 1 root root 4096 2011-12-12 15:17 fnmode
-rw-r--r-- 1 root root 4096 2011-12-17 18:40 iso_layout
```

On Ubuntu 11.10 (Oneiric Ocelot) the special directories **hid_apple/parameters** and the function key parameter file **fnmode** are missing in **/sys/module/** hierarchy, and indeed, because these are special files can not be created!

Because of this the following configuration code 

```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```

in **/etc/rc.local** can not be implemented anymore. This means that those of us who use Apple keyboards or run Ubuntu OS in VMs on Aplle machines can no longer access software features by using function keys!

Is this a permanent departure from the Open Systems philosophy, or just an annoying bug that creeped up in the latest release of Ubuntu?

---

### Post by ubix on 2011-12-20
I was hoping someone from Ubuntu will be able to tell us, what happened. I believe, this issue should be addressed sooner or later.

---

### Post by 2F4U on 2011-12-20
You mean a developer? Developers are usually not visiting the forum. If you want to talk to them you should create a bug report for your problem.

---

### Post by ubix on 2011-12-20
> **2F4U said:**
> You mean a developer? Developers are usually not visiting the forum. If you want to talk to them you should create a bug report for your problem.Nope, I did not mean a developer but a competent maintainer. This is not a development issue from where I stand. A user got burned by the latest update. As far as I can tell it may very well be a bug, but there should be plenty of users who are running Ubuntu from Apple equipment and I bet a moderator is familiar with the issues explained in my original post. So dear F4U, I am hoping someone here will first confirm they have the same problem and that the right moderator will come by in time.

FYI see also:  [http://ubuntuforums.org/showthread.php?t=1898070](http://ubuntuforums.org/showthread.php?t=1898070)

---

### Post by scognito on 2011-12-20
It works here on my iMac 21 mid 2011 and Oneiric
```

scognito@headache:~$ uname -a
Linux headache 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

scognito@headache:~$ sudo dmidecode -s system-product-name
iMac12,1

scognito@headache:~$ cat /sys/module/hid_apple/parameters/fnmode
1

scognito@headache:~$ echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
2

scognito@headache:~$ cat /sys/module/hid_apple/parameters/fnmode
2

```
playing with 1 and 2 values works as expected (enable/disable FN keys).

Hope it helps!

---

### Post by ubix on 2011-12-20
**scognito**, please tell me which version of Ubuntu are you running? This works for me too on 10.10, but not after installing 11.10 anew.

---

### Post by scognito on 2011-12-20
> **ubix said:**
> **scognito**, please tell me which version of Ubuntu are you running? This works for me too on 10.10, but not after installing 11.10 anew.

I told you, I'm using 11.10 :)
It is 64 bit version btw.

---

### Post by ubix on 2011-12-20
> **scognito said:**
> I told you, I'm using 11.10 :)
It is 64 bit version btw.Sorry, I missed your mention of ***Oneric***, _because you didn't explain how you installed it_? You most likely have upgraded from an earlier release where special files where created and kept over in the upgrade. Just as well, I have told you that already too! And FYI, I too have installed 64bit version of Oneric on my Mac Server, however mine is a new installation, and not an upgrade.

The new installation for some reason did not create special files! And you can not create them with a **sodo** or even if you create **root** account. Clearly you or I are missing something here. Your commands you have posted in your 1st post here should fail if the pertinent ***/sys/module*** infrastructure doesn't get installed or is missing just like the ones run from ***/etc/rc.local***.

Though unlikely, there may be yet one more possibility we both are not considering. Namely, I also have installed Ubuntu 11.10 on Mac mini Server in ***Virtual box***. Perhaps for some reason in VB this problem develops. But I will only know this for sure after I install ***11.10*** in true (not virtual) box. But that may not be so soon, due to still many unresolved issues. I do not want to loose the most stable Ubuntu platform yet to the flaky Unity based "serwups".:(

---

### Post by Apewall on 2011-12-21
> **ubix said:**
> Sorry, I missed your mention of ***Oneric***, _because you didn't explain how you installed it_? You most likely have upgraded from an earlier release where special files where created and kept over in the upgrade. Just as well, I have told you that already too! And FYI, I too have installed 64bit version of Oneric on my Mac Server, however mine is a new installation, and not an upgrade.

The new installation for some reason did not create special files! And you can not create them with a **sodo** or even if you create **root** account. Clearly you or I are missing something here. Your commands you have posted in your 1st post here should fail if the pertinent ***/sys/module*** infrastructure doesn't get installed or is missing just like the ones run from ***/etc/rc.local***.

Though unlikely, there may be yet one more possibility we both are not considering. Namely, I also have installed Ubuntu 11.10 on Mac mini Server in ***Virtual box***. Perhaps for some reason in VB this problem develops. But I will only know this for sure after I install ***11.10*** in true (not virtual) box. But that may not be so soon, due to still many unresolved issues. I do not want to loose the most stable Ubuntu platform yet to the flaky Unity based "serwups".:(


i do have a /sys/module/hid_apple which fnmode will temporarily work, however it will reset itself, all 3 of the suggested "permanent" methods to set fnmode do not work for me.

Tested on a fresh install of 11.10 ubuntu and 11.10 Xubuntu, Macbook Pro 4,1.

So basically, the files are there for me but do not work as they should.

---

### Post by pindar on 2011-12-21
> **ubix said:**
> Sorry, I missed your mention of ***Oneric***, _because you didn't explain how you installed it_? You most likely have upgraded from an earlier release where special files where created and kept over in the upgrade. Just as well, I have told you that already too! And FYI, I too have installed 64bit version of Oneric on my Mac Server, however mine is a new installation, and not an upgrade.

The new installation for some reason did not create special files! And you can not create them with a **sodo** or even if you create **root** account. Clearly you or I are missing something here. Your commands you have posted in your 1st post here should fail if the pertinent ***/sys/module*** infrastructure doesn't get installed or is missing just like the ones run from ***/etc/rc.local***.

Though unlikely, there may be yet one more possibility we both are not considering. Namely, I also have installed Ubuntu 11.10 on Mac mini Server in ***Virtual box***. Perhaps for some reason in VB this problem develops. But I will only know this for sure after I install ***11.10*** in true (not virtual) box. But that may not be so soon, due to still many unresolved issues. I do not want to loose the most stable Ubuntu platform yet to the flaky Unity based "serwups".:(
I find your passive-aggressive style inappropriate. Someone was trying to be helpful, so you have no business being rude. So just for the record: I have a brand new install of 11.10 on an imac, and the file /sys/module/hid_apple/parameters/fnmode is most definitely there and works as expected. It is possible that an install on Virtual Box is different here, or you may have mistyped something (your mentioning "sodo" does not inspire confidence in your typing abilities).

pindar

---

### Post by ubix on 2011-12-21
> **Apewall said:**
> i do have a /sys/module/hid_apple which fnmode will temporarily work, however it will reset itself, all 3 of the suggested "permanent" methods to set fnmode do not work for me.

Tested on a fresh install of 11.10 ubuntu and 11.10 Xubuntu, Macbook Pro 4,1.

So basically, the files are there for me but do not work as they should.**fnmode** _definitely should not reset itself_! Do you have the following line in **/etc/rc.local** 
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```NOTE: there must be _**exit 0**_ at the end of rc.local file!  However, I am even more surprised, the special files are there for you, perhaps this really is a VirtualBox issue, though I am not willing to risk to upgrade on the true hardware box (I mean outside VB) yet until a more trustworthy evidence comes around. All the answers here are too contradictory to be taken seriously, unless Ubuntu updates fixed this problem in the past, but why would files not exist on my out of the box and otherwise perfect installation, which also had been installed with updates option checked, as well as I had made the updates a few times since then. The fact is that Ubuntu since introduction of Unity has become a very problematic proposition. We can only hope that things will get better, after all we try to be helpful too and contribute to this process. 

The latter brings me to the last inappropriate comment suggesting even more inappropriate state of affairs here, namely, as **pindar's** post shows some here are far too personal and may even have alternative motives to post their moralistic comments. I wish to know what was really so terrible that prompted **pindar's** ridiculous comment.:shock:

---

### Post by scognito on 2011-12-21
> **pindar said:**
> I find your passive-aggressive style inappropriate. Someone was trying to be helpful, so you have no business being rude. So just for the record: I have a brand new install of 11.10 on an imac, and the file /sys/module/hid_apple/parameters/fnmode is most definitely there and works as expected. It is possible that an install on Virtual Box is different here, or you may have mistyped something (your mentioning "sodo" does not inspire confidence in your typing abilities).

pindar
Anyway I'm using Oneiric fresh installation, since I bought my Mac 20 days ago :)

---

### Post by ubix on 2011-12-21
> **scognito said:**
> Anyway I'm using Oneiric fresh installation, since I bought my Mac 20 days ago :)

Can you please tell us how did you install Ubuntu on your iMac? Did you repartition HD, or did you install it in a VM. Did you partition your Ubuntu file systems into smaller partitions /, /boot, ... ?

---

### Post by scognito on 2011-12-21
> **ubix said:**
> Can you please tell us how did you install Ubuntu on your iMac? Did you repartition HD, or did you install it in a VM. Did you partition your Ubuntu file systems into smaller partitions /, /boot, ... ?

I'll write a guide when I'll be back home...I've followed some guide on internet...no special things to do: partitioned using osx, then installed windows, and finally ubuntu.
No virtual machines, no other stuff, just another partition (shared data NTFS)...as simple as possible on iMac 21,5'' mid 2011.

---

### Post by ubix on 2011-12-21
> **scognito said:**
> I'll write a guide when I'll be back home...I've followed some guide on internet...no special things to do: partitioned using osx, then installed windows, and finally ubuntu.
No virtual machines, no other stuff, just another partition (shared data NTFS)...as simple as possible on iMac 21,5'' mid 2011.Thank you for your for your information and indeed your generosity, I have done just that already 7 years ago in 2006, when I experimented on Mac mini and have written up an extensive manual how to instal Ubuntu on Mac mini i386 partitions both native Mac partition and others. Unfortunately the files have disappeared from [http://doc.gwos.org/index.php/UbuntuOnApple](http://doc.gwos.org/index.php/UbuntuOnApple). I still have my original ascii (Wiki-formatted) texts, but have no interest on running Ubuntu on Apple hardware directly, however, you gave me an incentive to recover the text and publish it again on Ubuntu Wiki. Here is the recovered page: [https://help.ubuntu.com/community/UbuntuOnMacMini](https://help.ubuntu.com/community/UbuntuOnMacMini).

As you can see  I am not interested in the kind of information you are writing about, but rather things you do not want or can't answer, namely, how many partitions did you install in your Ubuntu, did you observe the size restrictions, etc... I would have liked to discuss the issues that are directly related to the missing special files. The rest I pretty much have under control and is of no particular value here except if you could confirm that special files get installed on non-Apple Intel and AMD platforms.  Besides the solution of installing Ubuntu directly on Apple sucks in many respects.

Though we are talking about Apple keyboard here, this is not really an issue related solely to Apple computers. Indeed for me it is much more important that I will be able to use Apple keyboard on Ubuntu installed on regular PCs. Hence, I only want to investigate the mysterious disappearance of special files, and why they did not get created in my otherwise perfect installation? How wide spread is this problem and what causes it! 

I do have a few clues but are not worth mentioning if all I get from other participants is only a contradictory information, that perhaps due to lack of understanding the complexity that spawns from myriad of possibilities can not even be taken seriously. For the moment I will put trust in what you've told me so far, and will try to resolve this issue on my own. And  when I do, and indeed if I do, I will report back to you what was the problem, even if it were mistyping of ***sodo*** as suggested by the faint-hearted moralist, but not if it is a VB issue, since here clearly none cares about this particular eventuality.

---

### Post by Apewall on 2011-12-25
> **ubix said:**
> **fnmode** _definitely should not reset itself_! Do you have the following line in **/etc/rc.local** 
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```NOTE: there must be _**exit 0**_ at the end of rc.local file!  However, I am even more surprised, the special files are there for you, perhaps this really is a VirtualBox issue, though I am not willing to risk to upgrade on the true hardware box (I mean outside VB) yet until a more trustworthy evidence comes around. All the answers here are too contradictory to be taken seriously, unless Ubuntu updates fixed this problem in the past, but why would files not exist on my out of the box and otherwise perfect installation, which also had been installed with updates option checked, as well as I had made the updates a few times since then. The fact is that Ubuntu since introduction of Unity has become a very problematic proposition. We can only hope that things will get better, after all we try to be helpful too and contribute to this process. 

The latter brings me to the last inappropriate comment suggesting even more inappropriate state of affairs here, namely, as **pindar's** post shows some here are far too personal and may even have alternative motives to post their moralistic comments. I wish to know what was really so terrible that prompted **pindar's** ridiculous comment.:shock:

This is my rc.local file
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
exit 0

```
Output after 10 hours of uptime for fnmode
```

~$ cat /sys/module/hid_apple/parameters/fnmode
~$ 1

```

fnmode resets itself to 1.

---

### Post by ubix on 2011-12-28
> **Apewall said:**
> This is my rc.local file
```
echo 2 > /sys/module/hid_apple/parameters/fnmode
exit 0

```
Output after 10 hours of uptime for fnmode
```

~$ cat /sys/module/hid_apple/parameters/fnmode
~$ 1

```

fnmode resets itself to 1.

As promised, I have done some research on this matter, and it is time to report back. In fact instead, I will refer you to the document I wrote about this. See: [Trouble With Apple Keyboard On Ubuntu](https://help.ubuntu.com/community/TroubleWithAppleKbdOnUbuntu). 

The problem is much more complex than originally anticipated, because it is rather inconsistent. As is seen by the interest and responses here, not many even know about this problems. This is the reason I decided to write forementioned document and adorn it with a few pictures, to underscore that this is not merely an Apple Ubuntu issue, but it pertains to all who use Apple keyboards, and even more so for those who run Ubuntu as a VM on Macs. I am adding the two pictures that reveal this point also here. Hopefully they will convey this very point about the problem not being only Apple Ubuntu, but rather a general Ubuntu installation and configuration problem.

[img]https://help.ubuntu.com/community/TroubleWithAppleKbdOnUbuntu?action=AttachFile&do=get&target=macmini-w-vBox-s200.png[/img] - - [img]https://help.ubuntu.com/community/TroubleWithAppleKbdOnUbuntu?action=AttachFile&do=get&target=my-amd-n-AppleKBD-w-vBox-s200c-h.png[/img]

---

