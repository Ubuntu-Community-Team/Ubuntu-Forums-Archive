---
title: "I want to remove banshee..."
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by darweth on 2007-01-05
Hello... I installed the latest version of Banshee via the instructions that can be found at: [http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html](http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html)


Due to some problems... I would like to fully uninstall/remove what I put in.  I have no idea how to do that since I compiled it (ipod plugin, plugins and all).

Can anyone post a means of removing it?  Thanks.

---

### Post by darweth on 2007-01-05
I try to get the directories I used to sudo make uninstall, but can't...

bepogi@bepogi-desktop:~$ cd banshee-0.11.3
bash: cd: banshee-0.11.3: No such file or directory
bepogi@bepogi-desktop:~$ cd banshee-official-plugins-0.11.3
bash: cd: banshee-official-plugins-0.11.3: No such file or directory



That is where I installed them in the first place though.  Hrm?

---

### Post by jpeddicord on 2007-01-05
If you compiled it, go back to the folder where you downloaded Banshee. This should be the same folder you ran `sudo make install`.

All you [should] have to do is type:
```
sudo make uninstall
```

Jacob

---

### Post by darweth on 2007-01-05
Hehe, yeah.  I googled on my own a bit and found that out, but it won't let me. :/

Maybe a bit dumb here... If I install the OLD Banshee from the repos, will it overwrite my current one?  Could I then remove it completely that way?

---

### Post by darweth on 2007-01-05
I am still stuck on removing Banshee, but I have another general ubuntu question.  If I am concerned about packages hanging around from this install or OTHERS that are no longer used by anything... just sudo apt-get autoremove?  is that correct?

:)  thanks.  still need banshee gone tho!


OOPS ****edit*******   Just read:
Don't run apt-get autoremove as suggested after dash removing. If you follow this advice and do so, it will deinstall the Ubuntu minimal package. The consequence is, that also the upstart package will be removed. On the next startup the system will stop booting in the initrd-shell. This will happen with all installed kernel-images and so the system is rendered useless.

Guess I better not do that.  What is the best way to remove idle packages?

---

### Post by PilotJLR on 2007-01-05
What do you mean "it won't let me"?? the sudo command should let you remove this, pls post the output of whatever error you are getting.

And anything you compile and install manually (with make) will not be in the apt database. In the future, install using apt-get, unless there is a compelling reason not to... as that will make installing and uninstalling much easier.

---

### Post by darweth on 2007-01-05
> **PilotJLR said:**
> What do you mean "it won't let me"?? the sudo command should let you remove this, pls post the output of whatever error you are getting.

And anything you compile and install manually (with make) will not be in the apt database. In the future, install using apt-get, unless there is a compelling reason not to... as that will be installing and uninstalling much easier.

Yeah, I will stick to that from now on.  I just wanted to try the latest version.  

The problem is I can't get to the directory that I used.

bepogi@bepogi-desktop:~$ cd banshee-0.11.3
bash: cd: banshee-0.11.3: No such file or directory
bepogi@bepogi-desktop:~$ cd banshee-official-plugins-0.11.3
bash: cd: banshee-official-plugins-0.11.3: No such file or directory

those directories are where i did sudo make install

---

### Post by wounded on 2007-01-05
You must have deleted the source tree that you used during the isntallation. I'm not sure if there is a way of uninstalling it now. Instead of 'make install' next time I would use 'checkinstall' instead - That will create a .deb file that you can install/remove more easily.

---

### Post by PilotJLR on 2007-01-05
the "sudo make install" part likely installed the binaries in another location, like /usr/bin.

Try doing a "whereis banshee" to see where the banshee binary is.

---

### Post by darweth on 2007-01-05
I got too confused going through everything so I finally just installed it via Synaptic and then promptly removed it.

a whereas banshee showed it to be gone.  i did that before and there was all kinds of crap.

hrmmm... i guess that is the easy way.

---

### Post by jpeddicord on 2007-01-06
Oops, I guess I should have hit Reload on the topic before I posted. :rolleyes: 

If installing then uninstalling via Synaptic works, then I suppose there is no harm in it.

---

