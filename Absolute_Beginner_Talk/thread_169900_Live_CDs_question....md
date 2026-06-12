---
title: "Live CDs question..."
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-05-03
I'm a bit puzzled about that...
The liveCD doesn't make any changes to the computer, right?
If so, how can I install packages? where does it download it? where does it save my settings?

really weird that one...

---

### Post by linmick on 2006-05-03
You actually can install using the synpatic manager. But it will install everything to your ram. That is you can keep adding and removing packages with your play space. The livecd should not worry you, it will install and remove from ram. But you will need to do a bit math. That is  , the package when it says how much disk space it will take. Really means how much ram, so don't go overboard or you'll end up crashing. I personally installed gnomebaker, kdar and few other apps to the allowed ram space. But remember once you reboot it will be gone. Their are livecd's already that an save the changes back to your cd.  But with ubuntu livecd   it does not happen. Also what i found a small trick is to run  sudo apt-get clean while playing 100% from  ram.  That way  it free the pretend harddisk space to have more ram. Also remember don't mount by mistake any of your hard disks or you can actually overwrite data. But strictly from ram your ok.

When your   doing everything 100% off the ram it still saves everything in the same place. Again, it will only save your settings for the time your pc is running. But if you reboot it will disappear unless you use one of those  live cd's that  either save back to your  burner  cd or makes a  home on your actual hard drive.

In ram or not your packages are saved to /var/cache/apt/archives.

The good thing of running strictly from ram is you never can mess up.  You can always reboot your computer and start fresh. The bad is the limit  what you can do is  based on the available ram space you have to use.

---

### Post by Caligula on 2006-05-03
ah, alright...
I'm just trying to get somebody sorted woth all this, and I though it woul help if I knew how it works first...:rolleyes: :D

---

### Post by linmick on 2006-05-03
Glad that could clear few things up afterall we are all in the learning and sharing  of UBUNTU!:)  recently actually made a switch from another disto.:KS I personally given up on ubuntu because of a  showstopper bug. But   as time went on noticed the  devs (while bug still open) really really try hard to  listen to the userbase.  It seems as  as time allows they are  knitting and quilting fixes. Who could ask for more then care here?

---

