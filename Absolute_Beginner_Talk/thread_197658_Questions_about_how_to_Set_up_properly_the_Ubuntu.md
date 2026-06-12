---
title: "Questions about how to Set up properly the Ubuntu"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by javierfh on 2006-06-16
Hello,

I'm novice into Linux and I have few basic questions.

I have read somewhere, that it is a good practice to have a partition for your own data, so if you update or re-install at some point you can format the partitions to do a fresh installation but still you have your data. Do people normally use that approach?

Second question it is about what will happened when the new release comes?
So now I'm running Dapper and lets assume that official release of edgy will be in December. If I keep updating the new patches everyday, does it mean that I will have then Edgy already by when the official release comes? Or when the release happens they will do major updates?
And, what is more convenient and why, to format all and do a fresh installation of Edgy from scratch or just update it from Dapper?

I'm trying to have it under control from the beginning and hope that at the end I don't have such a mess that I will end up going back to Msoft :-)

Thanks in advance,


Javi

---

### Post by 23meg on 2006-06-16
> I have read somewhere, that it is a good practice to have a partition for your own data, so if you update or re-install at some point you can format the partitions to do a fresh installation but still you have your data. Do people normally use that approach?
Lots of people do, and it's a good practice. Just set up a separate /home partition on install and your user preferences will be kept there even if you reformat / delete your other partitions.
> So now I'm running Dapper and lets assume that official release of edgy will be in December. If I keep updating the new patches everyday, does it mean that I will have then Edgy already by when the official release comes? Or when the release happens they will do major updates?Dapper will only get security updates until Edgy arrives. You'll have to do a major update (called a dist-upgrade) when Edgy is out.
> And, what is more convenient and why, to format all and do a fresh installation of Edgy from scratch or just update it from Dapper?
A dist-upgrade is more convenient in most cases but can lead to dysfunctions in some components depending on your configuration and how you modify your installation.

---

### Post by muep on 2006-06-16
Hi.

Many use the separate data partition approach, as it it much easier to do clean installs (which means formatting the root partition). Usually one needs about 5 - 10 Gigabytes of space for the operating system, some for swap and the rest for /home.

Edgy is and will be in its own repository, so people won't have to upgrade if they don't want to. Currently Edgy is under development and some are already using (testing) it. When they install their updates as you described, they will have Edgy when it comes out. Others need to upgrade if they want to, it is not hard and it may become even easier.

Some people have problems with upgrading from one major version to another, so they may decide to do a clean install instead. On the other hand, my friend, who is not a lot into linuxes, upgraded her system on her own.

Even if you don't have a separate /home partition, upgrading is safe and it preserves all your settings, data and stuff.

---

### Post by catlett on 2006-06-16
Make a seperate home partition. Upgrading is not safe. Just search the dapper forum and you willl see all the problems with a dist-upgrade. The safest way and best way to have a solid install is to have a home partition and then do a clean install from a cd. Just so you know, I speak from personal experience [http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903)
When you go to install use gparted live beforehand to make your partitions [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
 Make 3 partitions.

swap       512mb.........( swap is virtual memory. the rule of thumb is twice your ram i.e. 256mb ram = 512mb swap) you won't need more than 512 even if your twice ram number is higher, only if you video edit etc do you need a large swap. format this partition linux-swap

root           5gb.........(5gb is plenty for root if you have a home partition. root holds the install and any applicatioins you install after, to use a windows term it is the Program Files section ) format this partition ext3

home         ?gb.........(home should have the most space. make it whatever space you have left over. to use windows again, home is the My Documents area.) format this partition ext3

When you do the install, the partitioner will give you a list of your partitions. There will be a drop-down menu box next to each partition with choices for their label. Just choose the label accordingly. 512mb partition label "swap". The 5gb partition label "/"  The ?gb partition label "home". Make sure you check off the circle that has the heading "format?" so Ubuntu will format them and add data.

---

### Post by javierfh on 2006-06-16
Hello,

and thanks a lot for all the replies.

So, is it still possible to create a new partition when i have already the system working? At least in windows world it is possible to use Partition magic or similar and do repartitioning. Is there something similar to that in linux?
And if i create a home partition, how can i move or tell that i have a home partition and all the data should go there? is it as easy as to copy the /home directory to that partition? 

And what happens then with all plugins and applications i had installed? they probably go to /bin or some other folder, right? so when i do fresh installation i have to start from scratch, right?

Thanks for all the help.


Javi

---

### Post by Torquemada28 on 2006-06-16
[QUOTE=javierfh]Hello,

I'm novice into Linux and I have few basic questions.[/QUOTE]
I'm also a clueless noob, so all I can provide is discussion, not definitive answers.

[QUOTE=javierfh]I have read somewhere, that it is a good practice to have a partition for your own data, so if you update or re-install at some point you can format the partitions to do a fresh installation but still you have your data. Do people normally use that approach?[/QUOTE]
This is the approach I use with windows because it needs a clean install every 18 months. Ubuntu is bound to be more stable than XP but having your personal data stored on a seperate partition is probably a good idea in any case.
I'm still not comfortable enough with linux to leave the Microsoft software gulag, so I have a dual boot system. I have a single 10Gb partition formatted as FAT32 (vfat) so I can easily access any files I download in Linux, from XP.

[QUOTE=javierfh]Second question it is about what will happened when the new release comes?
So now I'm running Dapper and lets assume that official release of edgy will be in December. If I keep updating the new patches everyday, does it mean that I will have then Edgy already by when the official release comes? Or when the release happens they will do major updates?
And, what is more convenient and why, to format all and do a fresh installation of Edgy from scratch or just update it from Dapper?[/QUOTE]
This is an interesting question.
For me, one of the major selling points of Ubuntu was that the system could be upgraded without the need to reformat and start again. In fact, I got a kernel update today. The updater downloaded it and installed it and that was that. Uninstalled the old kernal using synaptic which removed it's entry from GRUB and went on my merry way. I imagine that upgrading to the next Ubuntu incarnation will be done in a similar manner, hopefully with the same amount of ease.

---

### Post by catlett on 2006-06-16
[QUOTE=javierfh]Hello,

and thanks a lot for all the replies.

So, is it still possible to create a new partition when i have already the system working? At least in windows world it is possible to use Partition magic or similar and do repartitioning. Is there something similar to that in linux?
And if i create a home partition, how can i move or tell that i have a home partition and all the data should go there? is it as easy as to copy the /home directory to that partition? 

And what happens then with all plugins and applications i had installed? they probably go to /bin or some other folder, right? so when i do fresh installation i have to start from scratch, right?

Thanks for all the help.


Javi[/QUOTE]
 When you install you give mount points for your partitions, lkike I explained earlier about the drop down menus. The difference is you DO NOT FORMAT the home partition. This way it is made your home parititon but the data is untouched.
If there are configuration setttings that are outside your home folder, you just make a copy of the plugins, configuratiuon file etc. and reinstall it from that copy after the update.
You can just run the upodate manager to upgrade but it doesn't always work. As far as keeping  your configuration goes.

The regular updates and kernels will be applied without a problem. But regular updates do not give you the next version.

To look at it a littler different. The update manager is just like windows automatic updater. It updates system components and gives patches. Upgrading is like going from Windows 98 to Windows XP. You don't just keep getting updates to 98 and end up with XP. Same thing with doing the upgrade. When you upgrade 98 to XP, XP doesn't save all your configuration files, there is too much changing. Linux does a better job at keeping your configuratiuon but it still has a way to go.

These won't be a concern in 6 months. Once you are comfortable with linux, configuring your system is simple. The command line is far more efficient asnd powerful than you realise.

---

### Post by javierfh on 2006-06-16
Hi, 
torquemada, thats a good point, i didnt realized that you can uninstall the old kernel, because as you said i guess i yesterday got that same kernel update.

As you, i have also dual boot system, with 30 GB for windows (yes, i admit it, basically for games :) ) and then 120Gb for linux. So i guess ill try to create a home partition as people adviced here, but then i was thinking if i should create a FAT32 to share with windows, eventhough dont have much else in windows but games, so probably no point for it :)

Thanks for the comments, very good ones.

Javi

---

### Post by javierfh on 2006-06-16
[QUOTE=catlett]When you install you give mount points for your partitions, lkike I explained earlier about the drop down menus. The difference is you DO NOT FORMAT the home partition. This way it is made your home parititon but the data is untouched.
If there are configuration setttings that are outside your home folder, you just make a copy of the plugins, configuratiuon file etc. and reinstall it from that copy after the update.
You can just run the upodate manager to upgrade but it doesn't always work. As far as keeping  your configuration goes.

The regular updates and kernels will be applied without a problem. But regular updates do not give you the next version.

To look at it a littler different. The update manager is just like windows automatic updater. It updates system components and gives patches. Upgrading is like going from Windows 98 to Windows XP. You don't just keep getting updates to 98 and end up with XP. Same thing with doing the upgrade. When you upgrade 98 to XP, XP doesn't save all your configuration files, there is too much changing. Linux does a better job at keeping your configuratiuon but it still has a way to go.

These won't be a concern in 6 months. Once you are comfortable with linux, configuring your system is simple. The command line is far more efficient asnd powerful than you realise.[/QUOTE]



Hi Catlett,

thanks a lot for the good reply.
The comparation with Windows was good at least for a novice as i am.

And yes i agree that i dont need to worry about Edgy for six months, but well i wanted to set up everything fine from the beginning so then is not that difficult to update. But i will try your instructions to set the home partition.

And about this been more confortable...i want to be optimistic,but seems long  process to get familiar with it, there are so many "open fronts" (im currently fighting with setting up the webcam, configuring wlan card in my laptop where i also installed dapper, setting up a nice work flow to work with pics from my Nikon D70 camera, etc, etc and not to mention GLX that i dont dear yet to mess with :) )

Thanks again,

Javi

---

### Post by Torquemada28 on 2006-06-16
[QUOTE=javierfh]

As you, i have also dual boot system, with 30 GB for windows (yes, i admit it, basically for games :) ) and then 120Gb for linux. So i guess ill try to create a home partition as people adviced here, but then i was thinking if i should create a FAT32 to share with windows, eventhough dont have much else in windows but games, so probably no point for it :)
[/QUOTE]

I still use windoze for games, bittorrent, Photoshop, Illustrator and Dreamweaver 8.
I just don't feel that The GIMP measures up to Photoshop yet and I get shitty download speeds from all the linux bittorrent clients compared to what I get from Bitcomet in windoze. I use my "Exchange" partition to put .torrent files in so I can open them with Bitcomet.
I'm yet to find linux eqivilents as functional as Illustrator and Dreamweaver 8.

*edit*
Add Skype to my list of "need windows for" programs.
The linux port of Skype doesn't work for the 64bit version of Ubuntu.
That sucks big time.

Now that I've been informed that moving to the next Ubuntu version won't be as easy as I thought, can someone recommend a good linux partitioning tool so I can isolate my /home directory? If I copy the contents of my current home directory to the new partition, how do I then get Ubuntu to recognise it as /home?
I only have a very basic knowledge of creating mount points, so explain it like you're talking to a congenital idiot.

---

### Post by fridayxiii on 2006-06-16
[QUOTE=catlett]Make a seperate home partition. Upgrading is not safe. Just search the dapper forum and you willl see all the problems with a dist-upgrade. The safest way and best way to have a solid install is to have a home partition and then do a clean install from a cd. Just so you know, I speak from personal experience [http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903)
When you go to install use gparted live beforehand to make your partitions [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
 Make 3 partitions.

swap       512mb.........( swap is virtual memory. the rule of thumb is twice your ram i.e. 256mb ram = 512mb swap) you won't need more than 512 even if your twice ram number is higher, only if you video edit etc do you need a large swap. format this partition linux-swap

root           5gb.........(5gb is plenty for root if you have a home partition. root holds the install and any applicatioins you install after, to use a windows term it is the Program Files section ) format this partition ext3

home         ?gb.........(home should have the most space. make it whatever space you have left over. to use windows again, home is the My Documents area.) format this partition ext3

When you do the install, the partitioner will give you a list of your partitions. There will be a drop-down menu box next to each partition with choices for their label. Just choose the label accordingly. 512mb partition label "swap". The 5gb partition label "/"  The ?gb partition label "home". Make sure you check off the circle that has the heading "format?" so Ubuntu will format them and add data.[/QUOTE]

I did my initial install of Ubuntu last night in dual boot format.  I have an 80GB HDD, my XP recovery partition is approx. 4gigs, I left 45 for XP, and marked the rest for Ubuntu (including a 512MB swap partition).  From what you said I'd be better off establishing three partitions for Linux, correct?  It'd be pretty easy to redo since I haven't done much aside from d/l & install all the updates.  If I go this route, do I choose ext3 for the file system on the home & root partitions?  

Another question: what's the primary difference between Kubuntu & Ubuntu - is it the Gnome vs. KDE GUI?  Are there any distinct advantages of one distro over the other (or is it just a matter of personal preference)? I think I also read that Kubuntu allows a user to switch between Gnome & KDE is that true?  

Thanx for helping the n00b. ;)

---

### Post by catlett on 2006-06-16
The great thing about linux is you can have many window managers. (that's what gnome and kde are, window managers. In windows you have only one choice Explorer)
If you installed Ubuntu all you need to do is install the Kubuntu desktop to have kde. First I'll show you how to install the different desktops then I'll explain how to choose.

I am using aptitude instead of apt-get because it does a better job of keeping track of everything, so to speak.
All the versions start with the server base. Adding the window manager is what makes them different. So if you have ubuntu you already have the server base plus gnome.
To get kde and thus have kubuntu do 
```
sudo aptitude install kubuntu-desktop
```
To have xubuntu a.k.a. xfce window manager 
```
sudo aptitude install xubuntu-desktop
```
To have edubuntu, the educational version of ubuntu 
```
sudo aptitude install edubuntu-desktop
```

And if you have kubuntu or xubuntu and you want ubuntu
```
sudo aptitude install ubuntu-desktop
```

Now you will have all the version of Ubuntu available to you. 
How do you switch? Good question.
After you start your computer you end up at the login screen. Where you enter your username and password.. In the bottom left hand corner there is "options" on the panel.
Click options and a menu comes up. Choose "select session" That is where you choose which version you want or more precise what window manager you want. The options will be listed as the name of the window manager i.e. Gnome, KDE, XFCE (I don't know about edubuntu because I never installed it).
There will also be a default session. The default will be whatever you installed first. Meaning if you had Ubuntu then the default is gnome. So if you want gnome you just choose the default session.
This leads to a point that needs to be menyioned. (sorry to bore you). When you install another window manager, there will be a prompt asking you if you want to switch the default session. Just select no. Sometines they ask it in terms of the session manager  i.e gnome's is gdm. KDE is kdm. Xfce's isn't confusing at all. I forget it but it is nothing like the other two.
Just keep your default session manager. Now when you choose kde as a session it will again ask you if you want to make this a permanent switch or just "for this session only". Choose "for this session only". Then when you log out or shutdown and restart just choose default sessionb to get back to gnome/ubuntu.
You'll understand as soon as you do it once. It isn't that difficult. The cool thing is you have 3 (I don't know how cool edubuntu is) window managers ready to go. They are all well established and have there advantages over the others.
They can all do the basics of e-mail, cd/dvds, internet etc. Once you get specific then they differ. Try them. That's what's great about linux, you have total control over your computer and almost limitless options (believe it or not there are even more window managers you can use. kde and gnome are the 2 big ones but there are plenty of other capable managers out there)
Have fun and if you have a problem, post it in the forums. Someone is always willing to help.

---

