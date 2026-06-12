---
title: "I 'scrubbed' my Ubuntu..."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-03-05
Well I think I made a big mistake...
I misread (maybe misunderstood) this HowTo:
[Securely clear free hard drive space with Scrub]("http://ubuntuforums.org/showthread.php?t=333309")
I understood it to mean it would clean up unnecessary files; in fact, I had to stop Scrub when I realized it had created a 5GB 'junk' file.
and...
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             10080520   9952800         0 100% /

Yes it is quite full. This 'junk' file's supposed to be delete once Scrub's done its job. Of course, I didn't delete it.
Now I'm still on Internet. The thing is I had just finished upgrading (Edgy) this box when I tried Scrub. I do have a Dapper backup which I could use to restore (I guess!) but would like to avoid having to upgrade again.

Any thought as to what I should do? Thanx in advance.

---

### Post by Jussi Kukkonen on 2007-03-05
EDIT: Ahh, I think I understand now .... You did not want to clear your disk at all.

Sorry, but using an industrial quality data remover pretty much guarantees the data is  ****ed beyond repair...

---

### Post by xyz on 2007-03-05
Hi Jussi,
Thanks for your reply.
I pretty much figured there was no way to solve this other than restoring from my *backup.tgz*

There was no room left at all in *hda2* and yet the OS got restored but not like I thought it would. Bear with me this is getting a bit confusing to me!

As I said in my 1st post, I had just finished upgrading this box to Edgy when I began using Scrub. I Ctrl + C Scrub the minute I realized it had created a 5.3 GB 'junk' file; that's when I realized it was not "cleaning up unnecessary files" but more whipping my partition.

My *backup.tgz* was a Dapper backup yet now I'm still running Edgy. The system did not ask me to reboot after restoring it!

Should I be afraid of rebooting? Sooner or later I'm going to have to shut down this box!

These are the last couple of lines of the restoring process:
> /home/th/my stuff/infos ubuntu/SetCheckDiskNumberOptions
/home/th/my stuff/infos ubuntu/Simple_Comme_Linux.pdf

gzip: stdout: No space left on device


I'm afraid restoring did not go all the way to the end?

Then I proceeded to delete the 'junk' which I had created as a destination file follwing the Scrub installation....and I'm back with a 48% used space.

Thanks for reading.

---

### Post by xyz on 2007-03-05
Well I rebooted and eveything's fine.

Still a mystery remains:

how can I still be running Edgy after restoring the OS using a Dapper backup.tgz file?

---

### Post by Jussi Kukkonen on 2007-03-05
xyz, the restore was definitely not finished: "No space left on device" means just that... Have you tried removing the junk file the scrub instructions tell you to remove?

> 
how can I still be running Edgy after restoring the OS using a Dapper backup.tgz file?
Can't tell, if you don't tell how you are creating that file...

---

### Post by xyz on 2007-03-06
> **Jussi Kukkonen said:**
> xyz, the restore was definitely not finished: "No space left on device" means just that... Have you tried removing the junk file the scrub instructions tell you to remove?


Can't tell, if you don't tell how you are creating that file...
Hi Jussi,
> "No space left on device" means just that...
OK I understand now. I thought that ,despite the fact that the restoring process didn't finish the job all the way, that it had restored some and therefore copied over what was there.
I didn't know restoring had to go all the way to really take effect. Now I do!

my *backup.tgz* was created using this command line as root:
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /
```
...and to restore:
```
tar xvpzf backup.tgz -C /
```
I hope this makes it a little cleare and thank you very much for your time.

---

