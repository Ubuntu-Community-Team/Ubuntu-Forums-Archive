---
title: "undo update?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Preserved Killick on 2007-02-01
I think the last update I ran has messed up either X or my nvidia driver or wine or all three.  Can I undo the last update without knowing what all those lib files etc. were specifically?  How do I do this?  Thanks,

Killick

---

### Post by dannyboy79 on 2007-02-01
look for a log file that has update or upgrade or apt or aptitude, it'll be in /var/log/. but all you should have to do is reconfigure your x server and maybe reinstall your nvidia driver and you'll most likely be fine. if you find the log file (there is a log viewer under system, admin) then you can look in the log file to see what was all updated last and you can maybe remove it but I am not sure how to undo what aptitude did? oh yeah, you should also be able to go into synaptic, and play around with the pull downs or on the right side and look for unattended updates or a filter that will show you what was updated recently and maybe there is a button to go back a version of a program or lib. chances are though, if ubuntu updated itself and you;re having x server issues you want to reconfigure your x server and leave the updates alone as they most likely needed to be upodated. good luck

---

### Post by Preserved Killick on 2007-02-01
Thanks, Dannyboy79.  I didn't think to look in Synaptic!  Synaptic keeps a history of updates.  (Open Synaptic, click file > history, and select a date).

Here's my history for the last two updates:

On 1/27/2007

Upgraded the following packages:
firefox (1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
firefox-gnome-support (1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
libnspr4 (2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
libnss3 (2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1


On 1/24/2007

Upgraded the following packages:
libc6 (2.3.6-0ubuntu20) to 2.3.6-0ubuntu20.2
libc6-dev (2.3.6-0ubuntu20) to 2.3.6-0ubuntu20.2
libc6-i686 (2.3.6-0ubuntu20) to 2.3.6-0ubuntu20.2
libgeoip1 (1.3.14-2) to 1.3.14-2ubuntu0.1
libsoup2.2-8 (2.2.93-0ubuntu1) to 2.2.93-0ubuntu1.1
locales (2.3.18 ) to 2.3.18.1

The problems I'm having began after the 1/27 update, and I wouldn't know why firefox updates would cause bzflag and picasa2 to crash Gnome, unless it's a bug in firefox-gnome-support 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1. 

There doesn't seem to be a way to go backwards with Synaptic-- only the new versions of these files are listed.

Anyone know how to undo an update?  Or how to stop Gnome from crashing when I launch bzflag or Picasa2?:confused: 

-- Killick

---

### Post by dannyboy79 on 2007-02-01
we need to troubleshoot this so we can narrow it down. what do your various log files state prior to and after the crash? /var/log/syslog? dmesg? Xsession (i could be wrong on what the log file is for your xserver)? 

and you haven't really been specific with what is occuring and what are you doing just prior to whatever is crashing. Make sure you are specific as to whether or not x-server is craching (dropping to terminal) or your mouse locks up? or your keyboard locks up? can you kill x-server by doing a ctrl-alt-backspace to get to a terminal to view the logs from there? I use nano when no window system is available. so you would do sudo nano /var/log/syslog and check it out. or you could do sudo cat dmesg | tail to just look at the end of your dmesg log. good luck and make sure you fill us in if you want our help.

---

### Post by Preserved Killick on 2007-02-01
Hi, Dannyboy, and anyone else following along.  

Thanks for your help.  I appreciate it!

When I try to start a full-screen game, BZFlag, the screen goes black (normal) but then instead of the game appearing, I get a brief flash of a terminal login, and then after a blink or two, I get the gui ubuntu login screen.

When I try to launch Picasa2, a photo database/photo utility tool that uses wine, the screen goes black (not normal) and the same terminal login, a few blinks, and then I'm looking at the ubuntu login screen.

So, to see what's going on, I took your suggestion and forced a crash by clicking the icon on my panel to start bzflag.  Once I'd re-logged in, I opened the /var/syslog file and here's what I saw:

Feb  1 15:37:02 localhost -- MARK --
Feb  1 15:57:04 localhost -- MARK --
Feb  1 16:03:26 localhost gdm[27833]: Error reinitilizing server
Feb  1 16:03:28 localhost gconfd (damon-27904): GConf server is not in use, shutting down.
Feb  1 16:03:28 localhost gconfd (damon-27904): Exiting
Feb  1 16:03:49 localhost gconfd (damon-19519): starting (version 2.14.0), pid 19519 user 'damon'
Feb  1 16:03:49 localhost gconfd (damon-19519): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  1 16:03:49 localhost gconfd (damon-19519): Resolved address "xml:readwrite:/home/damon/.gconf" to a writable configuration source at position 1
Feb  1 16:03:49 localhost gconfd (damon-19519): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  1 16:03:49 localhost gconfd (damon-19519): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  1 16:03:49 localhost gconfd (damon-19519): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb  1 16:03:53 localhost gconfd (damon-19519): Resolved address "xml:readwrite:/home/damon/.gconf" to a writable configuration source at position 0

----------
You can see what happened at 16:03:28.  I don't know what this means exactly or what kind of problem is implied by this data.  If you or anyone else has an idea, please let me know.

thank you!

-- Killick

---

### Post by dannyboy79 on 2007-02-02
actually this error for gconfd where is talks about Resolved Address is very common, i have it in my syslog as well. the part that I don't have in my log is right above it,
Feb 1 16:03:26 localhost gdm[27833]: Error reinitilizing server
Feb 1 16:03:28 localhost gconfd (damon-27904): GConf server is not in use, shutting down.
Feb 1 16:03:28 localhost gconfd (damon-27904): Exiting
so this really can't help us, it is merely telling us that there was an error trying to reinitialize your x server and it couldn't then it states that it's not running and will shut down but the gconfd daemon is NOT your x server which is what is crashing and causing you to be at the login prompt again so I don't think this is what we're looking for. so your syslog is ok, did you check out /home/username/.xsession-errors, /var/log/messages or kern.log? so look thru your /var/log/ folder and if you see a log file that has a recent date, open it with the log viewer and if the log viewer says it's not a log file than open it in gedit or nano.

here, I found this thread, [http://www.ubuntuforums.org/showthread.php?t=193670](http://www.ubuntuforums.org/showthread.php?t=193670). it has to do with reinstalling nvidia-glx. have you gogled bzflag kills gdm? or Picasa2 returns me to login screen? try the thread and if you don't use nvidia, then try gogling what I suggested.

---

### Post by Preserved Killick on 2007-02-02
Hi, Dannyboy.

I have googled for this problem and didn't find anything useful to me.  Here are the files that you suggested I look at:

This is /home/damon/.xsession-errors after I launched bzflag to get a crash:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "damon"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/LinuxOne:/tmp/.ICE-unix/29312
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:29381): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:29381): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
connect: Operation now in progress
init_poll: get_socket_error(): 111
Warning: Missing charsets in String to FontSet conversion
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

I'm not sure what these errors belong to, or whether they were involved in the crash at all.  They seem to be warnings.

/var/log/messages  -- this is the tail of the file after I reproduced the crash by opening bzflag.

Feb  2 10:08:34 localhost -- MARK --
Feb  2 10:28:35 localhost -- MARK --
Feb  2 10:30:33 localhost kernel: [17237848.656000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Feb  2 10:37:20 localhost gconfd (damon-13579): Received signal 15, shutting down cleanly
Feb  2 10:37:20 localhost gconfd (damon-13579): Exiting
Feb  2 10:37:29 localhost gconfd (damon-29360): starting (version 2.14.0), pid 29360 user 'damon'
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readwrite:/home/damon/.gconf" to a writable configuration source at position 1
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb  2 10:37:31 localhost gconfd (damon-29360): Resolved address "xml:readwrite:/home/damon/.gconf" to a writable configuration source at position 0
Feb  2 10:38:00 localhost kernel: [17238294.816000] usb 5-6: reset high speed USB device using ehci_hcd and address 4


Here's what I have in the tail of /var/log/kern.log after the reproduced crash:

Feb  2 09:19:41 localhost kernel: [17233596.580000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Feb  2 10:30:33 localhost kernel: [17237848.656000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Feb  2 10:38:00 localhost kernel: [17238294.816000] usb 5-6: reset high speed USB device using ehci_hcd and address 4

kern.log doesn't seem to reflect the crash (unless I'm missing something).  You mentioned the nvidia driver perhaps needing a re-install, and I'm willing to try that, but I don't know why you think this will help.  

this time the /var/log/syslog shows the gdm problem happening simultaneously with the gconf error.  I don't know if that matters or not.

Feb  2 10:37:20 localhost gconfd (damon-13579): Received signal 15, shutting down cleanly
Feb  2 10:37:20 localhost gconfd (damon-13579): Exiting
Feb  2 10:37:20 localhost gdm[13514]: Error reinitilizing server
Feb  2 10:37:29 localhost gconfd (damon-29360): starting (version 2.14.0), pid 29360 user 'damon'
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readwrite:/home/damon/.gconf" to a writable configuration source at position 1
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  2 10:37:29 localhost gconfd (damon-29360): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb  2 10:37:31 localhost gconfd (damon-29360): Resolved address "xml:readwrite:/home/damon/.gconf" to a writable configuration source at position 0
Feb  2 10:38:00 localhost kernel: [17238294.816000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Feb  2 10:48:36 localhost -- MARK --

Any ideas, Dannyboy, or anyone else following along?

Thank you very much,

-- Killick

---

### Post by susbut on 2007-02-02
> **Preserved Killick said:**
> I think the last update I ran has messed up either X or my nvidia driver or wine or all three.  Can I undo the last update without knowing what all those lib files etc. were specifically?  How do I do this?  Thanks,

Killick


I had similar problems after the update. The dbus session services stopped. I reinstalled the dbus-launch, dbus-send, hotplug packages, pcmcia-cs and pcmcia drivers. It didn't work. I reinstalled the X and finally the total gnome2-package. It didn't work. Finally I coundn't log into the gnome failsafe session. I then started all over.

Susbut.

---

### Post by dannyboy79 on 2007-02-02
> **Preserved Killick said:**
> You mentioned the nvidia driver perhaps needing a re-install, and I'm willing to try that, but I don't know why you think this will help.  

-- Killick

Wait, so you do have an nvidia driver installed????? Well ges, that's your problem. Certain updates will ALWAYS affect 3rd-party drivers like wireless drivers and nvidia or ati drivers. YES, reinstall it. Also, your x-server is crashing and you ask me why I would think the nvidia has anything to do with it? HELLO, your x server is basically the "GRAPHIC EDITION" of linux. otherwise we would just all be stairing at the command line. So, please reinstall any restricted drivers you installed prior to the update. I don't mean to get over anxcious here but one should be able to connect the dots when you're talking about programs which are graphic intensive causing a crash and your graphics driver. Also, I asked you to read the link I provided and by your response you must not have read it. I'll paste it here for ya:
** had the same problem recently with some system upgrades. gdm would spontaneously restart every 20 mins or so.**

**The Xorg log file report indicated the problem**.

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0): log file that the GLX module has been loaded in your X
(EE) NVIDIA(0): server, and that the module is the NVIDIA GLX module. If
(EE) NVIDIA(0): you continue to encounter problems, Please try
(EE) NVIDIA(0): reinstalling the NVIDIA driver.
AUDIT: Mon Oct 23 20:11:37 2006: 26491 X: client 2 rejected from local host
AUDIT: Mon Oct 23 20:11:37 2006: 26491 X: client 4 rejected from local host

**The problem was that the symbolic link /usr/lib/xorg/modules/extensions/libglx.so was broken. The glx module had somehow been removed during the upgrade (I guess). (The glx module was built by the NVIDIA driver installer NVIDIA-Linux-x86-1.0-8774-pkg1.run for me). **
Running glxinfo would trigger the problem and cause the gdm restart.

**I resolved this by reinstalling the NVIDIA driver. No more error messages, no more restarts.**

and also this right there in the next thread from the link I told you to read:

**that helped, but I also had to reinstall the Nvidia binary driver. I still had the .run file so that was easy at least!** if this part is applicable to you. it depends how you installed your nvidia driver and which one you used.

---

### Post by Preserved Killick on 2007-02-02
The problem was solved by re-installing the nvidia driver using the "envy" script you can download at: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

Thanks Dannyboy!  I wish I'd read that thread sooner, and I wish you'd noticed that I'd mentioned nvidia at the start of the thread.  We would have arrived at a solution sooner.  All's well that ends well, and I apologize for not attending to that thread.  Thank you for hanging in with me on this.

-- Killick

---

### Post by dannyboy79 on 2007-02-03
> **Preserved Killick said:**
> The problem was solved by re-installing the nvidia driver using the "envy" script you can download at: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

Thanks Dannyboy!  I wish I'd read that thread sooner, and I wish you'd noticed that I'd mentioned nvidia at the start of the thread.  We would have arrived at a solution sooner.  All's well that ends well, and I apologize for not attending to that thread.  Thank you for hanging in with me on this.

-- Killick

i can't believe after all the help I gave you, you have the audacity to even mention "I wish you'd noticed that I'd mentioned nvidia at the start of the thread"!!!!!!!!!!!!!! You can go back and read THREAD #2 and you'll clearly see that I stated, "look for a log file that has update or upgrade or apt or aptitude, it'll be in /var/log/. but all you should have to do is **reconfigure your x server and maybe reinstall your nvidia driver **and you'll most likely be fine" right from the get go! SO you can be sure that when I see your screen name again I ain't gonna help you you inconsiderate blah blah blah!!!!! Have a good day and I am glad you got it figured out. Why don't next time you search the forums or google and figure something out for yourself if you're gonna be a blah about it!

---

