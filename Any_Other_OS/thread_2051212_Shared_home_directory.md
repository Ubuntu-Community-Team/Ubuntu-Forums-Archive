---
title: "Shared home directory"
date: 2012-09-01
forum: Any Other OS
---

### Post by newb85 on 2012-09-01
I recently installed Ubuntu 12.04, Linux Mint 13 (Cinnamon), Peppermint 3, and Lubuntu 12.04 on separate partitions on the only HDD in my machine, using an additional partition for /home shared among them.  Now, when I boot into Mint after rebooting from one of the other three, I'm greeted by a dialog to the effect of:
> “You have chosen Cinnamon as your session, but the default is [Ubuntu.desktop/Peppermint.desktop/Lubuntu.desktop—whichever I just came from].  Do you want to change the default to Cinnamon”.  
In all four systems, the desktop configuration files are located in /usr/share/xsessions.  All four systems are apparently designed to change the default desktop  configuration to whatever you choose, and all four apparently store that default setting somewhere in the /home directory (of necessity, to avoid requiring an administrative password to change).  That much makes sense, but it creates an interesting scenario where the four systems fight one another for the default desktop configuration, each setting it to a session the other systems don't have installed. So far, this hasn't led to any serious problems, and the three excluding Mint silently take care of the problem by switching to an available desktop configuration.

Does anyone have a reason I should be concerned about the current arrangement?

Can someone tell me where specifically the default desktop config is stored?  Is there a way to make it system dependent.

Can anyone tell me how to make Mint take care of the problem silently, too?  Do I need to change login managers for this?

---

### Post by 2F4U on 2012-09-01
Linux is designed as a multi-user system. So, to enable different users to work with the same applications, but still have different configuration settings, these are stored in the home folder of the user. This not only affects the desktop environment, but other applications too. Therefore, it is never a good idea to share the home folder across distributions. Instead, you should have a small home folder on each distribution and a seperate partition that only stores your data. This partition can be shared across distributions without problems.

---

### Post by oldfred on 2012-09-01
+1 on 2F4U's comments.

I am aggressive about moving data out of /home so it is less than 2GB with most of that .wine just for Picasa. I even move some hidden folders like the Firefox & Thunderbird profiles so I can also share them from the data partition. Since my /home is small I keep it inside my / (root). 

Those that say you can share a /home partition assume you do use a different user in each distribution so each has its own settings & files within /home folders.

---

### Post by malspa on 2012-09-01
This is a perfect example of why I don't use a shared /home partition, although as oldfred mentioned, if the usernames are different for each distro, a shared /home partition can work out okay.

---

### Post by newb85 on 2012-09-01
I may need to rethink my strategy.  I intentionally shared the home folder because I specifically wanted the settings for some programs to be the same in all distros.  I guess I just didn't think the consequences out far enough.

To me, having a different user for each distro defeats the purpose of sharing a /home partition.

@oldfred - you mentioned moving data (e.g. your thunderbird & firefox settings) out of the home directory.  How does one go about doing that?  Wouldn't those programs need to be instructed to look for the settings in the new location?  Is there a reason I couldn't do the same with the file that stores the default desktop config?

---

### Post by oldfred on 2012-09-01
The desktop configs are small enough I might copy them over if you are sure you want them but I would not do that more than at the beginning.

With Thunderbird & Firefox you edit profile.ini to look into the new location.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I start Firefox once to create the new default profile and profile.ini then change the profile.ini to my standard profile location. I already have to data partition mounted in fstab so path is valid.

All the data folders in /home are folders in my data partition. I delete the standard folders before I have a chance to save anything and link my common data folders in their place.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

