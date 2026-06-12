---
title: "python2 logger module leaking file descriptors"
date: 2014-08-30
forum: Any Other OS
---

### Post by hamishmb on 2014-08-30
Hi,

I've been having an issue with a program I've been writing where the logger module from python 2 leaks the file descriptor for the log file to update-grub, when run from my function to start processes (I use it to pipe the output, so I can get live-updating command output to the user).
Here is some python2 code that will replicate the issue (but it will only work on an Ubuntu based distro).

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import subprocess
import logging

#Set up logging.
logger = logging.getLogger('Test')
logging.basicConfig(filename='/home/hamish/Desktop/log.log', format='%(asctime)s %(message)s', datefmt='%d/%m/%Y %I:%M:%S %p')
logger.setLevel(logging.INFO)

logger.info("Test.py started!")

def StartThreadProcess(ExecCmds):
    #Start a process given a list with commands to execute, specifically for this thread, as it also sends the output to self.UpdateOutputBox().
    #This now uses a set of default values, to keep it simple. It can be called with self.StartThreadProcess(ExecCmds=[], ShowOutput=True) etc. Only ExecCmds is compulsory.
    #Reset templog
    templog = []

    logger.debug("MainBackendThread().StartThreadProcess(): Starting process: "+' '.join(ExecCmds))
    runcmd = subprocess.Popen(ExecCmds, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)

    while runcmd.poll() == None:
        #Send given line to the outputbox and Log it too, if ShowOutput == True or if FullVerbose == True 
        line = runcmd.stdout.readline()
        templog.append(line)
        print line

    #Save runcmd.stdout.readlines, and runcmd.returncode, as they tend to reset fairly quickly.
    output = runcmd.stdout.readlines()
    retval = int(runcmd.returncode)

    #Add any missing output (this is what templog is helpful for: it'll contain only output from this command).
    for line in output:
        if line not in templog:
            templog.append(line)
            print line

    #Return the return code back to whichever function ran this process, so it can handle any errors.
    return retval

def UpdateGRUB2(PackageManager, MountPoint):
    #Okay, we've modified the kernel options and the timeout. Now we need to install grub to the UEFI partition.
    if MountPoint == "":
        if PackageManager == "apt-get":
            retval = StartThreadProcess(['update-grub'])
    else:
        if PackageManager == "apt-get":
            retval = StartThreadProcess(['chroot', MountPoint, 'update-grub'])

    #Return the return value.
    return retval

UpdateGRUB2(PackageManager="apt-get", MountPoint="")
```

It can be pasted into a file and executed with sudo to show the issue. I get the message:
> File descriptor 3 (/home/hamish/Desktop/log.log) leaked on lvs invocation. Parent PID 8379: /bin/sh

Where /home/hamish/log.log is my test log file.

Can anyone help me with this issue?

Thanks in advance,
Hamish

---

