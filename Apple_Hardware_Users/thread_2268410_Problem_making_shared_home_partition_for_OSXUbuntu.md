---
title: "Problem making shared home partition for OSX/Ubuntu"
date: 2015-03-08
forum: Apple Hardware Users
---

### Post by mageejp on 2015-03-08
I have a Macbook 6,1 (2010) with dual boot OSX 10.9 and Ubuntu 14.04 LTS. I tried making a shared home partition a la this how-to:
[http://www.tuxation.com/creating-home-partition-mac-linux.html](http://www.tuxation.com/creating-home-partition-mac-linux.html)

I logged in as root, moved the Users folder to the shared, unjournaled hfs+ partition, and removed the old Users folder as directed. I then rebooted to check how that worked, and OSX chimes, shows the Apple with a 'working' icon underneath, then shows a progress bar. Once it reaches around 30% the computer shuts itself off.

Thanks to some other how-tos ([http://lnx2mac.blogspot.com/2010/09/moving-os-x-users-to-separate-partition.html](http://lnx2mac.blogspot.com/2010/09/moving-os-x-users-to-separate-partition.html)) I now see that there's more to do than just moving the folder and editing the fstab. I'd like to go in and make those further changes (setting up Users mount point, set up automounting of Users, setting permissions, etc), but I don't know how to get into the system. I can boot in OSX Recovery mode, or I can boot from an external HD, or I can boot into Ubuntu, but will I be able to change permissions, etc, if I'm not booted into the copy of OSX that's on my first partition?

---

### Post by este.el.paz on 2015-03-08
> **mageejp said:**
> I have a Macbook 6,1 (2010) with dual boot OSX 10.9 and Ubuntu 14.04 LTS. I tried making a shared home partition a la this how-to:
[http://www.tuxation.com/creating-home-partition-mac-linux.html](http://www.tuxation.com/creating-home-partition-mac-linux.html)

I logged in as root, moved the Users folder to the shared, unjournaled hfs+ partition, and removed the old Users folder as directed. I then rebooted to check how that worked, and OSX chimes, shows the Apple with a 'working' icon underneath, then shows a progress bar. Once it reaches around 30% the computer shuts itself off.

Thanks to some other how-tos ([http://lnx2mac.blogspot.com/2010/09/moving-os-x-users-to-separate-partition.html](http://lnx2mac.blogspot.com/2010/09/moving-os-x-users-to-separate-partition.html)) I now see that there's more to do than just moving the folder and editing the fstab. I'd like to go in and make those further changes (setting up Users mount point, set up automounting of Users, setting permissions, etc), but I don't know how to get into the system. I can boot in OSX Recovery mode, or I can boot from an external HD, or I can boot into Ubuntu, but will I be able to change permissions, etc, if I'm not booted into the copy of OSX that's on my first partition?

@mageejp:

You ***may*** get somebody here who knows how to do this to show up and give some insights, but, not to be a naysayer, that first link was copyrighted in 2010 . . . and "stuff" has changed in OSX & linux since then . . . and that may be some critical details are not the same.  OSX doesn't really like people messing with it, and the fact that it isn't even booting is a sign that something is now "rotten in OSX" from its review of the system.

From my beginner dual/triple boot experience on my similar MBPro I'd say to find another way to spend your time.  Either, if you want to access linux while in OSX then use a virtual machine app, FusionWare or Parallels, or VirtualBox . . . OR, when in Linux, Be in Linux; and when in OSX, Be in OSX.  From my experience with OSX, it doesn't "recognize" linux, meaning it doesn't show the linux partition as even exisiting, although it may show up in DU . . . and when in Linux many folders in the OSX Home are X-d out, some can be opened in linux, but many cannot.  The shared Home folder is a lot easier to do on the Linux side if you wanted to add various flavors of Linux OS and share the same Home.

Also, from the very fast read I did of that link, it mentions rEFIt, but rEFIt doesn't support OSX over 10.7 I believe, so if you were going to keep trying on this it should now be rEFInd that you would use to coordinate your booting . . . .

e.e.p.

---

### Post by mageejp on 2015-03-09
Yep, I've got rEFInd instead of rEFIt. The actual install of Ubuntu and dual boot all went smoothly. The only reason I would want to access OSX from outside is to repair the Users mount point... so I'm just not sure what my options are right now. Recovery mode will let me access terminal, but I'm not sure it will let me log in as root for my main install.

---

### Post by este.el.paz on 2015-03-09
> **mageejp said:**
> Yep, I've got rEFInd instead of rEFIt.  Recovery mode will let me access terminal, but I'm not sure it will let me log in as root for my main install.

Well, try it, worst that could happen is it won't let you log in as root, right?  Main thing to understand is that OSX should go in first, and whatever you do to OSX should be done first, and then add the linux details . . . .

e.e.p.

---

