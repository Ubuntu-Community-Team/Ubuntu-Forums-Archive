---
title: "Ubuntu 10.04.4 LTS + Netatalk 2.2.1 + Mountain Lion 10.8"
date: 2012-09-29
forum: Apple Hardware Users
---

### Post by oliverp on 2012-09-29
Hi!

I'm having trouble setting up TimeMachine backup on a MBP Retina running 10.8.2.

The server is running Ubuntu 10.04.4 LTS with Netatalk 2.2.1. I'm currently using Netatalk to share some files over AFP, and that works great, both from Mountain Lion and from Lion. However, when I try to setup TimeMachine on any of my machines (one running Lion, the other one Mountain Lion); neither setup works, but with mixed results.

On Lion, I am able to select the "TimeMachine" volume in system preferences, but when the initial backup is about to start it failed with an error telling be the remote volume doens't support some AFP-features (which usually would mean I need to use uams_dhx2 instead of uams_dhx, but I have already done this).

On Mountain Lion, I'm not even able to select the volume within system preferences. It doens't show up.

[[img]http://www.narpau.se/slask/timemachine-toubles-small.jpg[/img]](http://www.narpau.se/slask/timemachine-toubles.png)

I have added the TMShowUnsupportedNetworkVolumes in the com.apple.systempreferences.plist on both machines by executing
```
defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1
```

I even tried deleting the com.apple.systempreferences.plist file to force System Preferences to generate a new one, which I then added the entry to once more (that's why the plist in the screenshot is so short).

This is my configuration on the server:

/etc/netatalk/afpd.conf
```
- -ipaddr 192.168.0.16 -tcp -noddp -uamlist uams_dhx.so,uams_dhx2_passwd.so -nosavepassword
```

/etc/netatalk/AppleVolumes.default
```
~/TimeMachine		"TimeMachine"	allow:oliver cnidscheme:dbd options:usedots,upriv,tm volsizelimit:280000
```

Can you see something wrong in my configuration? I just can't figure this one out. I appreciate all help I can get!

---

### Post by dmovad on 2012-09-30
This site helped me a lot!

[http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/](http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/)

---

### Post by CGSaw on 2012-10-03
This guide worked pretty well for me: [http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/](http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/)

One downside is that the drive you're backing up to should be HFS (it can't be HFS+). I legitimately followed all the steps only to realize my drive was ext4 and had to redo it.

---

### Post by EvilKeg on 2013-01-24
> **CGSaw said:**
> This guide worked pretty well for me: [http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/](http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/)

One downside is that the drive you're backing up to should be HFS (it can't be HFS+). I legitimately followed all the steps only to realize my drive was ext4 and had to redo it.

Oh great! I've built my partition as EXT4! Looks like I've got some messing about to do :/

sliding puzzle tastic!! :)

---

### Post by cdstelly on 2013-03-27
> **EvilKeg said:**
> Oh great! I've built my partition as EXT4! Looks like I've got some messing about to do :/

sliding puzzle tastic!! :)

Did reformatting to HFS fix your problem?

---

