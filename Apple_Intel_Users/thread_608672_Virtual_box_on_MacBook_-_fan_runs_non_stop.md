---
title: "Virtual box on MacBook - fan runs non stop"
date: 2007-11-10
forum: Apple Intel Users
---

### Post by mmtowns on 2007-11-10
Hello,
I have installed Gutsy via VirtualBox  (OSX host) on a MacBook.  I usually allocate 500mb of virtual memory and a 4gig virtual HD, although I don't think that's relevant information considering my problem.  **My issue is that when I run Ubuntu in VirtualBox, the laptop gets pretty hot - the fan runs almost 100% of the time. ** The fan stops pretty soon after I end my virtual machine session and/or if the virtual machine is idle/minimized for a while.  Has anyone else had this issue?  If so, is there a fix?

I've had similar issues when trying out other Ubuntu derivatives as well.

Thanks in advance for your thoughts.

---

### Post by Zelut on 2007-11-10
I suppose I have the same issue on my machine.. I never really took much thought to it other than "I'm now running two OSs, it's a heavier load on the machine..."

You could check out the solution on the [community MacBook support]("https://help.ubuntu.com/community/MacBook") page for increasing the fan speed.. not sure how much that'll help but its worth a shot.

---

### Post by mmtowns on 2007-11-10
Thanks for the suggestions, Zelut.  I guess I should have mentioned that I had tried this out already...

Here's the error I get after running

```
sudo modprobe applesmc
```


```
FATAL: Error inserting applesmc (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/applesmc.ko): No such device
```


Perhaps running Ubuntu through a virtual machine does not allow me to control the fans?

---

### Post by cyberdork33 on 2007-11-10
> **mmtowns said:**
> Thanks for the suggestions, Zelut.  I guess I should have mentioned that I had tried this out already...

Here's the error I get after running

```
sudo modprobe applesmc
```
```
FATAL: Error inserting applesmc (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/applesmc.ko): No such device
```
Perhaps running Ubuntu through a virtual machine does not allow me to control the fans?
nope

you are running two machines in one, it will get hot, that is how it works.

---

### Post by siepo on 2007-11-11
I had 100% CPU usage and a non-stop fan when I ran Win95 under VMware. I understand it has something to do with 16-bit OS-es not being able to idle properly; I don't know off-hand the technical expression.
On my system, Windows 2000, XP and Vista don't monopolize the processor, either under VMware or under VirtualBox.

---

