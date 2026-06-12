---
title: "Suggestions for running Xubuntu as lightly as possible"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by lesliek on 2008-01-04
I have an old laptop with a Pentium III chip (not sure of its speed) and 128MB of RAM.

I installed DSL v 4 on the laptop and attempted to connect it to my existing wireless network. That worked sometimes and sometimes not and I was unable to figure out why that was. Finally, being very frustrated at my continued inability to get a reliable wireless connection, I got rid of DSL and installed Xubuntu 7.10.

All seems well and though it's early days, I've had no wireless problems yet. I notice that the versions of ndiswrapper and wpa_supplicant in DSL are much older than those in Xubuntu and maybe it was the upgrade in those applications that seems to have overcome my former wireless problems.

In any event, given my sparse RAM and the fact that my main interest in the laptop is for web browsing, I'd like to do what I can to get the laptop running as quickly as possible.

I saw recently a document at Lifehacker with suggestions as to what to do in Linux generally, but it seemed to provoke angry responses from commenters.

Is there some sort of checklist specific to Xubuntu of things to do that's generally accepted in the community as accurate?

If so, I'd be grateful for a pointer to it, If not, does anyone have any specific suggestions for me?

Thanks for reading this,

Leslie

---

### Post by dwhitney67 on 2008-01-04
Nevermind!  I did not realize that you wanted to web-browse on your server.

-----------------------------------------------------------

Xubuntu is in itself very "light" compared to other distros.  If you are comfortable issuing commands from the command line, then one thing you can do to make Xubuntu lighter is to boot up into init level 3, thus ensuring that the XFCE window manager is not started.

There's an entry in the /etc/inittab that controls which init-level is entered during startup.  It looks like the following; simply replace the 5 with a 3.

```
id:5:initdefault:
```

Now when the computer boots, all you will see is the console.  You can login there, or alternatively, SSH into the system from another system that has a window manager.  The second option of course presumes that the server-system has an SSH-server running.

P.S.  I tend to like Fedora because it provides better user-control over which packages get installed onto a system.  For a server, I would elect not to install any window managers, and install SSHd, HTTPd, and MySQLd, along with the base system and other tools as necessary.

---

