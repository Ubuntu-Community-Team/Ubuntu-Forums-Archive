---
title: "boot script help"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by halitech on 2006-08-06
I've tried searching the forum and I've followed the instructions I found but I still cannot seem to get this to work. I'm not sure if I'm doing something wrong or just missing a simple step.

I have Xubuntu 6.06 running on an AMD k6/2 350 with 64 meg of ram. NO mouse so this has to be done totally by command line. I have it set so I can ssh into it and that works fine (thankfully cause I only have 1 monitor for 2 systems). 

what I am trying to do is have Shoutcast DNAS load on boot instead of login as I don't actually login unless I'm doing something over ssh.

I have followed the info from here mainly:

[http://www.ubuntuforums.org/showthread.php?t=140696&highlight=login+script+boot]("http://www.ubuntuforums.org/showthread.php?t=140696&highlight=login+script+boot")

I hav created a script which I think I did correctly:

#!/bin/sh
sudo ./sc_serv

but it does not run when I reboot. Any ideas on either a) what I'm doing wrong or b) a better way to get shoutcast to run on boot?

---

