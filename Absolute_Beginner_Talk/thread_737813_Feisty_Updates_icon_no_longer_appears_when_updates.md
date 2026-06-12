---
title: "Feisty Updates icon no longer appears when updates are available"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-03-27
A couple of days ago my computer froze while using Feisty, so I had to power it down by holding the power button.

When I tried to boot up into Ubuntu again, the boot process got stuck half way (see the note at end of this post for details), and when this happened once before, someone explained to me that, because I abnormally powered down the laptop, a bunch of inodes were probably orphaned and other open files weren't closed properly. So they told me that where the bootup gets stuck, at the cursor I should do:

```
e2fsck -y /dev/hda2
```

Then: Once it's done, "exit" to reboot the box and it should be fine.

I did all that and sure enough, the computer booted up fine and has been working fine since. But there are a few small major residual problems that cropped up as a result. The most major one I've noted so far is that the new updates icon that appears on the top panel when new Feisty security updates etc are available, is unable to appear. The little message appears that "new updates are available"-- but the icon that is supposed to appear on the top panel does not. And in its absence, I do not know how to trigger the updates window to open and start its work. What can I do to fix this problem, so the new updates icon will again start appearing when needed?

Thanks.


The below is merely supplemental info to explain what happened, should anyone need to see it--
----------------------------------------------------------------------------------------

Here is what happened when I tried to reboot into Feisty a few days ago after the computer had froze up: First Grub came as it should. I chose Ubuntu, and then after the Ubuntu boot screen came up with the progress bar, midway through the following screen came up:

```
/dev/hda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (i.e. without -a or -p options)
fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
bash: apt-get command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
bash: apt-get: command not found
root@swarup-laptop:~#
```

---

### Post by c-ron on 2008-03-28
Hi,
AFAIK, the two packages needed for the update notifications are:
notification-daemon & update-notifier

Try (re)installing them if they're misbehaving.

---

### Post by swarup on 2008-03-28
> **c-ron said:**
> Hi,
AFAIK, the two packages needed for the update notifications are:
notification-daemon & update-notifier

Try (re)installing them if they're misbehaving.

I tried going into Synaptic Package Manager and "reinstalling" both of these. But it didn't have any effect. I am wondering: would it make any difference if I instead "remove" or "completely remove" and then reinstall? I was going to do the "completely remove" but it says it will also remove the "configuration files" and I didn't know if that would harm something. 

Also as an aside: By opening Synaptic Package Manager I also realized that the Synaptic application itself has also now become defective due to what I described in my first post above. That is, when you do any search on Synaptic, it lists all the applications it has found-- but next to each application there used to be a check box indicating whether the application was already installed or not. And you could check or uncheck the box. Now that entire column of check boxes is itself GONE. 

And there are certain other icons in Synaptic as well as in the OS in general which still function fine, but do not appear the way they used to. For example, in Synaptic there is an option for "Mark All Upgrades", but the icon for it is now just a box with a red "X" in it.

---

### Post by philinux on 2008-03-28
I would be tempted to run fsck again.

But first, seeing as you can get into the system I'd back up anything important to a usb stick or external drive.

Reboot and choose recovery mode. 

Then

fsck -v /dev/xxx

If it finds any errors it will ask you if you want it to fix them.

---

### Post by swarup on 2008-03-28
> **philinux said:**
> I would be tempted to run fsck again.

But first, seeing as you can get into the system I'd back up anything important to a usb stick or external drive.

Reboot and choose recovery mode. 

Then

fsck -v /dev/xxx

If it finds any errors it will ask you if you want it to fix them.

Sounds great-- I'll try it now and let you know what happens.

---

### Post by c-ron on 2008-03-28
> **swarup said:**
> I am wondering: would it make any difference if I instead "remove" or "completely remove" and then reinstall? I was going to do the "completely remove" but it says it will also remove the "configuration files" and I didn't know if that would harm something.

It could very well be that it's the configuration files that are messed up. So if you 'completely remove' the packages and then reinstall, it should write new default configuration files.

---

### Post by swarup on 2008-03-28
> **c-ron said:**
> It could very well be that it's the configuration files that are messed up. So if you 'completely remove' the packages and then reinstall, it should write new default configuration files.

I see. Actually, when I shut down the computer and then rebooted, the updates icon has now miraculously started to appear again, when it hadn't for several days. And I didn't do anything to fix it. Although I did do the "reinstall" I mentioned above. Perhaps that actually fixed it, so it worked the next time it was rebooted. 

When I clicked on the update icon though, it did not manage to open the password window or do the download. Instead I had to right-click on that update icon and select the option to "install all updates". And THEN it gave me the password window and did its work. Anyhow, it is a step in the right direction. Let's see how it goes the next few times updates come in. Thanks.

---

### Post by swarup on 2008-03-28
> **philinux said:**
> I would be tempted to run fsck again.

But first, seeing as you can get into the system I'd back up anything important to a usb stick or external drive.

Reboot and choose recovery mode. 

Then

fsck -v /dev/xxx

If it finds any errors it will ask you if you want it to fix them.

I mentioned above that the updates icon has again started to appear when updates are available. But Synaptic Package manager is still defective as described, as are some other icons in the OS such as the dial-up modem icon when open on the toolbar.

So I thought I would try your suggestion above and see what happens. I rebooted in recovery mode, and then did fsck -v /dev/xxx as instructed above. Here below is what came up on the screen next:

```
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/xxx

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>.
```

So what should I do now?

My computer is otherwise running fine--except for the defects described in Synaptic etc. I am actually writing this post from that very laptop in which the above code has appeared. Is there something wrong there, and should I try running e2fsck as it describes above? If so, please give the exact command that I should type when get o the cursor after rebooting into recovery mode.

---

### Post by philinux on 2008-03-28
The xxx was whatever your partition is like e.g. sda1 sda2 hda1 hda2

---

### Post by swarup on 2008-03-28
Ok, I followed the directions and I tried to do the fsck--

```
fsck -v /dev/hda2
```

But then the following came on the screen:

> /dev/hda2 is mounted.
Warning!!! Running e2fsck  on a mounted filesystem may cause SEVERE filesystem damage. Do you really want to continue (y/n)?

So when I saw this, I became concerned and opted not to do anything. What should I do now? Will it cause damage to the filesystem if I continue?

---

### Post by c-ron on 2008-03-30
> **swarup said:**
> Ok, I followed the directions and I tried to do the fsck--

```
fsck -v /dev/hda2
```

But then the following came on the screen:



So when I saw this, I became concerned and opted not to do anything. What should I do now? Will it cause damage to the filesystem if I continue?

Boot from the LiveCD and run the fsck again.

---

