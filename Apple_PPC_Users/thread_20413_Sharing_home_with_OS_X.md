---
title: "Sharing home with OS X"
date: 2005-03-16
forum: Apple PPC Users
---

### Post by cinnabar on 2005-03-16
Hi All,
      I'm new to Ubuntu (but not linux: Mandrake, Gentoo, RedHat, and Mepis) and OS X.  My wife just bought me a 14" iBook and I'd like to put Ubuntu on it to use some of my favorite linux apps.  I'd like to set it up with only one /home directory that both OS X and Ubuntu use to avoid wasted space and unnnessary duplication of files.  Is this possible?  If so, do any of you have a preference for where to put the /home folder?  Under Ubuntu, OS X, or as it's own partition?  

Thanks!

---

### Post by kadymae on 2005-03-16
Well, I'm a nearly complete Linux noob, but on my dual boot system neither OS is aware that the other exists.

So, while it might be possible to browse the contents of your "other" drive, neither Ubuntu nor OS X do this out of the box.

---

### Post by Down8ve on 2005-03-16
Sharing the same home directory is not practical.  Linux and Mac use vastly different file systems.  

However, it is possible to move files between the two. I've tried it, but had permission errors.  Someone what to link a How To?

DSM

---

### Post by spoetnik on 2005-03-17
The best way to solve the permission problems is to create a ubuntu user with the same user- and group-ID as in OSX.

Boot to OS X, open your terminall.app. type 'ID' and check your User ID and Group ID.
Boot to ubuntu and create a user with the same username as you have in OSX, and the same user ID and Group-ID. 

I use this to have no permission problems on my mounted 'Data' partition, and share files between OSX and ubuntu.

---

### Post by cinnabar on 2005-03-17
Perfect.  Thanks spoetnik (and everyone else too).

---

### Post by zxee on 2005-03-17
I hope it's not a problem for me to tag on to this thread. I am interested in the orginal question.
I haven't used ubuntu yet but have used many types of deb on pc & ppc.
How well does MOL work with ubuntu? and could that be a solution to this?
i.e. run osX on linux and then all the files would/should be accessible.
What say you?? Thanks

---

### Post by Ptero-4 on 2005-03-17
[QUOTE=zxee]I hope it's not a problem for me to tag on to this thread. I am interested in the orginal question.
I haven't used ubuntu yet but have used many types of deb on pc & ppc.
How well does MOL work with ubuntu? and could that be a solution to this?
i.e. run osX on linux and then all the files would/should be accessible.
What say you?? Thanks[/QUOTE]
Welcome to Ubuntu.

MOL works very well on Warty. (I'll test on hoary in a few days). the kernel modules for the warty version of mol are on [www.petrvz.net/~pvz/kmods](www.petrvz.net/~pvz/kmods). You can have your stuff accesible to osx and linux, but you'll have only a one way transfer though (mol doesn't allow to have a volume mounted writable on both linux and MacOS 9/x) so if you move files to and from linux simultaneously a lot you'll find yourself closing and opening mol a lot.

Hope this helps

---

### Post by Leonida on 2005-03-17
I'm running mol (OSX 10.3.8 ) with Hoary. (see [screenshots](http://www.freesmug.org/forums/foss.nbs/275805139923))
I sahre files from ubuntu to OSX and vice-versa using FTP.
Run Mol, on OSX activate FTP on Sharing panel in System Preferences.
Under OSX get your IP adress.
On Ubuntu open Places->Connect to server.
Use Public FTP, my ip is 192.168.40.2, port 21, set your username and password, connect.

Sorry geek, really a "make it yourself" solution, really not pure and clean, but it work.

---

### Post by farruinn on 2005-03-18
[QUOTE=Leonida]I'm running mol (OSX 10.3.8 ) with Hoary. (see [screenshots](http://www.freesmug.org/forums/foss.nbs/275805139923))
I sahre files from ubuntu to OSX and vice-versa using FTP.
Run Mol, on OSX activate FTP on Sharing panel in System Preferences.
Under OSX get your IP adress.
On Ubuntu open Places->Connect to server.
Use Public FTP, my ip is 192.168.40.2, port 21, set your username and password, connect.

Sorry geek, really a "make it yourself" solution, really not pure and clean, but it work.[/QUOTE]

*If* you're going to use MOL for file transfer though that's exactly how I would recommend doing it, however I think that's a lot of overhead if all  you want to do is share files.  I think he best way to share files between a linux install and a mac os install is to have a vfat partition which both Linux and OS X can read/write without problems (write functionality to HFS+ in linux is a bit iffy at best).  That being said, I personally use an outside ftp server (provided by my school ;-) ) to share files when I have to.

Also, I've been staying up to date in Hoary the past week or so and haven't run into any MOL breakage (just as long as I remember to reboot after kernel upgrades ;-) )

---

### Post by dherren on 2005-03-27
[QUOTE=spoetnik]The best way to solve the permission problems is to create a ubuntu user with the same user- and group-ID as in OSX.

Boot to OS X, open your terminall.app. type 'ID' and check your User ID and Group ID.
Boot to ubuntu and create a user with the same username as you have in OSX, and the same user ID and Group-ID. 

I use this to have no permission problems on my mounted 'Data' partition, and share files between OSX and ubuntu.[/QUOTE]

Easy enough, but how do you even get ubuntu to see the OSX partitions? My install certainly doesn't.

---

### Post by farruinn on 2005-03-28
Two things: you need to load the hfsplus kernel module (sudo modprobe hfsplus).  You'll probably want to just add hfsplus to the /etc/modules file (sudo echo hfsplus >> /etc/modules).

The other thing you need to do is add an appropriate line to your /etc/fstab.  Something like this should work:
```

/dev/hda10     /mnt/mountpoint     hfsplus     defaults,uid=[mac osx uid],gid=[macosx gid],rw     0     0
```

You'll want to change the partition to wherever your OS X home directory is and of course substitute the uid and gid from OS X.

-Nathan

---

### Post by Leonida on 2005-03-30
To mount ubuntu partition on OSX you can use [ext2fsx](http://sourceforge.net/projects/ext2fsx/).
Screenshot [here](http://www.freesmug.org/forums/foss.nbs/458380304783).

---

### Post by Leonida on 2005-04-03
Read also this Yellow dog How to [Mounting HFS+ Partitions](http://www.yellowdoglinux.com/support/solutions/ydl_4.0/hfsplus.shtml)

---

### Post by paulsomm on 2006-03-19
I simply enabled folder sharing in ubuntu, which installed samba. I shared my home folder, then under OS X from the finder I do "Go / To Server" and type in "smb://my.ubuntu.ip.address/myname" and I share files that way.

---

### Post by engla on 2006-03-19
Regarding the original topic, I tried sharing home directories with OSX and ubuntu. Since I was making clean installs, the uid thing was no issue, I simply changed it in OSX and chowned my home directory.

I used OSX v10.3 and ext2fsx to have the home on an ext2 partition. It seemed to work fine, and I even used the same .bashrc, but with a conditional block for aliases that only made sense on one os...
I'm not sure I would recommend that setup though, and I didn't test it more than a week until I had to abandon it when I installed OSX v10.4 that can't mount ext2 and even less have a home dir on such a partition.

---

