---
title: "Updates and Checkinstall?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by willywonder86 on 2006-09-10
Was wondering if anyone could help me with a minor problem every time I try to install updates get this message below.

Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

Now when I follow what it says still comes back with the same thing every time its more annoying than anything is it possible to stop it doing this?

---

### Post by droogy on 2006-09-16
I have the same problem and would also appreciate a solution.. in fact I have another 4 'updates' along with the checkinstall one that will not upgrade.

---

### Post by tageiru on 2006-09-16
Which packages is it complaining about?

---

### Post by tandre75 on 2006-09-16
I am having trouble also.  I also posted to the Desktop forum, but haven't gotten any replys.  Sorry if this makes me seem rude.

I cannot use Update Manager, the full Synaptic program, or aptitude from the command line.

I get the following message:
[I](Reading database ... dpkg: error processing /var/cache/apt/archives/automatix_6.5-3-6.06dapper1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `pmount': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/automatix_6.5-3-6.06dapper1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
[/I]

---

### Post by droogy on 2006-09-17
> **tandre75 said:**
> I am having trouble also.  I also posted to the Desktop forum, but haven't gotten any replys.  Sorry if this makes me seem rude.

I cannot use Update Manager, the full Synaptic program, or aptitude from the command line.

I get the following message:
[I](Reading database ... dpkg: error processing /var/cache/apt/archives/automatix_6.5-3-6.06dapper1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `pmount': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/automatix_6.5-3-6.06dapper1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
[/I]
looks like something w/ automatix... try completely removing it and reinstalling the latest.  I've never had a problem w/ it.  And yes.. a little of topic... but as long as you figure out your problem who cares.

---

### Post by droogy on 2006-09-17
> **tageiru said:**
> Which packages is it complaining about?

For me it complains about:

Checkinstall
MJPEGTools
Transcode

I'm thinking to remove the packages and reinstall.  The problem I see with that is that synaptic then wants to remove the programs that depend on these packages... I don't want to do that.

---

### Post by willywonder86 on 2006-09-17
Still not fixed this problem yet and have no idea how to, but now I cannot install one of my updates I wonder if it is related?




The following problems were found on your system:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.47_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.47_i386.deb)
  Connection failed [IP: 195.248.90.54 80]

---

### Post by willywonder86 on 2006-09-17
Looking at the file it says its a security update so how do I fix it? as I am not sure if its risky not to anyone with ideas?

---

### Post by droogy on 2006-09-17
> **willywonder86 said:**
> Looking at the file it says its a security update so how do I fix it? as I am not sure if its risky not to anyone with ideas?
Solution:  Remove checkinstall.  Apply changes, then reinstall checkinstall.  It has now stopped nagging me for the update.

---

### Post by willywonder86 on 2006-09-18
Thanks for that works fine now :)

---

### Post by ozPATT on 2006-09-19
removed them permanently or just until you next update?

how do i remove checkinstall?

---

### Post by tandre75 on 2006-09-19
> **droogy said:**
> Solution:  Remove checkinstall.  Apply changes, then reinstall checkinstall.  It has now stopped nagging me for the update.

Doesn't work for me.  Last time I posted I had 4 updates, and now I have 13 updates waiting.  I cannot even uninstall the offending packages.  I have tried to uninstall each package seperately, and I have tried uninstalling them all at once, but it always stops with an error like "E: automatix: failed in buffer_read(fd)."  Automatix isn't always the program that doesn't uninstall/update, but hopefully you get the idea.

Any other ideas?

---

### Post by j5tixc on 2006-09-22
Same thing for me... Also flashplugin is screwing around, how bout checking those auto-updates so they work? If I look at adept updater it says "Checkinstall upgradeable no change", if I select it to change it wants to remove installwatch which I'm afraid to do....

Removing and reinstall might have done the trick though...

---

### Post by dmizer on 2006-09-26
i have this problem too.

1) i did not use automatix
2) i do not have checkinstall installed

same error with updating.  seems to be a problem with libxvidcore4

---

### Post by dmizer on 2006-09-27
um ... the libxvidcore4 package was VERY VERY broken on my machine.  it was hosing everything.

this package comes along with gstreamer0.10-plugins-bad-multiverse, so if you've used some quick utility or some guide to get video to work on your machine, this is probably where the package came from.

i could not even remove either of these packages using synaptic (when i tried, it locked up my system) or using aptitude.

the only way i was able to fix this problem was to perform fsck in safe mode.  it repaird several problems direcly related to libxvidcore4, and then i was able to get my updates.

i was also able to remove both packages after the repair and my system's back to normal.

you can do fsck on your install with your live cd.

edit: fortunately removing these packages seems to have had no adverse effect on playing video or dvd's (so far).

---

