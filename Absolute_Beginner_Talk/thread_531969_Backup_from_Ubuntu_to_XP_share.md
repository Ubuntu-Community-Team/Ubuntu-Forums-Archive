---
title: "Backup from Ubuntu to XP share"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by steveb001 on 2007-08-22
Hi
I am in the process of migrating from Vista to Ubuntu and have managed to find alternative programs for everything I need, with one exception.

Under Vista (and previously XP) I used backup programs (SecondCopy and Cobian Backup) to back up certain data from my PC to a "NAS" (runnig XP with a shared folder) on my network.  The Backup program also copied other data (originating from other PCs) on my network from the NAS to a folder on my PC.

I have looked for a product which can provide similar functionality but cannot seem to find one which will backup data to and from a Windows XP share.
I can manually connect to the XP share from within Gnome and can manually copy data backwards and forwards between the two machines.  However, this is not an ideal solution (as I am looking for an automated solution for this).

Any assistance in pointing me in the right direction would be gratefully received.
Thanks in advance.

---

### Post by mikeyphi on 2007-08-22
I have my windows permanently mounted and use sbackup (download with synaptic) in ubuntu to do a daily backup. It's a good flexible program - have a look at it!

---

### Post by steveb001 on 2007-08-22
mikeyphi

Thanks for the quick reply.  I have sbackup installed on my Ubuntu PC but when i run the config utility I can't seem to point the destination setting to the XP share.  Any ideas?

Also, you say that you have your XP permanently mounted - how can I do that?

Thanks once again for your help

---

### Post by jppaynesr on 2007-08-22
[COLOR="Red"]WARNING[/COLOR]

Be VERY careful if you access the wikka site of sbackup at sourceforge. The_ features page_, the _configuring page_, and the_ restoring files_ page are loaded with hyper links at the top. I clicked one and it was loaded with pop ups, fake virus scanners, and other junk. It looks like this page has been severely hacked. Be warned.

---

### Post by mikeyphi on 2007-08-22
> **steveb001 said:**
> mikeyphi

Thanks for the quick reply.  I have sbackup installed on my Ubuntu PC but when i run the config utility I can't seem to point the destination setting to the XP share.  Any ideas?

Also, you say that you have your XP permanently mounted - how can I do that?

Thanks once again for your help

It's very easy! Good guide here:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

and - by the way - there are no issues with installing using synaptic, especially if you don't use third party sites.

If you are having difficulty pointing to your windows share whilst in the sbackup menu - make a note of the address and type it in yourself
eg; /media/windows/linuxbackup

---

### Post by steveb001 on 2007-08-22
mikeyphi

Thanks for the reply.  I have now managed to connect to my XP share (syntax error when typing the path in the "destination directory" box :oops:)

However, when i set up the backup job with a test file, i get a message saying that the job has been started (wit a process iD).  However, no files have been copied to my XP share.

I really appreciate your help with this, but I don't seem to be getting very far at the moment.  I might have to resort to running a backup utility through wine if i can't solve this.

Thanks once again

---

### Post by mikeyphi on 2007-08-22
> **steveb001 said:**
> mikeyphi

Thanks for the reply.  I have now managed to connect to my XP share (syntax error when typing the path in the "destination directory" box :oops:)

However, when i set up the backup job with a test file, i get a message saying that the job has been started (wit a process iD).  However, no files have been copied to my XP share.

I really appreciate your help with this, but I don't seem to be getting very far at the moment.  I might have to resort to running a backup utility through wine if i can't solve this.

Thanks once again

Make sure you've given ubuntu 'write' access to XP - but first just confirm, by opening Simple backup restore, that there is no restore file.

---

### Post by steveb001 on 2007-08-22
No restore file is there.  Also, the XP share is set to everyone - full control

---

### Post by mikeyphi on 2007-08-22
You've got a process id - so something is happening somewhere!!!!

All I can offer now is - recheck _all_ the settings in the backup config.

---

