---
title: "Mac Ubuntu 4 on a PB G4 800 DVI, need help with Linux LVM HD Access"
date: 2006-06-25
forum: Apple PPC Users
---

### Post by CrossGT6 on 2006-06-25
Ok yes I have an older version of Ubuntu... much older *laugh* I  am trying to DL ver. 6 but with no luck. I am so used to Fedora that this is a big change so far in location and getting used to things. 

Some help is needed but mainly I need to get all my information from my Fedora Linux LVM partition on my 60 gig to this 40 so I can remove the 40 and install the 60 in here with the permant OS install. 

I have no plans of going back to Fedora for now, the fact that an older version of Ubuntu loaded and just worked right away has me wanting to see what the newer version can do. 

Either way I need access to the LVM drive and I need to know the replacement for yum amoung other things. 

Any help is greatly apppriciated. Also if anyone can tell me why I see the normal swap partition just not the rest that would be a help to. (I connected the drive and see only the 1 partition)

Also just some basic starting off help. I also can not seem to get the new ISO for ubuntu to dl for some reason. 

Thanks!

---

### Post by BoneKracker on 2006-06-27
Can't you just move the files from within Fedora (which is already set up to access the LVM)?

Can you provide more detail on the other issues:

a) there are links to download the ISOs on the ubuntu home page.  I've never had a problem.  But there are numerous mirrors you could manually choose from (if you did a little into the download site you'll see them listed), and you can choose from http, ftp, bittorrent, and so on.

b) You can't see anything but the swap area?  On what?  With what?

c) I'm guessing yum is your rpm utility?  If so, we use the Debian system (deb instead of rpm).  Command-line interface is apt or aptitude:
```
man apt-get
man apt
```
As far as the gui goes, there is a very simple gui in the menu ("add/remove" in Dapper) and a more sophisticated application called "Synaptic" that's accessible under the "System > Administration" menu.  You can set up repositories through that gui or by editing a config file (/etc/apt/menu.list).

The new version is much, much slicker than what you're using now.  When you DO get it installed, go to the help menu which points you quickly to some good documentation resources.  You should read some, because Debian is very different than RedHat in some ways, and you can avoid some frustration.

And this is an active community with lots of people willing to help.

---

### Post by CrossGT6 on 2006-06-28
Ok heres some further information. 

I got a friend the burn the ISO of Ubuntu 6 and it worked so I have the live cd running now. 

My external hd encloser has the Hard Drive I was using with my old laptop. That laptop was running Fedora Core 5. It will load the /boot partition but not the other partition with all the information. 
Mac OS X Tiger identifys this partition as Linux LVM. 

I just want to mount the other partition. I also am not sure.. but is it possible to mount the OS X partition and just copy everything directly to that HD? If not I was going to ask how to repartition the external HD without losing any data and then make a new partition thats fat32 because I know I can read that in os x. 

I also am not familure with mounting these other hd partitions so any help there would be great. 

Thanks!!

---

### Post by BoneKracker on 2006-06-28
fdisk and parted are command line tools for working with partitions and filesystems

You can educate yourself from the terminal as follows:
```
man fdisk
man parted
```

Both tools:
  ? = help
  p = print (show) the partition table


Also, check out:
```
man mkfs
```
Yes it's possible to move the data.

Also, I recommend that you use the Alternate Installer CD.  I don't trust the graphical partitioning tools on the LiveCD for anything but very simple installation.  (At least so far -- hopefully they will improve it.).

---

### Post by CrossGT6 on 2006-07-01
Hmm this really sounds like it might be beyond my level. I will try but I am not sure I trust myself with it. 

I tried even using Fedora again and got no where accessing the LVM. I could see that it existsed but nothing I did would mount it. 

I am sure I am just missing how to do it but without some realy help from someone who knows how with me or giving me a detailed guide (I am not saying ur not just that I really don't think I know how lol... I am not really well versed with all the in's and out's of linux yet. Of the commands and programs you mentioned this will be my first time trying them and basically I learn from having someone else there to ask and bounce idea's off of.)

I hope that came out right I basically do ot trust myself at this point. I am still trying as I have to get access to that data but I am not sure i can do it on my own.

I will run the installer and go from there. Maybe I will get lucky and figure out how to access it with just the commands you have shown me and some reading/thinking.... but I still think I am going to be stumped :p

I will let you know where I get stuck next. 

Thanks!

---

### Post by BoneKracker on 2006-07-01
What you might want to try is installing (at least initially) to your 40 GB drive (and to simply things, put in the master drive position on your cable).  Then you can try to add access to the other drive's LVM volumes from within an active Ubuntu install.

Also, if you install using the "alternate install CD", you have more advanced partitioning options that allow you to tell the ubuntu system you are creating about the existing LVM on the other drives and tell it where to mount them.  Then they'd be mounted automatically.  That's probably what I'd do.

Oh, and if you feel you need more help - you might get a quicker additional response by starting a new post.  I would simply make the subject "new install, need help to access existing LVM" or something like that.  You won't hurt my feelings.  : )

---

