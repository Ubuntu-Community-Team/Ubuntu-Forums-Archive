---
title: "Messed up host name/can't sudo"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by revlarry on 2007-01-14
Hi!

I just did my first Ubuntu install yesterday (13-Jan-07), 5.10 (Breezy Badger) on an older HP X2100 workstation. The install went well, and the system is working and internet (Firefox) is working well, too.

Somewhere along  the line, as I was trying to set up file sharing with the rest of the network (Windows), I think I did something that changed the host name of my Linux computer. 

I can no longer access [system][administration][networking] -- it "starts", but never shows up on screen ... it is just "titled" at the bottom, and then disappears.

I also cannot sudo -- I get a response "sudo: unable to lookup via gethostbyname ()"

In Terminal, the title-bar reads "larry@: ~"

On boot-up, after username and password, I get the error message: "Could not look up internet address for .  This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding to the file /etc/hosts."

Reading through the forumsI have found similar advice. I looked at the file and have found no host name listed in this file. However, I have also not figured out how to edit the file. It comes up "read only".  As a new user, I am not very familiar with all the tools or procedures -- but so far nothing has worked to correct the problem.

The install and updates went smoothly, so I could reinstall from scratch, if needed, but would prefer to correct the problem in the current installation, if I can, since that would be a better learning opportunity.

Any advice would be appreciated. Thanks!

--Larry--

---

### Post by taurus on 2007-01-14
Boot into recovery mode from GRUB menu and at the prompt, paste the outputs of these two commands here!

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by revlarry on 2007-01-14
Once I figured out how to boot into the recovery mode from GRUB ...

cat /etc/hostname -- returns nothing
cat /etc/hosts -- returns localhost.localdomain localhost

then the lines
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

(can't just cut and paste, as I am using a second machine here)

Thanks!

--larry--

---

### Post by taurus on 2007-01-14
While you are still in recovery mode, edit both /etc/hostname & /etc/hosts.

```
nano /etc/hostname
```
Add this name to it (should be only one name in there...).
```
larry-desktop
```
Save it by holding down <Ctrl> while hitting x.  Type Y to save it and Return.  Now, edit /etc/hosts.

```
nano /etc/hosts
```
Your /etc/hosts should look something like these below...

```

127.0.0.1       localhost
127.0.1.1       larry-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

After making changes to both /etc/hostname & /etc/hosts, reboot and see if you can use sudo and/or network works again.

```
shutdown -r now
```

---

### Post by revlarry on 2007-01-14
That did it!

Now I know how to use GRUB AND I have a working network command again.

Thank you, thank you, thank you!!!!

---

### Post by taurus on 2007-01-14
Just be careful next time you play around with computer name and things like that.  Otherwise, you should know how to fix it now if you run into the same problem again.  ;)

---

### Post by The_Apprentice on 2007-01-19
Can we take this one step further please......

I can puTTy on to my ubuntu box and I can NX on to the box.

The thing is I can not use puTTY as I can not edit anything 'cos of the sudo issue.

When using NX I can not change the seesion "ctrl-alt-f1", nor can I logout without closing my connection.

Any other ideas so I do not have to get of my @rse.



Funny thing is, nothing has been changed on the box for weeks, and everything had been fine until this morning when I noticed there were updates and the Update Manager would not open.
In fact anything requiring a password to run does not work.

---

### Post by lfloyd on 2007-02-03
Messed up password file/can't sudo:  what if you can't boot into root in recovery mode.  I am having similar problems changed samba.config, nsswitch.config, etc to attempt to network with windows business server.  Any help would be appreciated.  Thanks




Loretta

---

