---
title: "sudo: must be setuid root"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Pyrollis Ah Firos on 2007-10-31
I posted this in other thread but I'm not getting any replies so I'm starting a new thread here. Hope you all can help! Thanks in advance!

__________________________

It's strange that I got it just now. I was doing my usual business last night and the network was fine and all. Today, I saw that my computer has shut down from a different distro (Ubuntu 7.04) and I tried to boot it back in that distro but the GDM error came up so I decided to go back to my usual distro; Ubuntu 6.06. When I went back in and for some reason the network isn't working right, I can't sudo for anything, and I can't even get some programs (synaptic, network configuration, programs that requires sudo to be executed) to run. I double clicked on one program. It would either not appear at all, or shows up then disappears after a while. The "not appear at all" part is the most common problem. So far what I did last night was delete some files and I didn't think it would be that harmful to Ubuntu. It was some general files and not of any importance to the Ubuntu kernel. Could it be because I accidentally deleted something critical? I can log in my account but no network, can't do sudo (I keep getting the same message, sudo: must be setuid root) and I have tried the method mentioned above but no luck. I'm not sure if this is important but when I logged in my account in recovery mode, I saw this message, "-bash: no job control in this shell". I'm not sure if I'm supposed to have job control or is it just the default message? Also, when I tried to go from my user account to root, su root, I typed in the password but it said, invalid password, sorry.

Oh yeah, I also tinkered with the /etc/fstab file to make the usb device from nouser to user so I can automatically have my USB drive mounted when I plug it in. Could it be part of the reason why I'm experiencing this? Thanks in advance! 

~PAF

---

### Post by bks on 2007-10-31
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=219767") and don't forget searching the forums can yeild nearly all the answers you need without waiting for a reply.

---

### Post by Pyrollis Ah Firos on 2007-10-31
Already read that thread, plus searched high and low for any problems similar to mine. Already tried all of the suggestions and everything seems to be set up correctly but still can't do sudo. I know better to search before posting a new thread because there are already some threads on them and I already read them all and nothing did the trick so that's why I started this thread because two of the threads I read, I posted in them for help and no one replied to my post thus the new thread.

---

### Post by Pyrollis Ah Firos on 2007-11-19
Fellow Ubuntu users, 

I still am stuck with this problem. Does anyone know how to fix this other than doing a fresh install of Ubuntu? I want to use this because I spent a lot of time tinkering with this and don't want to start all over... Please help me :) 

~PAF

---

