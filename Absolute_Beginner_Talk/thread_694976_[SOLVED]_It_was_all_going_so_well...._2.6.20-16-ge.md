---
title: "[SOLVED] It was all going so well.... 2.6.20-16-generic boot problem"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by AntonyG on 2008-02-12
Hi All

It was all going so well, I was using Kubuntu 7.04 for about 3 or 4 months now, nothing clever, just using the basics.

I don't do anything technical since I got my wireless card working in the early days, the only thing I do is keep my packages up to date automatically using Adept Notifier when it tells me to.

Now for some reason last week my machine suddenly fails to boot up. It goes through the splash screens, and just when the status bar gets to the end the screen flickers, goes blank, and I'm left with a black screen with flashing cursor and nothing else. So I was really stuck about what to do and what was wrong.

By default grub tells me its normally booting Ubuntu, kernel 2.6.20-16-generic

So I tried the other boot option in grub Ubuntu, kernel 2.6.20-15-generic and this works FINE!!! :)

So basically, something is broken, and I'm fairly sure I didn't do anything apart from running the automatic adept-updater, and would kind of like to know how to fix it without the cheating of using kernel 2.6.20-15 for no particular reason.

If you need any boot-logs or anything then just let me know, but please tell me how to get them as  I'm sure you've guessed I'm a new guy.

Thanks in advance!

Antony

---

### Post by Herman on 2008-02-12
:) Hello AntonyG,
It sounds like maybe the new kernel doesn't quite agree with something in your hardware. I'm just guessing, but I would probably just keep booting the kernel that does work. Someday another new kernel will come out that supercedes the new one you just got and hopefully that one will work and you can jump to that one then.
Maybe some one else will have a suggestion too. I will be interested in what others have to say as well.
Regards, Herman :)

---

### Post by AntonyG on 2008-02-13
Thanks

I agree, it must be something with that kernel, but I was running that version of the kernel just fine for months very happily without problems.

Cheers

Antony

---

### Post by rkd on 2008-02-13
I have seen reports that sometimes a kernel update makes errors in constructing the new Grub boot menu.

If you showed us your current menu.lst file here in a post, maybe we could spot some problem with it.

You can display your menu.lst file by opening a Terminal and entering the following command```
cat /boot/grub/menu.lst
```Then you can use the mouse to highlight all of the text that the cat command displayed in the Terminal and go to the Edit menu and select Copy to copy the text to the clipboard. Then when creating a post here in the forum, use Edit -> Paste to paste the clipboard into the post.

Or you could use the Manage Attachments button (below the post composition box under Additional Options) to attach the /boot/grub/menu.lst file to your post instead of putting it into the body of your post.

---

### Post by AntonyG on 2008-02-13
Thanks very much for your post and helpful instructions

Below is the grub boot menu.lst

I realise that I could change the default value to automatically boot kernel 2.6.20-15-generic, but that feels like it wouldn't solve the problem with the 2.6.20-16 kernel which I was running for months without any problems.

Anyway, thanks again for helping, and let me know if this triggers any good ideas.

Antony


```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c9d51623-1026-4563-80d0-dd59bcab4671 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=c9d51623-1026-4563-80d
0-dd59bcab4671 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=c9d51623-1026-4563-80d
0-dd59bcab4671 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c9d51623-1026-4563-80d
0-dd59bcab4671 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c9d51623-1026-4563-80d
0-dd59bcab4671 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

---

### Post by rkd on 2008-02-13
The menu.lst file doesn't seem to show any sign of the problem that I read about on another thread, so the simple solution doesn't apply here.

I guess the next thing to do is to compare the system log messages from booting the two versions of the kernel.

Here is how I get the messages from the system log.  First, make note of the time. Then boot the computer using the working version of the kernel. When the boot is done and you are logged in, go to the System menu, and select Administration, then System log. When log viewer window opens, find syslog in the left pane of the window and click on it. Then in the right pane scroll to the time you booted the computer. You should see a message that reads something like "Inspecting /boot/System.map-2.6.20-15-generic". Use the mouse to highlight and copy to the clipboard all the messages from there to the end of the log. Then go open an editor (perhaps Applications -> Accessories -> Text Editor), paste the clipboard into the editor, then save the file with a name like log15. 

Now close all the windows, note the time again, and try to boot the computer to the new kernel. When it stops on the black screen, could that be like a big terminal window, not a dead machine? Try entering the command pwd to see whether it can tell you what the current directory is. If it asks you to login, try to do so, then try pwd again. If it seems to be a big terminal window, try the following commands:```
cd /var/log
sudo cp syslog savesyslog
```If you can't get it to take any commands, don't let it worry you.

Boot back to the working kernel, and open the log viewer again. If you were able to get the nonworking kernel to accept your commands and make a copy of the syslog, go to the File menu, select Open, find the savesyslog file and open it. Find the point in the log where the time is the time of the attempt to boot the nonworking kernel. Copy to the clipboard the messages from there to the end of the log, then open an editor, paste the clipboard into the editor, and save it with a name like log16.

If you were not able to get the nonworking kernel to accept commands, when you get back to the working kernel and into the log viewer, scroll through syslog to the time of the attempt to boot the nonworking kernel. Copy to the clipboard all the messages from there up to the start of the boot back into the working kernel. Open an editor, paste the messages into the editor, and save as log16.

Finally, make a new post here and use the Manage Attachments button to attach log15 and log16 to the post. (The Manage Attachments button is a bit below the box into which you type your post -- below Additional Options.)  I suggest making them attachments rather than putting the text into the body of the post because there is so much text. 

When I get a chance, I'll compare them and see whether there are any clues to the problem there. Of course, you can look at them, too -- maybe you'll spot a message that leads you to the solution without more help.

---

### Post by dstew on 2008-02-13
Just a quick thought. Look into your /boot directory and make sure the kernel and ramdisk images are in there.

---

### Post by rkd on 2008-02-13
Good idea, dstew, and that reminds me that I recently saw one thread about boot problems where it turned out that one of the boot files, while present, had length 0.

AntonyG:

So one more thing you could do is post the output of an ls command. In a Terminal, do the following commands:```
ls -l /boot
ls -l /boot/grub
```Then use the mouse to highlight and copy to the clipboard the ls commands and all the output they produced. Paste that text into a post.

---

### Post by AntonyG on 2008-02-13
Crikey, this is really good stuff guys.... I'll do the second tip first... below are the "ls" commands of the 2 directories... there doesn't seem to be any 0 btye files, but I'll paste results here to see if you spot anything....

I'll get on with the other idea now of obtaining the syslogs on each boot... I'll be back soon

thanks

```

antony@antony-desktop:~$ ls -l /boot
total 33508
-rw-r--r-- 1 root root  414210 2007-04-15 09:07 abi-2.6.20-15-generic
-rw-r--r-- 1 root root  414274 2008-02-01 03:43 abi-2.6.20-16-generic
-rw-r--r-- 1 root root   83234 2007-04-15 06:33 config-2.6.20-15-generic
-rw-r--r-- 1 root root   83217 2008-02-01 00:12 config-2.6.20-16-generic
drwxr-xr-x 2 root root    4096 2008-02-06 22:08 grub
-rw-r--r-- 1 root root 7178043 2007-05-15 22:45 initrd.img-2.6.20-15-generic
-rw-r--r-- 1 root root 6911184 2007-04-17 06:25 initrd.img-2.6.20-15-generic.bak
-rw-r--r-- 1 root root 6949728 2008-02-06 19:27 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 6948649 2007-12-19 20:49 initrd.img-2.6.20-16-generic.bak
-rw-r--r-- 1 root root   94600 2006-10-20 12:44 memtest86+.bin
-rw-r--r-- 1 root root  806942 2007-04-15 09:08 System.map-2.6.20-15-generic
-rw-r--r-- 1 root root  807071 2008-02-01 03:44 System.map-2.6.20-16-generic
-rw-r--r-- 1 root root 1745100 2007-04-15 09:07 vmlinuz-2.6.20-15-generic
-rw-r--r-- 1 root root 1747596 2008-02-01 03:43 vmlinuz-2.6.20-16-generic


antony@antony-desktop:~$ ls -l /boot/grub
total 212
-rw-r--r-- 1 root root    197 2007-05-15 22:45 default
-rw-r--r-- 1 root root     15 2007-05-15 22:45 device.map
-rw-r--r-- 1 root root   8660 2007-05-15 22:45 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-05-15 22:45 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-05-15 22:45 installed-version
-rw-r--r-- 1 root root   9152 2007-05-15 22:45 jfs_stage1_5
-rw-r--r-- 1 root root   4908 2008-02-06 22:08 menu.lst
-rw-r--r-- 1 root root   4908 2008-02-06 19:27 menu.lst~
-rw-r--r-- 1 root root   7860 2007-05-15 22:45 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-05-15 22:45 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-05-15 22:45 stage1
-rw-r--r-- 1 root root 110132 2007-05-15 22:45 stage2
-rw-r--r-- 1 root root   9980 2007-05-15 22:45 xfs_stage1_5

```

---

### Post by AntonyG on 2008-02-13
Right - I'm back, and I think you're onto something.

Attached is boot-15.txt, which shows the system log from boot up all the way through to working desktop for the 1.6.20-15 kernel.

And boot-16.txt, the logs for bootup to a failed blank screen (not a command prompt).

Of particular interest to you guys are probably the line near the end of the file... totally foreign to me though.

Feb 13 21:43:37 antony-desktop kdm: :0[5597]: IO Error in XOpenDisplay
Feb 13 21:43:37 antony-desktop kdm[5563]: X server for display :0 terminated unexpectedly
Feb 13 21:43:37 antony-desktop kdm[5563]: Display :0 cannot be opened
Feb 13 21:43:37 antony-desktop kdm[5563]: Unable to fire up local display :0; disabling.

Thanks even more for your help so far and perfectly clear instructions.

I look forward to your response.

Regards

Antony

---

### Post by dstew on 2008-02-13
> the screen flickers, goes blank, and I'm left with a black screen with flashing cursor and nothing elseThis goes with those error messages, and suggests that your xserver is not working properly. DId you try ctrl-alt-F1 when you get the black screen/blinking cursor? If you get a command line, you know your kernel is basically OK. Then, you can try to reconfigure the xserver with the command```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by AntonyG on 2008-02-17
Thanks very much, that helps a lot.

I do indeed get a login prompt when I press Ctrl+Alt+F1 - so my Kernel is fine :)

I ran "reconfigure xserver-xorg" and basically answered the default answer to every question as there was way too much I didn't understand.

And after this my system could boot up in kernel 2.6.20-16-generic. So thats great...

...except everything looks blocky and chunky and not as smooth.. I assume this is now because my xorg.conf file is now using basic device drivers and graphics settings.

I tried replacing my old xorg.conf file but again this stopped my system from working.

So what I would like to know is how come my system works fine with kernel 2.6.20-15 and my original xorg.conf file. but doesn't work with kernel 2.6.20-16 and the exact same xorg.conf file?

I've attached my original xorg.conf file, as well as the xorg.conf file which I got after reconfiguring my xserver, which does work with kernel 2.6.20-16 but looks a bit basic. If anyone spots anything wrong with my original settings then I'd very much appreciate any tweaks you think I should make.

Thanks

Antony

---

### Post by rkd on 2008-02-18
I've been looking at the two log files -- the ones from booting the old and new kernel.  There are lots of differences between the two, making it hard to pin down what differences are important.

One difference I found that might be the problem is that with the old kernel, the syslog has messages about loading the Nvidia restricted driver, while with the new kernel, no such messages appear.

A little web searching led me to a page on which it said that whenever the kernel is updated, the Nvidia driver must be reinstalled.  The page is here:

   [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

I think you didn't mention reinstalling the Nvidia driver after the kernel was updated, so if that page is correct about the need to do so, this very well could be the problem.

That page describes three methods of correcting the problem plus it has lots of troubleshooting advice. I've tried to pick out the steps that apply to you.  I encourage you to look at the page yourself to see whether you agree with the steps that I think are right before you do them. I might have misunderstood something about your system. Ask about anything you aren't sure of.  I think what you need to do is:
```
sudo apt-get  update
sudo apt-get  install  linux-generic
sudo apt-get  install  nvidia-glx-new
sudo cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure  -phigh  xserver-xorg 
sudo nvidia-xconfig  --no-composite
```
Notice that in the last command, there are two hyphens before no-composite.

I see you ran dpkg-reconfigure recently.  If you run it with the -phigh option, as shown above, it won't ask all those questions you had to answer the other time.  If you don't want to take the default answers, you can leave off the -phigh option this time, too.

After running those commands, restart X by typing Ctrl-Alt-Backspace (hold down the Control and Alt keys and press the Backspace key). This will stop all programs you have running, so make sure there is no unsaved work before you do that. The screen will drop back to a text screen for a few moments, then the login screen that appears right after booting will appear. Login and see whether the display is working correctly.

I left out a step that he says creates a menu entry for running the nvidia-settings program.  Include that if you like.  Without it, you can still run the program from a Terminal.

I added the apt-get update at the beginning, just to make sure that the package manager is up-to-date with the respositories.

Now, I don't know why all those steps are necessary when we have the Restricted Drivers Manager.  We certainly don't have to do all this stuff when we install Ubuntu the first time. I don't know why you couldn't just use the Restricted Drivers Manager to reinstall the Nvidia driver.  That page is specifically for Ubuntu Feisty, so it seems that the writer would not overlook a much simpler solution such as using the Restricted Drivers Manager, so maybe it doesn't work after a kernel update.  But if I were in your situation, I think I would first try using Restricted Drivers Manager to enable the Nvidia driver rather than the several steps given above.

When you first installed Ubuntu, do you remember going to System -> Administration -> Restricted Drivers Manager and enabling the Nvidia driver?  If you did not do that, but installed the Nvidia driver some other way, perhaps that is why things didn't go well in the update of the kernel.  Or maybe it doesn't matter how the Nvidia driver was installed.

---

### Post by rkd on 2008-02-18
Oops, I forgot to answer a question of yours from your most recent post.  Why does the xorg.conf file that works with kernel 2.6.20-15 not work with kernel 2.6.20-16? I think it is because the xorg.conf names the driver to use, "nvidia" in your case, and I think the nvidia driver is not present in kernel 2.6.20-16.

If we get the nvidia driver installed properly in kernel 2.6.20-16, you could test this explanation by copying the xorg.conf file that worked with kernel 2.6.20-15 into /etc/X11/xorg.conf to see whether it works again after getting the nvidia driver installed.

---

### Post by bumanie on 2008-02-18
Following the last kernel update in feisty, my computer ran very slow, that is internet and everything else was slow. I removed the new kernel from synaptic and the computer is now basically performing like it did before the kernel upgrade. I boot on the previous kernel.

---

### Post by AntonyG on 2008-02-25
Thanks Everyone

Especially rkd.

I reinstalled the drivers, and restored my original xorg.conf and it all worked.

Problem solved.

Thanks very much

Antony

---

### Post by rkd on 2008-02-25
Good news!  I'm glad you got it solved.

Did you reinstall the drivers using the Restricted Drivers Manager, or did you use apt-get to install linux-generic and nvidia-glx-new?

If you are satisfied that the problem is solved, please use the Thread Tools link up near the top of the page to mark the thread as solved. You are the only one who can do that.

---

