---
title: "Ubuntu unreachable"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-12
I was trying to remove Amarok to reinstall it.  Somehow, Synaptic began to remove EVERYTHING.  I hit the reboot button.  I came back in cmd line and typed in enough commands to get the gdm to start.  However, once it reached the first brownish screen nothing further happened.

I rebooted to recovery mode but the same thing happened.  On the CD I tried booting into the first hard disk but got the same results.

Right now I'm on the CD so if anyone can help me at least I can reach a terminal.

My main concern is saving my contacts and mail in Thunderbird2.  No, this isn't backed up because just as I finished updating everything I tried to fix the sound, for the 100th time.

I'm hoping someone out there knows how to restore the system without a complete reinstallation.

Thanks,
Bobland

---

### Post by [S|G] on 2007-05-12
Your settings are most likely safe in your home directory. Assuming you didn't place it in a separate partition, you might want to copy your entire /home/youruser directory to somewhere else and reinstall. Then just copy everything back and you'll have all your settings, contact lists and documents back.

If you can, however, get into the command line with no gui, you can try to reinstall the base desktop:
```
sudo apt-get install ubuntu-desktop
```
You can do that from command line with no need to start gnome.

---

### Post by BobLand on 2007-05-12
SG,
That put me back in business.  Still a bit of strangeness going on but I'll contend with it as it arises.

Many, many thanks for this tip.
Bobland

---

