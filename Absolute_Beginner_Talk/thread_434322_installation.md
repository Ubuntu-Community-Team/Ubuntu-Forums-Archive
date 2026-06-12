---
title: "installation"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Boxers on 2007-05-05
Hello need assistance.......I have a Compaq SR1250NX that has windowsxp home version on it, but the windows has become corrupt in the registry. I want to wipe the window off this hard drive and install Linus as  standalone machine........any suggestion on getting windows xp off the drive and installing Ubuntu on it

---

### Post by starcraft.man on 2007-05-05
> **Boxers said:**
> Hello need assistance.......I have a Compaq SR1250NX that has windowsxp home version on it, but the windows has become corrupt in the registry. I want to wipe the window off this hard drive and install Linus as  standalone machine........any suggestion on getting windows xp off the drive and installing Ubuntu on it

Ummm, if you have nothing to back up or really important. Pop in the live CD and use the guided installation, then use the migration assistant if you need it. Should be really easy if you ONLY want Ubuntu. Be prepared for a culture shock though when you start to use it constantly. Might wanna read Ubuntuguide.org in my sig in conjunction with psychocats.com [here]("http://www.psychocats.net/ubuntu/index.php") read the beginning section to understand some of ubuntu before installing :)

You may want to look [here]("http://linuxappfinder.com/windows?page=1") for windows alternatives if there are any programs that are vital to you.

---

### Post by Tux Aubrey on 2007-05-05
You will be given that option during the partitioning step during the installation.  You can choose to have Ubuntu's "/" (root) partition take over the whole hard-drive and just leave a few gig for your swap file.  

That will work just fine.  There are more sophisticated ways to set up your partitions but if this is your first linux install, you probably want to keep it simple.

Check out this great "how-to" web site [[COLOR="Navy"]_http://psychocats.net/ubuntu_[/COLOR]]("http://psychocats.net/ubuntu/").  It has a good section on planning your partitions.

Good luck and welcome.

---

### Post by starcraft.man on 2007-05-05
> **Tux Aubrey said:**
> You will be given that option during the partitioning step during the installation.  You can choose to have Ubuntu's "/" (root) partition take over the whole hard-drive and just leave a few gig for your swap file.  

That will work just fine.  There are more sophisticated ways to set up your partitions but if this is your first linux install, you probably want to keep it simple.

Check out this great "how-to" web site [[COLOR="Navy"]_http://psychocats.net/ubuntu_[/COLOR]]("http://psychocats.net/ubuntu/").  It has a good section on planning your partitions.

Good luck and welcome.

Just one note, it is highly advisable to make a seperate /home directory formatted with as much hard drive as you would like to use for storage. Format it with Ext3 and make sure it is logical. Its important to do this, so that if you ever screw up your Ubuntu OS you can just reinstall Ubuntu and get access to all your files. Root (/) only really needs 6-8 Gigs, and swap 2-3, rest can be home. Read up on psychocats though, there is more info on this. :)

---

