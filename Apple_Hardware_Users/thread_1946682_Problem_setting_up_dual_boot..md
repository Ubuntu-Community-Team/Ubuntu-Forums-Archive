---
title: "Problem setting up dual boot."
date: 2012-03-25
forum: Apple Hardware Users
---

### Post by Kopkins on 2012-03-25
Hey, so i've set up dual boot on a couple of friends PC's, and have been trying to do it on my mac without success. I can begin to boot ubuntu, but after a little while it come up with a built in command line that tells me type help for a list of builtin commands. It also gives the error that it is unable to find a medium containing a live filesystem. Only way out of that screen is to use the reboot command or force shutdown. 

Thanks for any help.
Kopkins

---

### Post by ranger1021994 on 2012-03-25
I guess u try to do Alt+F9/F8 Just try it with couple of Function keys...
I had this problem but sumhow this solved it

---

### Post by Kopkins on 2012-03-25
> **ranger1021994 said:**
> I guess u try to do Alt+F9/F8 Just try it with couple of Function keys...
I had this problem but sumhow this solved it

Thanks for the reply, but this really isn't helpful at all. The suggestion didn't change anything for me in the end, it just change how I get there slightly.

Kopkins

---

### Post by pindar on 2012-03-26
> **Kopkins said:**
> Thanks for the reply, but this really isn't helpful at all.
That may be because your post is confused and confusing. You don't mention which hardware you are using, which version of ubuntu, how and where you installed, and the error message you paraphrase (you don't quote it) says something about a live filesystem, so this looks like you're running from a live cd, not from an installed system. How is anyone going to help you? We can't read your mind or magically know what you're doing.

---

### Post by Kopkins on 2012-03-26
> **pindar said:**
> 

Thanks for pointing out my idiocy, sincerely. 

I have a MacBook pro 8.1 
With:
intel i5 
intel HD Graphics 3000
2 x 2Gb Memory

When trying to boot Ubuntu 11.10 from the LiveCD or install from the CD I get this.
I haven't been able to install it anywhere yet. It just starts to boot from the LiveCD, then fails.

What shows up and what I do follow:

```
BusyBox v 1.18.4 (Ubuntu 1.18.4-2ubuntu2) builtin shell (ash)

# it doesn't always display this next line.
Unable to find a medium containing a live filesystem.

Enter 'help' for a list of builtin commands

(initramfs)

(initramfs) help
# enter help

. : [ alias  break cd chdir command continue echo eval exec exit expot false getopts hash help let local printf pwd 
read readonly return set shift test times trap true type ulimit umask ualias unset wait [ [[ ash awk basename 
blockdev cat chmod chroot chut egrep env expr false fbset felflush fgrep find grep gunzip gzip clear cmp cp cut 
deallocut df dnsdomainname du dumpkmap echo hostname ipconfig ip kill ln loadfont loadkeymap ls mkdir mkfifo 
mknod mkswap mktemp modinfo more mount mv openvt pidof printf ps pwd readlink reset run rmdir sed 
setkeycodes sh sleep sort stat static-sh stty sinc tail tee test touch tr true tty umount uname uniq wc wget which yes 
zcat

(initramfs) reboot
# enter reboot, system reboots, I choose OSX instead of boot from disk. 
```

Let me know if I left anything out. 

Thank you,
Kopkins

---

### Post by pindar on 2012-03-26
This appears to be a known problem with some models of the macbook pro; there are several threads in the forum about this problem. [This one]("http://ubuntuforums.org/showthread.php?t=1758739") has at least a workaround, so you may want to try that.

---

### Post by Kopkins on 2012-03-27
> **pindar said:**
> This appears to be a known problem with some models of the macbook pro; there are several threads in the forum about this problem. [This one]("http://ubuntuforums.org/showthread.php?t=1758739") has at least a workaround, so you may want to try that.

Thanks, I was able to install Ubuntu and it runs pretty well except the wireless. Apparently, there is already a fix for this. I went through the whole process, found [here]("http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html"), twice now. The first time it would load the wireless and find all the networks, but would continuously be trying to connect to the network. The second time, up near where the wireless networks would be, it says wireless disabled by hardware switch, and also says somewhere that the firmware is missing. Any ideas?

Kopkins

---

### Post by msarro on 2012-03-28
You will need a USB stick with approximately 700M of free space.

Download the Ubuntu ISO.
Open system information and select the USB disk. Make note of what it says the disk number is (disk0 or disk1).

Open a terminal window and type:
dd if=/path/to/ubuntu.iso of=/dev/diskN bs=1M

Once that is done, reboot the mac (keeping the USB attached) and press/hold the C button to start booting off of the CD. You should no longer get the "unable to find live filesystem" error since it'll find the filesystem on the USB.

---

### Post by Kopkins on 2012-03-29
Hey all,

My system is up and running, and my wireless adapter is recognizing the networks, but it can't seem to ever connect to them. I followed the procedure found [here]("http://homepage.uibk.ac.at/%7Ec705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html"). I don't understand why it won't connect. I am running 11.04 now.

Thanks
Kopkins

---

### Post by Kopkins on 2012-03-29
Hey,

Installed Precise Pangolin today and the wireless didn't work by default which surprised me a little, but I was able to extract the firmware and get it working.

Thanks to everyone who helped me out. 
Kopkins

---

