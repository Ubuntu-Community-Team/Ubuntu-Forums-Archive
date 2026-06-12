---
title: "Random Crashing"
date: 2007-02-02
forum: Apple PPC Users
---

### Post by jernomer on 2007-02-02
Hi,

I am running 6.10 on a Powerbook (1.25, 2 GB RAM) and I have been getting these crash reports the last few times I have booted into Ubuntu. First, the report said that "python2.4" crashed, then the next time it was "python", and this last time I booted up Ubuntu it was "esd". I am not sure what to do.

I do not know if this is related but I am unable to open Synaptic Package Manager and many other applications. I some times can open Firefox but it will ultimately crash on me.

Any ideas? I did just do a fresh re-install of 6.10 yesterday and these issues are all happening after that.

---

### Post by pauljwells on 2007-02-02
On my powerbook I had random crashes until I disabled 'powernowd' in System/Administration/Services. After that it was ROCK solid

---

### Post by jernomer on 2007-02-02
> **pauljwells said:**
> On my powerbook I had random crashes until I disabled 'powernowd' in System/Administration/Services. After that it was ROCK solid

Thanks for the advice. I disabled that service and so far so good. What does that service do anyway?

---

### Post by pauljwells on 2007-02-02
It allows the processor to throttle to a lower clock speed under low load, which extends battery operation time.

I found on my 12" AlPB that even in OSX I had to disable the auto switching in power manager or OSX would hang too.

---

### Post by jernomer on 2007-02-02
Thanks. Okay, things seem to be running okay, but...

I am still unable to open Synaptic or Update Manager. They both stall when it says "Building dependency tree" and then just quit.

Also, the last couple of times I rebooted the fsck menu came up right before it booted into Ubuntu. Any experience with any of this?

---

### Post by pauljwells on 2007-02-02
hmmm

fsck should kick in every thirty reboots. You can force it to run on the next reboot by typing 

```
sudo touch /forcefsck
```

worth a try to make sure your filesystem is intact.

Synaptic and update manager are both front ends to apt-get. I would try running apt-get in a terminal and it will tell you what's upsetting it.

```
sudo apt-get update
```

this will reload all your repositories

then

```
sudo apt-get upgrade
```

will bring your system up to date.

You might want to try

```
sudo apt-get install ubuntu-desktop
```

this will ensure you have a full edgy distribution

---

### Post by jernomer on 2007-02-02
Thanks a lot for all the suggestions. I will give them a try.

---

### Post by jernomer on 2007-02-02
Paul, thanks so much for the help. I ran the commands you suggested and it seems to have worked - it updated to python2.6 and a couple of other things. Thanks, again.

---

### Post by pauljwells on 2007-02-03
No problem!

I've posted way more questions than answers on these forums - it's nice to be able to give something back

Welcome to Linux

PS - if it will let you, add powernowd to this thread's tags to help people find it in the future

---

### Post by jernomer on 2007-02-03
It looks like I should be able to add "powernowd" as a tag to this thread, but it does not actually take it when I attempt to add a tag. There must be something wrong with the "adding a tag to an already published thread" feature. Oh well.

---

