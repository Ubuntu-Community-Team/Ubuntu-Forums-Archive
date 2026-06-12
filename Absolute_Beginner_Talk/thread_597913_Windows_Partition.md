---
title: "Windows Partition"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by lilkeith07 on 2007-10-30
I just installed Ubuntu 7.10 and its the first version i have had and I am quite amazed at how well it works and how easy it was to set up. Forgive me for anything I miss or is irrelevant I am really knew to this.  I have one problem though I have Ubuntu on one partition and then windows vista on another. Now since I installed everything a couple of days ago and I could see my windows partition mounted on the desk top and from the places menu and now its suddenly gone from both locations, I did not unmount it or anything. When I did a restart it was gone. I know its still there because I can boot into Windows or see it through the Wine menu. Is there anyway to get the partition back onto the desktop or places menu? Thanks in advance.

---

### Post by Six_Digits on 2007-10-30
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Try that, re-post if you have any problems.

---

### Post by lilkeith07 on 2007-10-30
I got this error when finishing it up:


Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

---

### Post by lilkeith07 on 2007-10-31
wow never mind Im a huge idiot...haha

if anybody else has this problem its because the last time I was in windows it didn't shut down properly so it didn't register so I just had to restart and then close down windows normally.

---

