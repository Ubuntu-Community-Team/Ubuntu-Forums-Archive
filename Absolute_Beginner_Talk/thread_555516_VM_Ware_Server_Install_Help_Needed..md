---
title: "VM Ware Server Install Help Needed."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by rhardie on 2007-09-20
I'm a fairly new user of Ubuntu.

I am attempting to install VMWare server and get a message that a previous version was installed and then:

"If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.

If it was installed through Ubuntu, you must purge (completely remove) the old package."

If I attempt to continue:

"E: /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb: subprocess pre-installation script returned error exit status 1"

Google search indicates I'm supposed to run an uninstall program.  Not sure what to do from here.

Thank you in advance.

---

### Post by finer recliner on 2007-09-20
try 

```
sudo vmware-uninstall.pl
```

---

### Post by rhardie on 2007-09-20
I tried that and got a "command not found" so I was guessing that I am not running a program correctly.  I have not yet learned how to run programs from the command line.  But, I'm "getting there". :)

I'm still open to suggestions.

Thank you for your assistance.

rhardie

---

### Post by Scrib on 2007-09-23
Did you get anywhere with this - I have the exact same issue.

---

### Post by odiseo77 on 2007-09-23
Maybe the uninstall script is hidden somewhere not in your $PATH ? Have you people tried running ***sudo updatedb && locate vmware-uninstall.pl*** to see where the script is located? (you probably have to purge the package later with ***apt-get remove --purge vmware-server*** (or whatever the package is named)).

Regards.

---

### Post by rhardie on 2007-09-23
I have not.  I'm attempting to get hold of a friend of mine who is a very good Linux person, but he is difficult to reach.  I'll be happy to share the answer when I get one - from what ever source.

Regards,

Rhardie

---

### Post by Scrib on 2007-10-27
rhardie  - Did you get an answer?

---

### Post by rhardie on 2007-10-27
I did not receive an answer nor have I figured out the problem.  I did attempt to load virtualbox, but I get an error on that and have not been able to fix it either.  I'm generally at a Linux User Group on Wednesdays and get some help there but no answers at this time.

---

### Post by Scrib on 2007-10-31
OK keep me posted. I use VMWARE on Windows all the time and if i can get it working on Linux I would be well impressed.

---

### Post by rhardie on 2007-10-31
I must have "reverse Midas Touch"; everything I touch turns to poop.

Each time I attempt to load either VMware or Virtual Box, I get some command line error that I can't get beyond.

I did find what appears to be a workable (for someone ELSE) procedure for 7.10 as follows:

[http://ubuntuforums.org/showthread.p...install+vmware](http://ubuntuforums.org/showthread.p...install+vmware)

I got as far as step 4 and then got an error.  I posted a reply on a thread asking for assistance.  [http://ubuntuforums.org/showthread.php?t=597688](http://ubuntuforums.org/showthread.php?t=597688)

I am really looking forward to running virtualization on my server so I can impliment my industry specific software applications on a Linux platform.

Regards,

Rhardie
Austin, Texas

---

### Post by volksman on 2007-10-31
Based on your first post try this:

```
rm -rf /etc/vmware
```

Then try the vmware installer again....

---

### Post by tact on 2007-10-31
first up...  if you have ever installed any flavour of vmware (eg vmware-server), then uninstalled it and tried to install a different flavour (eg vmware player) ....  you will may very well come to grief.

you have to completely..and I mean COMPLETELY remove any previous install - not just using the uninstall process... but after that go on a hunt and destroy mission to delete any and all config files or directories related to vmware still left on your HDD's.

with a cleansed system ... then you will have success installing vmware server according to the link someone else posted above.

exactly what uninstall process to use depends on how you installed.  did you install from source?  only if so will you find the vmware-uninstall.pl script.

did you install from synaptic?  or deb?  then you need to use dpkg or synaptic to uninstall.

then...as mentioned above...  go on that hunt and kill mission to locate all configs or directories related to vmware and delete them.

---

### Post by volksman on 2007-10-31
while I've never installed vmware from a deb (only from source) I have installed and re-installed many times.  The only directory that the vmware installer really cares about is /etc/vmware....so if its not there then vmware will perform the install and overwrite any previous versions it finds....

I can't comment on a source install on top of a deb install though.

---

### Post by tact on 2007-11-01
Ya volksman - if you only ever installed from source then reinstalling is fine.

My comments are for those who had (for example) vmware-player installed via synaptic, and removed via synaptic (its in the repos)....  then wishing to install vmware-server (from source or anywhere else - its not in repos).

For this specific situation (not your situation) uninstall/reinstall alone is not sufficient.

---

