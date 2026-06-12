---
title: "SeamlessVirtualization"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-28
I've followed this guide: [http://ubuntuforums.org/showthread.php?t=342631](http://ubuntuforums.org/showthread.php?t=342631)

and have VMWare set up with Windows XP Pro.   I'm trying to follow this guide here to get SeamlessVirtualization working with it: [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

But it really confuses me, especially with getting Window XP Pro's address.

Can anyone help me with this?

---

### Post by dreadlord_chris on 2007-06-28
To get XP's IP:
(from your virtual XP) Start > Run > cmd <ENTER>
in the windows that opens
```

ipconfig

```

---

### Post by Hork on 2007-06-29
Thank you!

I got the IP, shutdown the VM server, then did this:
```
Files\Internet Explorer\iexplore.exe" 192.168.210.128:3389 -u taylor
Autoselected keyboard map en-us
ERROR: connect: No route to host

```

(I have no password and my username for Windows is taylor)


Is there any way to fix this?

---

### Post by Hork on 2007-06-29
Did I get the IP incorrectly?

---

### Post by Hork on 2007-06-29
Whoops, that code window should be:

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 192.168.210.128:3389 -u taylor

```

---

### Post by Hork on 2007-06-29
Hmmm, I honestly can't figure out what's going on here.

---

### Post by pveith on 2007-06-29
@Honk: You are not supposed to shut down the Windows VM. Just log your windows-user off (You should see the Windows Login-Screen in VMWare). If you are running vm-player you have to leave the interface running (if i remember correctly). In VMware-Server you can close the VMware-Interface and the server will keep Windows up and running.

Then the next thing would be to enter the rdesktop code-line.

Hope that helps...

---

### Post by Hork on 2007-06-29
```
taylor@ubuntu:~$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 192.168.210.128:3389 -u taylor
Autoselected keyboard map en-us
ERROR: connect: Connection timed out

```

Thank you, I feel like I'm a step closer, but not quite there yet.

---

### Post by gentleStu on 2008-02-04
Hi Hork,

I've just responded to another thread that seems very similar to your problem: [http://ubuntuforums.org/showthread.php?t=624918](http://ubuntuforums.org/showthread.php?t=624918).  

Hope this helps

Stuart

---

