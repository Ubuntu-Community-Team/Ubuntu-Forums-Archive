---
title: "Setting up VirtualBox to run Vista"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by _Silhouette_ on 2008-04-19
Hi, I've read through some threads here and some links in google, but I'm still confused with how to setup Vista to run in VirtualBox.

I'm at the "Create New Virtual Machine" screen, where it's asking me for a boot hard disk or something like that. I'm confused as to what to do.

I already have Vista installed on the C:\ drive (I'm dual booting Ubuntu via external hard drive).**I'd like to have Virtualbox use, if possible, my existing installation of Vista.** If that's not possible, is there a way to set it up so it won't erase my existing installation or take up huge amounts of space on my external hard drive running Ubuntu? Thanks!

---

### Post by TenPlus1 on 2008-04-19
Basically the hard-drive setup in virtualbox allows you to make a virtual partition on your ubuntu installation that it will use to install Vista on... set it to around 4000mb for a basic install to test things out as 4gb should be more than enough to start with...

---

### Post by george9233 on 2008-04-19
Virtual box need its own specific virtual hard drive image, so there's no way to use the existing installation. After setting up all the things, you need to press settings and in "CD/DVD-ROM" let it mount the Vista CD you've got. After installing it to the virtual hard drive you no longer need to mount it. You may also want to adjust video memory settings since Vista requires much video memory, and to enable audio is also recommended.

---

### Post by Can+~ on 2008-04-19
Virtualbox fakes a filesystem. It creates a file (.vdi) that will fool the OS making it think that he's on a real hard disk.

You can't use a partition that already exists for the same reason. Make the "hard disk" with dynamic space and set it a minimum space, more than 7GB I guess, since Vista is pretty big (never installed it though).

---

### Post by _Silhouette_ on 2008-04-19
Okay, got an error while trying to start up Vista:


```
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

---

### Post by the8thstar on 2008-04-19
Hmm, I beg to differ with what has been said before. You CAN in theory run an existing partition however the procedure is quite complex and if you screw up, you'll mess up your setup in VirtualBox and your actual Vista partition altogether.

Personally, I've never tried this option because of its potential inherent danger.

More info can be found here: [http://www.virtualbox.org/wiki/Migrate_Windows]("http://www.virtualbox.org/wiki/Migrate_Windows") I also advise you to look into the help file that's included with VirtualBox, as there's an entire section focusing on just that, running 'raw' partitions.

Hope this helps.

---

### Post by _Silhouette_ on 2008-04-19
HELP! I changed root and my login to be in the virtualbox group, and when I restarted my computer it gave me crazy error messages, forcing checks and doing all kinds of crazy things. I hope I didn't mess up my computer by installing Vista via VirtualBox???!

---

### Post by anewguy on 2008-04-19
As the 8th star mentioned, you can indeed run off an existing partition - I did that with Windows XP for a while.  You need to read through the help in virtualbox, particularly the advanced part and it will talk about using vboxcommand and show you how to do this.  Would I, based on my experience, recommend it?  Honestly, no.  Each time you switch between virtualbox and a true boot (such as from the dual boot menu from grub) I had to re-register Windows.  Microsoft wasn't taking too kindly to that.  I even eventually ran into a point where Windows would no longer boot from either method.

My recommendation, the same one made to me that I decided against when I first started, is to bite the bullet, backup everything you need from Vista, then add the partition space to Ubuntu and install Vista in virtualbox.  You will want to be sure you have a lot of memory and a lot of cpu horsepower or it's not really worth it.  Also, go the the vbox makers site and download the other version (it's free, but not open source).  It supports USB devices.

As with any virtual machine, particularly for Windows, don't expect to be able to run some of the games.  While improving, video is not there yet. 

Hope that gives you something to think about.  You could always backup everything and then try the direct partition method, but I seriously wouldn't recommend it.  :):)

---

### Post by the8thstar on 2008-04-19
(... what did I say? ...)

Okay **_silhouette_**, just for clarification, what are you talking about exactly:

1. vboxusers in User control?
2. Ubuntu login?
3. Vista login?

Final question: why did you change your root and login?

---

### Post by _Silhouette_ on 2008-04-19
Yes, I added root and my login to the vboxusers group.

After I made set up Vista and did that, I got some creepy errors about forcing a disk check and something about errors. I'm real nervous about this, and am now backing up all my important files to to my C:\ drive before I try to go back in again.

I hope I didn't just ruin Ubuntu by doing this...

---

### Post by the8thstar on 2008-04-20
I assume you have saved your important documents.

Now let's see what happens when you reboot your system (not in virtualbox). If your Ubuntu is screwed (which I doubt) I'll try and help you out.

---

