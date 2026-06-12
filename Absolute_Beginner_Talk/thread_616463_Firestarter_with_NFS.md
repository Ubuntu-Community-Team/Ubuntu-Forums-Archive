---
title: "Firestarter with NFS"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-18
I have just had a strange event and was wondering if anyone had any similar experiences ....

I have been struggling to get NFS working but just succeeded.  My solution was to stop the firewall (on both machines) using Firestarter.  All worked.  Before that I had entered an inbound and outbound policy to allow NFS.  Not only did it not work but for some reason every other port was blocked by default.

I made the changes with Firestarter since NFS did not work with the firewall running and I thought that this would be the easiest way of stopping it since Firestarter has a GUI.

But ...  I found that when I started up Firestarter again and having removed the NFS policies that everything was still blocked.  So I uninstalled Firestarter and rebooted.  Everything back to normal working.

I am not exactly sure what to do next.  I like to use Firestarter to start and stop IP tables when I am testing something that does not work but I do not want the pain of managing IP tables without a GUI.

---

### Post by overdrank on 2007-11-18
> **expatCM said:**
> I have just had a strange event and was wondering if anyone had any similar experiences ....

I have been struggling to get NFS working but just succeeded.  My solution was to stop the firewall (on both machines) using Firestarter.  All worked.  Before that I had entered an inbound and outbound policy to allow NFS.  Not only did it not work but for some reason every other port was blocked by default.

I made the changes with Firestarter since NFS did not work with the firewall running and I thought that this would be the easiest way of stopping it since Firestarter has a GUI.

But ...  I found that when I started up Firestarter again and having removed the NFS policies that everything was still blocked.  So I uninstalled Firestarter and rebooted.  Everything back to normal working.

I am not exactly sure what to do next.  I like to use Firestarter to start and stop IP tables when I am testing something that does not work but I do not want the pain of managing IP tables without a GUI.

Hi what I would recommend is using this link to enable sharing and still use firestarter
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)
I am sure there are other ways of sharing but I do not know of them :oops:  :D

---

### Post by fain on 2007-11-18
this is what i used
[http://ubuntuforums.org/showthread.php?t=352486]("http://ubuntuforums.org/showthread.php?t=352486")

---

### Post by expatCM on 2007-11-18
overdrank .....   well nice idea but ....  the problem is that when I put Firestarter back on the system it blocks 100% of everything instantly.  There are no policies set at all.  So I have to click to disable the firewall and then uninstall / reboot to get any form of Internet or network connection.

fain .... looked at your suggested  thread, very interesting.  There is a big difference between this setup and mine.  In the link there are a very small number of ports, in mine there is quite a large selection which would make this a large task.

I do not know what is happening here .... something is wrong with Firestarter or the iptables ....   I hate unexpected headaches like this ....

---

### Post by fain on 2007-11-18
What that how-to does is force nfs to use a few selected ports unlike the default which is a large random range. That way you can open just those ports. I have this set up with firestarter and i get a connection every time.

---

### Post by expatCM on 2007-11-18
ah ... got it, thanks ...

I will work through that as soon as I can figure out what has gone wrong with Firestarter.

---

### Post by fain on 2007-11-18
Np :)

---

