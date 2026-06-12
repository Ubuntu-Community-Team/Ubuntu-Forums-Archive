---
title: "USB stalling, how to turn it off?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by penguinbreath on 2008-01-05
On my secondary PC that has USB 1.0, copying data from my camera has always worked very well and very fast.

On my primary that I believe also has USB 1.0, copying data from my camera is slow. It will download an image, then display "stall", then download another image. 
    I believe this is one of those safety things to prevent corrupt data. I am not worried about downloading a corrupt image to my hard drive, since I will probebly notice it and reload it.

I am running Kubuntu 7.04 on my primary, and I don't know how to turn off this ?safety feature?

Any ideas on what it is and how to fix it/turn it off (if possible)?

---

### Post by penguinbreath on 2008-01-06
I heard that I can fix this USB stalling slowdown in Ubuntu by right clicking on the USB icon on the desktop (when I plug in the camera) and going to settings then changing some option.

I tried right clicking on the USB icon in Kubuntu, but I cannot find the option to fix the problem.

Any ideas?

---

### Post by penguinbreath on 2008-01-19
I hope I'm not being rude in bumping this thread for a second time, but I really need help here.

I wanted to buy a USB flash drive for my photos, but now I'm afraid to since I really can't use it like I would with this "stalling"  slow down.


[[IMG]http://img518.imageshack.us/img518/9894/123123fe5.th.jpg[/IMG]](http://img518.imageshack.us/my.php?image=123123fe5.jpg)



Can someone please help?

---

### Post by penguinbreath on 2008-01-27
This will be the last time I ask, as it is the third time I am bumping this thread.  Does anyone know how to fix this, or another place I can ask?

---

### Post by rkd on 2008-01-29
I don't know anything about this, but since nobody else is stepping up, I can suggest a couple of things to try.

1.  Download and burn an Ubuntu 7.04 Live CD image (not Kubuntu), boot from it, plug in your camera, and download some photos, and see whether the stall happens.  If it does, boot again, plug in your camera, do the right-click on the USB icon thing you heard about, and see whether that fixes the stalls.  If it does, then we can try to figure out how to make the equivalent fix in your installed system.

If you can tell me where you learned about the change you make by right clicking on the USB icon, it might help me understand things to read it myself.

2.  Find the application that displays the system log.  I don't know what it is in Kubuntu, but in Ubuntu, you go to the System menu, choose Administration, then choose System Log.  When the application opens, find and select syslog. Scroll down to the last message and note the time of the last message displayed. Plug in your camera and download some photos. Watch for any messages appearing in the system log. If you don't know how to interpret the messages, copy all of the messages from the time when you plugged in the camera to the end and past them into a post here.

3. I did some web searching and found a possible work around. In a terminal window enter:
```
sudo modprobe -r ehci_hcd
```
then plug in the camera and download some photos.  That modprobe command removes the USB 2.0 module, in case it got loaded. That helped some people who were reporting similar problems but didn't help others.

Let me say again that I don't know anything about this problem, but since nobody else seems able to help, I'll give it a try.

---

### Post by penguinbreath on 2008-01-29
> Re: USB stalling, how to turn it off?
I don't know anything about this, but since nobody else is stepping up, I can suggest a couple of things to try.

1. Download and burn an Ubuntu 7.04 Live CD image (not Kubuntu), boot from it, plug in your camera, and download some photos, and see whether the stall happens. If it does, boot again, plug in your camera, do the right-click on the USB icon thing you heard about, and see whether that fixes the stalls. If it does, then we can try to figure out how to make the equivalent fix in your installed system.

If you can tell me where you learned about the change you make by right clicking on the USB icon, it might help me understand things to read it myself.

2. Find the application that displays the system log. I don't know what it is in Kubuntu, but in Ubuntu, you go to the System menu, choose Administration, then choose System Log. When the application opens, find and select syslog. Scroll down to the last message and note the time of the last message displayed. Plug in your camera and download some photos. Watch for any messages appearing in the system log. If you don't know how to interpret the messages, copy all of the messages from the time when you plugged in the camera to the end and past them into a post here.

3. I did some web searching and found a possible work around. In a terminal window enter:
Code:

sudo modprobe -r ehci_hcd

then plug in the camera and download some photos. That modprobe command removes the USB 2.0 module, in case it got loaded. That helped some people who were reporting similar problems but didn't help others.

Let me say again that I don't know anything about this problem, but since nobody else seems able to help, I'll give it a try. 

I tried the  ```
sudo modprobe -r ehci_hcd
``` and things seem to be going slower. Thought I might ask, is there a way I can undo it or is it permanently set?

I do have a Ubuntu 7.10 CD, will this work for the test? I tried my Kubuntu 7.04 CD, and apparently when I tried to shut of my system, it had a problem with my CD drive and shut off the system with the CD drive open.

Thanks for the input.

---

### Post by rkd on 2008-01-29
To turn on the ehci_hcd module again, you can use the same command without the "-r". Or reboot the computer.

I suggested using an Ubuntu Live CD (not Kubuntu Live CD) to try the method of right-clicking on the USB icon because when you are running your Kubuntu system, you cannot see the option you heard about. I figured that booting from the Kubuntu Live CD wasn't worthwhile, since the option probably wouldn't be present in that situation, either, because it is still Kubuntu. I suppose there is some chance that something done during or after installation turned off that option, and it might be present when running from the Live CD. So it can't hurt to try booting from the Kubuntu Live CD to look for that option, but if you don't see it, don't get discouraged.

Booting from the Ubuntu 7.10 Live CD to look for the option on the right-click menu might not be as good as booting from the Ubuntu 7.04 Live CD, only because that menu might have changed between 7.04 and 7.10. But except for the time you spend trying it, it can't hurt to try that. If you don't find the option when using the Ubuntu 7.10 CD, it still probably is worth taking the time to download Ubuntu 7.04 to try it, but I can't guarantee that the option will be there, either, since I really don't know anything about the problem you are having. I'm just suggesting things I can think of to gather some more information about the problem.

I'm not sure whether you are asking something about the system shutting off with the CD drive open. If you are wondering how to proceed from there, I believe that when you turn the computer on the next time, the CD drive will close and open normally.  If you want to make it boot from a CD right away, push any of the first few function keys when the boot menu appears. That will stop the boot timer, and you then have plenty of time to put the CD into the drive and close it. Then use Ctrl-Alt-Del to make it start the boot again.

---

### Post by penguinbreath on 2008-01-29
> To turn on the ehci_hcd module again, you can use the same command without the "-r". Or reboot the computer.

I suggested using an Ubuntu Live CD (not Kubuntu Live CD) to try the method of right-clicking on the USB icon because when you are running your Kubuntu system, you cannot see the option you heard about. I figured that booting from the Kubuntu Live CD wasn't worthwhile, since the option probably wouldn't be present in that situation, either, because it is still Kubuntu. I suppose there is some chance that something done during or after installation turned off that option, and it might be present when running from the Live CD. So it can't hurt to try booting from the Kubuntu Live CD to look for that option, but if you don't see it, don't get discouraged.

Booting from the Ubuntu 7.10 Live CD to look for the option on the right-click menu might not be as good as booting from the Ubuntu 7.04 Live CD, only because that menu might have changed between 7.04 and 7.10. But except for the time you spend trying it, it can't hurt to try that. If you don't find the option when using the Ubuntu 7.10 CD, it still probably is worth taking the time to download Ubuntu 7.04 to try it, but I can't guarantee that the option will be there, either, since I really don't know anything about the problem you are having. I'm just suggesting things I can think of to gather some more information about the problem.

I'm not sure whether you are asking something about the system shutting off with the CD drive open. If you are wondering how to proceed from there, I believe that when you turn the computer on the next time, the CD drive will close and open normally. If you want to make it boot from a CD right away, push any of the first few function keys when the boot menu appears. That will stop the boot timer, and you then have plenty of time to put the CD into the drive and close it. Then use Ctrl-Alt-Del to make it start the boot again.



I have Gnome installed on this computer, and I could not find the right-click option there. Now thinking about it, the Ubuntu live CD should be no different then my Gnome session I believe. I am looking for the old thread I found about the right click option.  I was thinking that I would use the live CD to test things on the default options. Sorry for forgetting to state that I had Gnome installed earlier. 

Apparently someone else had the problem:  [http://ubuntuforums.org/showthread.php?t=330613](http://ubuntuforums.org/showthread.php?t=330613)


Any ideas?


Thanks for the input.

---

### Post by rkd on 2008-01-31
Yes, that thread shows you aren't the only one. I saw other threads reporting similar problems, too. Unfortunately, the only one I saw with a suggested workaround was the one about turning off ehci_hcd, which didn't help you.

If you installed Gnome onto a Kubuntu system, it might not be quite the same as on an Ubuntu system. Even if your system was Ubuntu from the start, something you did since installing it might have changed things in a way that removed that option you heard about. I'll admit that I'm not sure that you'll see the option when booting from the Ubuntu Live CD, but it was something I could think of to check. If it is a lot of bother for you, then don't do it. It could be that the option was added to the right-click menu by some package that you don't have installed. 

Did you look at the system log when you were trying to transfer photos? If not, take a look and see whether there are any messages that give you an idea about what is wrong. If you want to have us look at it, you can put the messages in a post, or if there are a great many of them, put them in a file that you attach to your post.

It might also be informative to look at the messages written during a boot. They are in syslog, too. If it isn't easy to find the messages from your last boot, you could note the time, boot, then you'd know what time to go back to in syslog to find the beginning of the boot. You could copy the messages from the log viewer and paste them into a file that you attach to a post. There will be a lot of them.

If you can find that thread you looked at before where learned about the right-click option, I'd like to read it, too. I'm hoping it gives some clue as to where that option came from.

---

### Post by penguinbreath on 2008-02-01
> **rkd said:**
> Yes, that thread shows you aren't the only one. I saw other threads reporting similar problems, too. Unfortunately, the only one I saw with a suggested workaround was the one about turning off ehci_hcd, which didn't help you.

If you installed Gnome onto a Kubuntu system, it might not be quite the same as on an Ubuntu system. Even if your system was Ubuntu from the start, something you did since installing it might have changed things in a way that removed that option you heard about. I'll admit that I'm not sure that you'll see the option when booting from the Ubuntu Live CD, but it was something I could think of to check. If it is a lot of bother for you, then don't do it. It could be that the option was added to the right-click menu by some package that you don't have installed. 

Did you look at the system log when you were trying to transfer photos? If not, take a look and see whether there are any messages that give you an idea about what is wrong. If you want to have us look at it, you can put the messages in a post, or if there are a great many of them, put them in a file that you attach to your post.

It might also be informative to look at the messages written during a boot. They are in syslog, too. If it isn't easy to find the messages from your last boot, you could note the time, boot, then you'd know what time to go back to in syslog to find the beginning of the boot. You could copy the messages from the log viewer and paste them into a file that you attach to a post. There will be a lot of them.

If you can find that thread you looked at before where learned about the right-click option, I'd like to read it, too. I'm hoping it gives some clue as to where that option came from.

Where would this syslog be located? (path?)

---

### Post by rkd on 2008-02-01
I mentioned that in post #5 in this thread, item 2. Or rather I mentioned that there is an application that displays the contents of various logs, syslog being one of them.

If you prefer not to use that application and look at the file directly, it is /var/log/syslog (and older entries are compressed in files named syslog.1.gz, syslog.2.gz, etc. in the same directory).

---

### Post by penguinbreath on 2008-02-01
Here is my log.  I made my name "me" in this document.

```
Feb  1 14:58:37 me-desktop syslogd 1.4.1#20ubuntu4: restart.
Feb  1 14:58:37 me-desktop anacron[5286]: Job `cron.daily' terminated (mailing output)
Feb  1 14:58:37 me-desktop anacron[5286]: Normal exit (1 job run)
Feb  1 14:58:37 me-desktop postfix/pickup[5156]: 7F2BC746F9: uid=0 from=<root>
Feb  1 14:58:37 me-desktop postfix/cleanup[5963]: 7F2BC746F9: message-id=<20080201195837.7F2BC746F9@me-desktop>
Feb  1 14:58:37 me-desktop postfix/qmgr[5155]: 7F2BC746F9: from=<root@me-desktop>, size=530, nrcpt=1 (queue active)
Feb  1 14:58:37 me-desktop postfix/local[5965]: 7F2BC746F9: to=<me@me-desktop>, orig_to=<root>, relay=local, delay=0.38, delays=0.27/0.09/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Feb  1 14:58:37 me-desktop postfix/qmgr[5155]: 7F2BC746F9: removed
Feb  1 15:01:57 me-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Feb  1 15:01:57 me-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 
Feb  1 15:03:28 me-desktop cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Feb  1 15:17:01 me-desktop /USR/SBIN/CRON[6045]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  1 15:32:03 me-desktop -- MARK --
Feb  1 15:52:03 me-desktop -- MARK --
Feb  1 16:12:03 me-desktop -- MARK --
Feb  1 16:17:02 me-desktop /USR/SBIN/CRON[6111]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  1 16:32:03 me-desktop -- MARK --
Feb  1 16:52:03 me-desktop -- MARK --
Feb  1 17:11:04 me-desktop cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Feb  1 17:16:39 me-desktop kernel: [ 8854.306792] usb 2-1: new full speed USB device using ohci_hcd and address 2
Feb  1 17:16:40 me-desktop kernel: [ 8854.531466] usb 2-1: configuration #1 chosen from 1 choice
Feb  1 17:16:40 me-desktop NetworkManager: <debug info>^I[1201904200.189394] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial'). 
Feb  1 17:16:40 me-desktop NetworkManager: <debug info>^I[1201904200.190970] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_if0'). 
Feb  1 17:16:40 me-desktop NetworkManager: <debug info>^I[1201904200.269384] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_usbraw'). 
Feb  1 17:16:42 me-desktop kernel: [ 8856.660717] usb 2-1: USB disconnect, address 2
Feb  1 17:16:42 me-desktop NetworkManager: <debug info>^I[1201904202.257504] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_if0'). 
Feb  1 17:16:42 me-desktop NetworkManager: <debug info>^I[1201904202.267391] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial'). 
Feb  1 17:16:42 me-desktop NetworkManager: <debug info>^I[1201904202.272090] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_usbraw'). 
Feb  1 17:17:01 me-desktop /USR/SBIN/CRON[6213]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  1 17:32:04 me-desktop -- MARK --
Feb  1 17:38:07 me-desktop kernel: [10140.204964] usb 2-1: new full speed USB device using ohci_hcd and address 3
Feb  1 17:38:08 me-desktop kernel: [10140.432627] usb 2-1: configuration #1 chosen from 1 choice
Feb  1 17:38:08 me-desktop NetworkManager: <debug info>^I[1201905488.132235] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial'). 
Feb  1 17:38:08 me-desktop NetworkManager: <debug info>^I[1201905488.133771] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_if0'). 
Feb  1 17:38:08 me-desktop NetworkManager: <debug info>^I[1201905488.792800] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_usbraw'). 
Feb  1 17:44:29 me-desktop kernel: [10521.319810] usb 2-1: USB disconnect, address 3
Feb  1 17:44:29 me-desktop NetworkManager: <debug info>^I[1201905869.558992] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_if0'). 
Feb  1 17:44:29 me-desktop NetworkManager: <debug info>^I[1201905869.569079] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial_usbraw'). 
Feb  1 17:44:29 me-desktop NetworkManager: <debug info>^I[1201905869.575600] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_311a_noserial'). 
Feb  1 17:52:31 me-desktop cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Feb  1 17:52:56 me-desktop cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Feb  1 18:12:04 me-desktop -- MARK --
Feb  1 18:17:01 me-desktop /USR/SBIN/CRON[8286]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

---

### Post by rkd on 2008-02-01
So it looks like a USB device was connected for 6 minutes starting at 17:38.  I assume that was the camera and you spent about 6 minutes transferring some photos.  Is that correct? Did you get a lot of the stalls during that transfer?  How many photos and how many megabytes total for all the photos?

---

### Post by penguinbreath on 2008-02-01
> So it looks like a USB device was connected for 6 minutes starting at 17:38. I assume that was the camera and you spent about 6 minutes transferring some photos. Is that correct? Did you get a lot of the stalls during that transfer? How many photos and how many megabytes total for all the photos?


It was 20 photos, about 60mb total. Every photo had a "stall".

As far as the USB download time, I might have left the cable in for a minute. ( I am thinking you measured the time between the transfer and removing of the USB device?) Should I re-do the download and time it?

---

### Post by rkd on 2008-02-01
No need to time it exactly.

How much do you remember about that thread in which you read about the option you can get by right-clicking the USB icon? Anything that might help me find it in a search. Was it also about problems with a camera? Do you have any recollection of what the option name was? Do you remember what key words you used when searching?

I haven't used a camera with my system yet, so I just plugged mine in and although it previewed the photos and transferred ones I selected, no icon appeared on my desktop or in the Places menu. Maybe I don't have something turned on to see icons for cameras -- I do see icons for flash drives when I insert them and for CDs when I load them. Do you remember installing something to get the camera icon to appear or changing some configuration setting to get the camera icon to appear? (This is an Ubuntu 7.04 system.)

I'd like to see what modules are loaded, and what messages are in the log at the time of a boot.

The command to display the modules is: ```
lsmod
``` Just copy the output into a post.

To get the messages from the boot, the easiest way is just to reboot your system, then when the boot is complete, copy all the messages from the time you rebooted to the end of syslog.  There might be so many that the posting software won't let you put them into a post; if so, put them into a file and attach the file to the post.

If you don't want to reboot your system, you can look back through the syslog for the last time you booted. If it was before the beginning of the current log, you can open older syslog files from the File menu in the System Log application (or if you are looking at the files directly, just open the other files with your editor). If you have to look at a file that has been compressed (has .gz at the end of its name), use the command ```
sudo gunzip filename
```to uncompress it.

I notice that in your first post, you said you were running Kubuntu 7.04 on the primary, where you are having the stalls. What system are you running on the secondary, where you are not having the stalls?

Although you are running Kubuntu 7.04, you said you are running Gnome. So did you install the ubuntu-desktop package onto the Kubuntu system, or did you get Gnome some other way?

Have you tried temporarily switching back to the Kubuntu desktop to see whether you can find that right-click option then? I don't have a system with both installed, so I don't know how to do that. I remember reading somewhere that you can logoff, then select the desktop from an options menu before logging on.

Okay, that's a bunch of questions.  Please read through this post and try to answer each one of them, then collect the output from lsmod and the boot messages.  You could answer the questions in one post and put the output in another post, if you like.

---

### Post by penguinbreath on 2008-02-01
> 
No need to time it exactly.

How much do you remember about that thread in which you read about the option you can get by right-clicking the USB icon? Anything that might help me find it in a search. Was it also about problems with a camera? Do you have any recollection of what the option name was? Do you remember what key words you used when searching?

I haven't used a camera with my system yet, so I just plugged mine in and although it previewed the photos and transferred ones I selected, no icon appeared on my desktop or in the Places menu. Maybe I don't have something turned on to see icons for cameras -- I do see icons for flash drives when I insert them and for CDs when I load them. Do you remember installing something to get the camera icon to appear or changing some configuration setting to get the camera icon to appear? (This is an Ubuntu 7.04 system.)

I'd like to see what modules are loaded, and what messages are in the log at the time of a boot.

The command to display the modules is:
Code:

lsmod

Just copy the output into a post.

To get the messages from the boot, the easiest way is just to reboot your system, then when the boot is complete, copy all the messages from the time you rebooted to the end of syslog. There might be so many that the posting software won't let you put them into a post; if so, put them into a file and attach the file to the post.

If you don't want to reboot your system, you can look back through the syslog for the last time you booted. If it was before the beginning of the current log, you can open older syslog files from the File menu in the System Log application (or if you are looking at the files directly, just open the other files with your editor). If you have to look at a file that has been compressed (has .gz at the end of its name), use the command
Code:

sudo gunzip filename

to uncompress it.

I notice that in your first post, you said you were running Kubuntu 7.04 on the primary, where you are having the stalls. What system are you running on the secondary, where you are not having the stalls?

Although you are running Kubuntu 7.04, you said you are running Gnome. So did you install the ubuntu-desktop package onto the Kubuntu system, or did you get Gnome some other way?

Have you tried temporarily switching back to the Kubuntu desktop to see whether you can find that right-click option then? I don't have a system with both installed, so I don't know how to do that. I remember reading somewhere that you can logoff, then select the desktop from an options menu before logging on.

Okay, that's a bunch of questions. Please read through this post and try to answer each one of them, then collect the output from lsmod and the boot messages. You could answer the questions in one post and put the output in another post, if you like.
__________________






I remember the thread talking about the right click option was slightly old, and I believe it was here on Ubuntu forums. It could have been about an external hard drive operating slow, or a flash drive. I will try searching again. 

My secondary computer used to run Kubuntu 7.04, and apparently I upgraded it to Kubuntu 7.10 and had some problems. I tried a fresh Ubuntu 7.10 + my old copy of WinXP (dual boot) and it did not work properly. So currently I have my secondary system only running WinXP, though I may make a dual boot with Feisty or may wait until a few weeks after Hardy is released and use that.

My primary computer is a system someone gave to me. It is running Kubuntu, and I installed XFCE and GNOME on it.  Apparently I did not install Kubuntu on my primary, the original owner did.

As far as the lsmod, here it is:

```

Module                  Size  Used by
snd_opl3_synth         16132  0
snd_seq_instr           8832  1 snd_opl3_synth
snd_seq_midi_emul       7680  1 snd_opl3_synth
snd_ainstr_fm           3456  1 snd_opl3_synth
snd_rtctimer            4384  0
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   241004  0
nfsd                  218992  17
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_userspace       5408  0
cpufreq_stats           7360  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
dev_acpi               12292  0
sony_acpi               6284  0
video                  16388  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
dock                   10268  0
button                  8720  0
battery                10756  0
container               5248  0
ac                      6020  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ipv6                  269088  14
lp                     12452  0
snd_cmipci             37024  1
gameport               16520  1 snd_cmipci
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_opl3_lib           11520  2 snd_opl3_synth,snd_cmipci
snd_hwdep               9988  1 snd_opl3_lib
snd_mpu401_uart         9472  1 snd_cmipci
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_opl3_synth,snd_seq_instr,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_rtctimer,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9100  7 snd_opl3_synth,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  15 snd_opl3_synth,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               4713780  22
pcspkr                  4224  0
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0
serio_raw               7940  0
sis_agp                 9604  1
agpgart                35400  2 nvidia,sis_agp
soundcore               8672  1 snd
i2c_sis96x              6532  0
i2c_core               22656  3 i2c_ec,nvidia,i2c_sis96x
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
af_packet              23816  2
evdev                  11008  4
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ide_disk               17024  3
pata_sis               14732  0
ata_generic             9092  0
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  1 libata
sis5513                14856  0 [permanent]
floppy                 59524  0
hpt366                 17920  0 [permanent]
sis900                 24704  0
mii                     6528  1 sis900
generic                 5124  0 [permanent]
ohci_hcd               22532  0
usbcore               134280  2 ohci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

```

I'm a little confused on the boot messages. Do I need to reboot and repost the syslog or am I to be looking for another file? 

Thanks for the input.

Edit:

I found the thread about the right click option here:
[http://ubuntuforums.org/showthread.php?t=432119](http://ubuntuforums.org/showthread.php?t=432119)
The people did not have the same problem as I did, but it did speak of a setting that is used to prevent corrupt data in case the drive is unplugged. Now re-reading this I am not sure if it could have something to do with my "stalling" problem or not.

---

### Post by rkd on 2008-02-01
Good that you found that thread. I believe that setting would affect only writing to a USB device, and probably would not cause stall messages, but it still seems strange that you don't find it on your system. Maybe it only applies to devices that you can write to, so won't show up for a camera. Do you have an external USB hard disk or USB flash drive that you could plug in and check to see whether the option appears when you right click its icon? If you don't have something to test that with, it's not important.

When you said that copying photos from your camera on the secondary PC has always worked well, does that include when it was running Kubuntu 7.04?

How did you install XFCE and Gnome on the primary system? Was it by installing the Ubuntu-desktop and Xubuntu-desktop packages from the Ubuntu repositories via one of the package installers, or did you get them some other way?

I want to see the boot messages from the syslog file, but don't copy the whole file -- just the messages from the time of the boot to the end. Just make note of the time on the system, restart, then when you've logged on again, look for that time in the syslog. You'll find some messages that say things like:

Inspecting /boot/System.map-2.6.20-15-generic
Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic

Copy from there to the current time at the end of the log.

---

### Post by penguinbreath on 2008-02-02
> **rkd said:**
> Good that you found that thread. I believe that setting would affect only writing to a USB device, and probably would not cause stall messages, but it still seems strange that you don't find it on your system. Maybe it only applies to devices that you can write to, so won't show up for a camera. Do you have an external USB hard disk or USB flash drive that you could plug in and check to see whether the option appears when you right click its icon? If you don't have something to test that with, it's not important.

When you said that copying photos from your camera on the secondary PC has always worked well, does that include when it was running Kubuntu 7.04?

How did you install XFCE and Gnome on the primary system? Was it by installing the Ubuntu-desktop and Xubuntu-desktop packages from the Ubuntu repositories via one of the package installers, or did you get them some other way?

I want to see the boot messages from the syslog file, but don't copy the whole file -- just the messages from the time of the boot to the end. Just make note of the time on the system, restart, then when you've logged on again, look for that time in the syslog. You'll find some messages that say things like:

Inspecting /boot/System.map-2.6.20-15-generic
Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic

Copy from there to the current time at the end of the log.


Copying photos from my camera to my secondary system under Kubuntu 7.04 has always been ok.  I believe it was also ok under *Ubuntu Gutsy. (I tried both Ubuntu and Kubuntu Gutsy on my secondary system.) I will try loading photos on its current installation of WinXP.

I installed XFCE and GNOME on my primary system with a command like this. "sudo apt-get install ubuntu-desktop" and "sudo apt-get install xubuntu-desktop".

Don't know if this will help but here is the system specs for my computers. (My secondary was built in a shop and my primary was a barebone custom build my brother gave me.)

Primary:
Intel P4 2.4ghz. I believe it is socket 4** something.
Do not know exactly what the motherboard is, (looking for the manual) but I believe it is or close to a soyo dragon p4s.
1gb ram
two hard drives
DVD drive and a CD drive that is disconnected.
A new 400w power supply I installed. Apparently I did not connect things properly, so I get an error saying something about an 80 conductor cable not installed. (I think it might be talking about my floppy? Going to fix it after I try to get this USB thing fixed.)
A BFG Nvidea geforce 4000 128mb.

I plan to later remove one of the hard drives and leave my 80GB (to make things more simple) and organize the cables a bit better. 

Secondary:
AMD 1.8ghz Duron socket 4**
MSI motherboard with a VIA chip.
512 RAM


I am also posting the boot log of my primary PC.

---

### Post by rkd on 2008-02-03
The syslog messages don't show anything that I can recognize as indicating a cause of your problem.

I checked into some technical details about USB and learned that "stall" is a kind of status that a device can have which means it cannot accept a command at the moment. Apparently, it can be triggered by sending commands in combinations that the device was not programmed to expect.

There seems to be a lot of marginal implementations of the USB protocols in USB devices.

My impression is that it is more likely that the problem is due to the particular software on your primary computer than it is due to the hardware.

One suggestion I can make is to be sure the software on your primary computer is completely up to date.  First go to the Software Sources application (under System -> Administration). In the Updates tab, make sure that feisty-updates and feisty-backports are both selected. (The others can be selected, too, if you choose.) Then in a Terminal, enter the commands:```
sudo apt-get update
sudo apt-get upgrade
```
That might require downloading a lot of updates, which might not be practical if you have a slow connection. If we knew which packages are most relevant, we could upgrade just them, but I am unsure which packages they are.

If the problem persists after that, there is some chance that the problem comes from having the mixture of Ubuntu, Kubuntu, and XFCE desktops. I haven't seen any reports that say that is a problem, but it seems like something we should check on. I think it would be worth booting from a Live CD to see whether the problem occurs in that environment. If you have any 7.04 Live CD, I think that would be the best one to try at first because if it works from a 7.04 Live CD, we know the 7.04 software can work on your PC, and we only need to figure out what is keeping it from working with your current mix of software. If you try the 7.10 Live CD without first trying a 7.04 Live CD and the camera works, we won't know whether the problem is something in 7.04 that was fixed in 7.10, or was caused by mixing the three environments (or some other configuration choice you made) on your PC.

If you do try the camera with a 7.04 Live CD and it still doesn't work, then it probably makes sense to try the camera with the 7.10 Live CD. If it works with the 7.10 Live CD, then you probably need to upgrade to 7.10. Since you had the camera working on the secondary system with 7.04, I think the only reason you would have to do that would be if it really was something about the hardware on your primary PC that is causing the problem. I think it is more likely to be a software configuration problem, but it could be hardware.

Here is a list of all the camera models that the Linux software says it supports. 

   [http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

It would be interesting to know whether your camera is mentioned in that list. We know it does work because you were using it on your secondary PC, but if it is not included in that list, that might be an indication that there are some peculiarities about your camera. Or it could mean that the people maintaining that list just haven't checked your camera.

---

### Post by penguinbreath on 2008-02-03
My camera is supported according to the list. I tried copying files directly, used digiKam, and also used the GNOME picture download ?wizard?. Still the same stalling problem.
I tried the Kubuntu feisty live CD, and I still had the stalling. 



I have done updates since I recieved the computer, and I have third party updates on. I do not have pre-released updates on. I believe my feisty setup is pretty up to date.


I believe there is a card I can buy that has USB ports on it. Should I think about buying one of those? And is it likely it will fix my problem?

I will be looking for another USB device to try and see if it does the same thing when copying data.

---

### Post by rkd on 2008-02-04
An add-on USB adapter card might be worth trying, but I'd like you to verify the updates before you try that.

You mentioned that you have third party updates on, but there isn't a tab named third party updates.  There is one named Third Party Software and one named Updates. Having Third Party Software enabled is okay, but probably doesn't affect this problem. Please check the Updates tab and be sure that "Recommended updates (feisty-updates)" and "Unsupported updates (feisty-backports)" both are checked.  If they are checked already, that is fine -- you have any updates that might be relevant.  If either of them is not checked, correct that, then do the apt-get update and apt-get upgrade commands I mentioned earlier, then test the camera.

Assuming completely up-to-date software doesn't fix the problem, I guess trying a USB add-on adapter would be reasonable.  They don't cost much -- I've seen them priced between $5 and $10.  If you are familiar with opening your computer, you shouldn't have any difficulty installing the adapter.  Just remember to take precautions to avoid static electricity discharges.  While you are working, frequently touch some bare metal part of the computer case to drain off any static electric charge, and when handling the adapter card, try to touch only the edges of the card where there are no conductive strips.

I really have no idea what the cause of the problem is, so I have no idea how likely it is that an add-on USB adapter will fix the problem.  The camera worked okay with 7.04 on the secondary computer, so we know the camera works with 7.04 software. But it doesn't work with 7.04 software on the primary computer.  That seems to say the USB on the primary computer is the problem.  But the error -- the stalling -- seems to me to be a software protocol problem, not a hardware problem.  Hence my confusion.  Maybe I'm wrong and the stalling *is* a symptom of a hardware problem.

I can think of one test we have not tried yet; at least I don't remember trying it.  It would be good to try using the camera on the secondary PC with the 7.04 software.  I know the camera works correctly on the secondary PC using Windows, but it has been a while since you have used the camera on the secondary PC with Ubuntu (or Kubuntu -- whatever you were running on that PC).  There is a small chance that some configuration setting in the camera was changed after you stopped using it with Ubuntu on the secondary PC, and that change is preventing it from working with Ubuntu now.  We can test that by booting the secondary PC from the 7.04 Live CD and trying to transfer some photos from the camera.  If that works, then the USB hardware on the primary PC seems to be the only explanation for the problem.

If it happens that you get the stalling when doing that test on the secondary PC, then we have to figure out what changed.  It might be some camera configuration setting.  It might be the cable between the camera and the PC has gone bad (low chance since it still works with Windows).  It might be something else, but I can't think of anything else right now.

Trying another USB device on the primary computer might be interesting, but might not.  If it doesn't work, then that would cast more suspicion on the USB hardware.  If it does work, I think that wouldn't tell us anything about why the camera doesn't work.

Okay, that's all I can think of right now.  My suggestion is:

First, make sure the software updates settings are as I described. If they are not set right, correct, update, and test the camera again.

Second, try booting the secondary PC with the Live CD and see whether the camera still works properly there.

Third, get a USB add-on adapter and see whether the camera works with it.

---

### Post by penguinbreath on 2008-02-13
Is there something I can try through here?

[[IMG]http://img352.imageshack.us/img352/5941/imagesoftware8cc0.th.jpg[/IMG]](http://img352.imageshack.us/my.php?image=imagesoftware8cc0.jpg)

---

### Post by rkd on 2008-02-13
I don't know anything about Device Manager, so the short answer is I don't know. Maybe someone else can chime in with a more definite answer. Meanwhile, when I have a chance, I'll look into it to see whether there is anything there that might be helpful.

---

### Post by rkd on 2008-02-15
I took a little bit of a look at Device Manager. As far as I can tell, it only displays information about the hardware in the system. It seems not to provide any way to change the devices or the software that uses the devices.

If there were some bit of information about the USB hardware that we wanted to know, that Device Manager might be able to show it to us, but at the moment, I can't think of any information we don't already know.

So it seems to me that Device Manager doesn't offer any help in solving the stalling problem you are having.

---

### Post by penguinbreath on 2008-02-16
My primary computer has two hard drives. I think it also has a mounted NFS. I believe this is what gives me problems with Google Picasa (jerky and slow at times), which is why I plan to remove one of the hard drives (to make things more simple) and reinstall the OS without this NFS thing. I may try the workaround first.

From: [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

> If you have an NFS mounted home directory, the performance may be poor. Picasa relies heavily on a lot of files in the ~/.picasa directory, and if the home directory is slow, then Picasa will be slow. You can work around this by making a directory in /var/opt/picasa/$USERNAME/ that corresponds to your username. You have to have full rights to that directory.


Could this have something to do with my USB issue? Could something with the two hard drives be causing the problem? Like maybe if the OS is on one drive and my photos are on another, wouldn't this slow things down, causing issues when copying data? But it still does not make sense since I still had  the same USB issue with the live CD.

---

### Post by rkd on 2008-02-16
I kind of doubt you have a NFS-mounted home directory. It is the home directory part that I doubt is true. When you login, is the directory that you are in at that point on the NFS server or is it on your computer's hard drive? If it is on your computer's hard drive, then that warning about NFS doesn't apply to you.

I imagine your hard disks are connected via IDE, not USB. Do you believe that is correct? If they are IDE disks, then I doubt the disks are contributing to the stalls, no matter whether you have one or two of them. If the disks were connected via USB, I suppose there would be some possibility that they could be overloading the USB and somehow triggering the stall, but I think even that is unlikely.  

I have to say that I can't rule out any cause completely, since I don't know for sure what is triggering the stall.  I have a little bit of experience dealing with hardware, and that gives me the feeling that these factors aren't contributing to the stalls, but I can't say anything stronger than that about them.  The cause really is a puzzle to me.

I think there is no technical reason to prefer one disk over two, so question of one disk or two is purely a personal choice.  If you would prefer to have just one, go for it.  I'm pretty sure it will have no effect on the stalling problem or on this Picasa problem, so don't be too disappointed if it doesn't make a difference with that.  But if it ends up as a more pleasing arrangement for you, then that is a benefit for you.

---

