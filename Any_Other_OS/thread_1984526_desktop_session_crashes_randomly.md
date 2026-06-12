---
title: "desktop session crashes randomly"
date: 2012-05-21
forum: Any Other OS
---

### Post by linuxrawkstar on 2012-05-21
Every, yes _EVERY_ time I log in to my mint desktop I can expect for the screen to flash black and immediately thereafter I'm presented with the login screen. My desktop session is completely lost, as was the state of each desktop application running at the time of failure -- such as google chrome, thunderbird, gnome terminal, and system monitor. I haven't been able to narrow the problem down to a given application; no matter what application or combination of applications I run, the problem still happens.

I found a file under my home directory called ".xsession-errors". It contains some messages that might provide clues to others about why my x session keeps bailing. When I see log messages like "...This shouldn't happen!", I grow suspicious that something is wrong with X or one of the applications running in it.  I'm including a pastebin link to its contents...

From the looks of the file, does anyone have any ideas of 1) what could be wrong, and 2) how I can make this stop happening? It is such an awful productivity killer to be working with a completely unstable desktop.

Here's a pastebin link to the contents of the file => [http://pastebin.com/WFG2wHmV](http://pastebin.com/WFG2wHmV)

---

### Post by rai4shu2 on 2012-05-22
That does look worrisome. Especially when it starts doing:

> Window manager warning: Got a request to focus 0x1200004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: Log level 16: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2412: instance `0x1b73e60' has no handler with id `16387'
Window manager warning: Log level 16: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2412: instance `0x1b73e60' has no handler with id `16388'
Window manager warning: Log level 16: gnome-shell: Fatal IO error 0 (Success) on X server :3.


(nautilus:6009): Gdk-WARNING **: The application 'nautilus' lost its connection to the display :3;
most likely the X server was shut down or you killed/destroyed
the application.

dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :3.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :3.

(gdu-notification-daemon:6309): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :3.

chrome: Fatal IO error 11 (Resource temporarily unavailable) on X server :3.
gnome-shell-calendar-server[6100]: Got HUP on stdin - exiting
** (process:6313): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:6313): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

(gnome-shell-calendar-server:6100): GLib-GIO-WARNING **: Error releasing name org.gnome.Shell.CalendarServer: Timeout was reached

---

### Post by Perfect Storm on 2012-05-22
Moved to Other OS/Distro Talk.

---

### Post by linuxrawkstar on 2012-05-23
Since my original post in this topic thread, I've been trying many things to get the random logout behavior to go away. I have thought to myself over and over that this seems like a hardware problem, probably a faulty graphics card or something. I decided I would go buy a new gfx card soon. I also continued to hunt around in other possible directions, such as BIOS firmware settings and upgrades, and then kernel tuning parameters.

I can't confidently say that it's working completely, but I did make a discovery that made my home-built computer boot faster and perform better -- AND my gnome session has NOT CRASHED for over 12 hours running and heavy use! The change was that I added the "nomodeset" flag in /etc/default/grub on the line that reads: GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

After editing that file I called $ sudo update-grub

Then I rebooted into a much faster computer.

You see my computer is hand-built. Here is a summary of my hardware (output of `lshw`) => [http://pastebin.com/r8mqdzzc](http://pastebin.com/r8mqdzzc)

Because the problem seemed hardware related to me, I theorized that the issue might have had to do with ACPI functionality in the newest Linux Mint kernel (I hadn't been experiencing these problems before that upgrade). By using the nomodeset kernel flag, it signaled to the Linux kernel not to emulate a windows operating system's ACPI behavior when interacting with the BIOS/motherboard. Since making this change, I haven't had any problems. I'm hoping this trend continues! If I can go another couple days without a session crash, I'll consider the issue "solved", at least for me.

One final note: don't try using "acpi=off" as a kernel flag, as this has (accurately) been described elsewhere on the internet as a "nuclear bomb" approach to ACPI problems. I can confirm that using it is problematic, and may cause your computer to become unbootable until you reboot it and remove that option from the Linux kernel parameters from the grub prompt and also from your /etc/default/grub, etc.

---

### Post by linuxrawkstar on 2012-05-23
> **linuxrawkstar said:**
> ...I can't confidently say that it's working completely, but I did make a discovery that made my home-built computer boot faster and perform better -- AND my gnome session has NOT CRASHED for over 12 hours running and heavy use!

That dream is now dead 

After a sustained period of heavy use, and despite obvious performance gains, I must with sadness report that the issue happened again. I was automagically logged out at a random time and presented with the login screen. This realllllly stinks! I'm going to continue to try to find a new, good graphics card, but I must admit I really had my hopes up. Things were going so well.

Another huge blow to the satisfaction-o-meter is that debugging X issues is apparently very complicated! Just take a quick look at this link and you'll know what I'm talking about => [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)

That link is mentioned in many ubuntu bug reports regarding X, so I know if this keeps happening, I'm eventually going to have to start really digging deep into X. This is such a shame and a hassle. I had been enjoying a steady level of productivity with my computer for a couple months now with a brand new installation of "Lisa" Mint. That relationship is really souring. The only thing that keeps me from running to another distro is that I've read it happens in Ubuntu and SuSE as well anyway. The root of my problem seems to go deeper than the Linux distro itself; other people out there are experiencing this and the bugs are unresolved. I found that out by searching an hour around here => [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

I wish there was a quick and easy solution to this, but I don't think this would qualify as an open and shut case; this issue is going to be a really difficult nut to crack. I'm not looking forward to it _at all_.

---

### Post by rai4shu2 on 2012-05-24
Have you tried the nvidia driver? It seems to me that if you are using an nvidia video card, then you really should give the proprietary driver a shot. Don't bother with the default one, though.

latest stable: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by linuxrawkstar on 2012-05-24
> **rai4shu2 said:**
> Have you tried the nvidia driver? It seems to me that if you are using an nvidia video card, then you really should give the proprietary driver a shot. Don't bother with the default one, though.

latest stable: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I've been using the proprietary "NVIDIA accelerated graphics driver (post-release updates) (version current-updates)"

...That's what you're talking about, correct?  I've been wondering if going back to the default non-proprietary driver would be better =(  I wouldn't be able to play most of my 3D games anymore though, and that would really ruin the gaming experience for my 7 year old.

---

### Post by rai4shu2 on 2012-05-24
I guess you really are running into hardware problems. Not really surprising when you build your own. You really need to double-check your power and heating/cooling situation. Make sure you're on top of all that or it could become a serious problem in the long run for sure.

---

### Post by linuxrawkstar on 2012-05-30
By way of follow up, I purchased a new graphics card and installed it.  After a few days with no problems I think it's safe to say that the issue is solved.  Too bad it wasn't more easy to diagnose.

---

