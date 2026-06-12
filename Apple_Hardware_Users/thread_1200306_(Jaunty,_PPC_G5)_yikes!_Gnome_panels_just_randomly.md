---
title: "(Jaunty, PPC G5) yikes! Gnome panels just randomly disappeared upon log in today."
date: 2009-06-29
forum: Apple Hardware Users
---

### Post by Tommmyboy on 2009-06-29
hi!

I've been using Jaunty without any bumps, post-install config tweak help courtesy some supernice people on this forum, on my iMac G5 (single processor, triple boot includes Jaunty, a full installation of Leopard 10.5.7 that I use as my primary Mac environment, and the barebones remainder of Panther 10.3.9 that came installed on the machine and I keep around for those in case any apps that migrated when I upgraded to Leopard start to misbehave)

**[SIZE="3"]Here's my problem:[/SIZE]** 
Just a few mins ago I booted up the machine, it defaulted into ubuntu as it should, the splash screen came up, the log in window came up, I logged in.
[B]
But all my panels are gone.[/B] :cry:

Which means, seeing as the only knowledge I have regarding the CLI is when to use sudo, and how/why to use the rm, cd, and make commands, LOL, I don't know how to open any apps or really do much of anything without the menus. I was tooling around help trying to figure out what to do and saw something about using terminal to check gnomePanel but heck, I couldn't even open a terminal if I wanted because for some reason alt-fun2 (or is it alt-fun4? I tried both, nothin happened) doesn't bring up a terminal window in the state my machine is in. My theme and desktop settings are intact. I had a file sitting on the desktop so I right clicked on that to see if I could get to get to the file browser to find any logs (although I had no clue what I was looking for) and did find something called xsession.errors in my home directory which I've copy and pasted below - it's full of all kinds of errors.  I right clicked on the desktop and got to the help dialogue through the change desktop selection which in turn got aBrowser up and running and me here to the forum. 

**[SIZE="3"]After what appeared to be a problem-free log out of my last Jaunty session, here are some out of the ordinary things that may or may not be relevant:[/SIZE]**
I needed to repartition one of the empty partitions I had set up previously to use with Mac files (and once I installed Ubuntu for some reason I can no longer use Apple disk utility to partition in any way at all except to erase the entire disk completely and start over so no matter if I am partitioning something for OS X or Ubuntu, I always have to use gparted and if its Mac go back and reformat the partition) so I inserted the Jaunty live cd (note: this was a release candidate live cd **but** I have the release version of Jaunty installed, I couldn't find that disk) I chose restart as the option in the shut down dialogue, and out of sheer force of mac habit held down the C key to initiate boot from CD rom. Everything came up as it should, I partitioned, I logged out of the live CD environment and the computer shut down. Three hours later, I returned, everything booted at normal speed, it didn't seem to be struggling, but after successful log in, NO PANELS. my theme settings are intact, my background is intact. But no panels. AGH. me need me my panels. 

Does the following log indicate what my problem might be? If so what should I do? There is mention of issues with gnome but I have no clue what all that means.

I've never had any other issues with my system once I got it all tweaked just right.  

[COLOR="Red"]BEGIN XSESSION.ERRORS LOG FILE:
[/COLOR]
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-Klfipb/socket
SSH_AUTH_SOCK=/tmp/keyring-Klfipb/socket.ssh

(gnome-settings-daemon:3198): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3198): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/tom/.config/metacity/sessions/1023ebfa119b67e812124632101727501500000030310018.ms: Failed to open file '/home/tom/.config/metacity/sessions/1023ebfa119b67e812124632101727501500000030310018.ms': No such file or directory
x-session-manager[3031]: WARNING: Could not launch application 'gnome-panel.desktop': Unable to start application: Failed to execute child process "gnome-panel" (No such file or directory)
** (nm-applet:3231): DEBUG: applet_common_device_state_changed
** (nm-applet:3231): DEBUG: applet_common_device_state_changed
** (nm-applet:3231): DEBUG: old state indicates that this was not a disconnect 0

** (nautilus:3228): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (update-notifier:3230): DEBUG: /usr/lib/update-notifier/apt-check returned 6 (security: 0)
** (update-notifier:3230): DEBUG: crashreport_check

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x2400008 (.xsession-); [COLOR="YellowGreen"]these messages lack timestamps and therefore suck.[/COLOR]
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


[COLOR="Red"]END LOG FILE[/COLOR]

Of course the particularly amusing comment [COLOR="YellowGreen"]these messages lack timestamps and therefore suck[/COLOR] contained within the log are quite humorous yet seem to make me want to slap someone. (just kidding)

Thanks for your help!

---

### Post by Tommmyboy on 2009-06-30
I still don't know exactly what happened or what caused it, but I finagled by way into the file browser by right clicking to create a new folder on the desktop and navigating into that way. Once in the file browser, I went and found synaptic and did a search for 

gnome-panel.desktop

which was the problem causer apparently throwing the error in the xsession error log it looks like. Nothing with that exact name came up but there were some packages sounding awfully similar in name - I think they were appended with the word "sharp" and there were some other ones that intuitively I felt were all wrapped up in my mess. 

So I just marked them all for removal if they were supposedly installed already, then again for installation. Restarted. Nothing.

I'm such a newbie I had no idea that the panels setting might actually be a full on application - things like that in Mac are usually in System Preference pane or extensions or something. But some how I ended up rooting around (sorry I should stop using the term rooting to describing me looking around given what one could infer from that term, to be clear, I was NOT in "root," as in the real "sudo" or "full access," doing any of this at any time.). I somehow ended up in the apps folder and there it was... something called Panels with the icon of a footprint. Double clicked to run it and low and behold returned my panels, with all of their settings intact. Hurrah.

Restarted to just see if I was in a dream and everything booted as normal and no errors in the xsession log and my panels were still there. so I went to bed happy and content that there was peace once again in the ubuntu-that-tom-built.

---

