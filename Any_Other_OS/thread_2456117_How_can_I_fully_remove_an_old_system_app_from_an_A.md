---
title: "How can I fully remove an old system app from an Android device?"
date: 2021-01-04
forum: Any Other OS
---

### Post by jcdenton1995 on 2021-01-04
Hello all!

Thought I'd try a little android question here.

So I have a Samsung Note 4 running an unofficial build of Lineage OS 17.1. I want to re-enable the call recording function of the Dialer app, and I'm 95% of the way there, but I'm having trouble installing the modified .apk file back onto the phone. So far I have...


[LIST=1]
[*]copied the Dialer.apk from the phone and decompiled it using 'apktool' 
[*]edited the necessary .xml file 
[*]rebuilt it using apktool 
[*]generated a keypair using 'keytool' 
[*]signed the .apk using 'apksigner' 
[/LIST]

...all of which has been successful (eventually), but the problem is when I try to install the modified .apk back to the phone via...```
adb install -r Dialer.apk
```...I get the following error:```
[INSTALL_FAILED_UPDATE_INCOMPATIBLE: Package com.android.dialer signatures do not match previously installed version; ignoring!]
```...and when I try to uninstall the Dialer.apk already on the device, I get...```
Failure [DELETE_FAILED_INTERNAL_ERROR]
```...even when running adbd as root. I tried opening a shell on the device via adb and removing the encumbent .apk as root, but the filesystem is mounted read-only. This is where I got a bit stuck, I don't know how to work out which file-system the .apk file comes under. if I run disk-free on it's directory I get the following...```
Filesystem            1K-blocks    Used Available Use% Mounted on
/dev/block/mmcblk0p24   3628452 1094988   2533464  31% /apex/com.android.media
trlte:/system/product/priv-app/Dialer
```...which to me, /dev/block/mmcblk0p24 is the partitons device file, and it's filesystem is mounted on /apex/com.android.media,so I try running...```
mount -o rw,remount /dev/block/mmcblk0p24
```... just to get a message telling me that device path isn't in /proc/mounts. So I ran the following...```
# mount | grep mmcblk0p24

/dev/block/mmcblk0p24 on / type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.tzdata@290000000 type ext4 (ro,seclabel,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.tzdata type ext4 (ro,seclabel,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.runtime@1 type ext4 (ro,seclabel,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.runtime type ext4 (ro,seclabel,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.resolv@290000000 type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.resolv type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.media.swcodec@290000000 type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.media.swcodec type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.conscrypt@299900000 type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.conscrypt type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.media@290000000 type ext4 (ro,seclabel,nodev,relatime,discard)
/dev/block/mmcblk0p24 on /apex/com.android.media type ext4 (ro,seclabel,nodev,relatime,discard)
```...which basically looks like that filesystem is mounted in many different places, and it's mounted read only.

I'm going to be doing some serious looking into it, but I have a call in a few days which it might be wise to keep a record of, so I'd like to get it working soon, although if it comes to it there are 3rd party call recorders I could use, but I'd rather stick with the native Dialer app.

Any help is appreciated as always!

---

### Post by coffeecat on 2021-01-05
Support, not discussion.

*Thread moved to **Any Other OS**.*

---

### Post by scorp123 on 2021-07-10
> **jcdenton1995 said:**
> How can I fully remove an old system app from an Android device? 

I had to do that ages ago on my Samsung Galaxy Note 1 because one of the stupid default apps there contained some (now defunct) Samsung news service bloatware that would nag me all the time about buying newspaper subscriptions and pop-up ads ... So that stupid thing had to go.

And this is what I used back then:
[https://play.google.com/store/apps/details?id=com.keramidas.TitaniumBackup]("https://play.google.com/store/apps/details?id=com.keramidas.TitaniumBackup")

At least back then it was able to uninstall otherwise uninstallable applications from the Android OS. And if you made a backup before that drastic step it was also able to put that stupid app back if you ever wanted that. I have not had the need to install and use "Titanium Backup" ever since those days (ca. 2011?) because none of the Samsung Galaxy Note models that I owned later and still own now have had that kind of "nagware" again.

The various reviews on the German language Google Play Store suggest that "Titanium Backup" may no longer be in active development!? Some of the reviewers there suggested this alternative:
[https://play.google.com/store/apps/details?id=org.swiftapps.swiftbackup]("https://play.google.com/store/apps/details?id=org.swiftapps.swiftbackup")

I have never used "Swift Backup", but based on the reviews I can see on Google Play it too should be able to remove otherwise uninstallable apps from an Android OS, provided that you rooted it.

Good luck.

---

### Post by scorp123 on 2021-07-10
Aww man, sorry for the necropost ](*,)

---

### Post by reuben-p on 2021-12-15
You need to replace the Dialer.apk on the /system partition using Recovery. You can find it using the following

```
#[FONT=monospace][COLOR=#000000] ls -R /system |grep dial -i[/COLOR][/FONT]
```

back up the old Dialer.apk and place the new one in it's place.
Reboot and  your new Dialer should be activated.

---

