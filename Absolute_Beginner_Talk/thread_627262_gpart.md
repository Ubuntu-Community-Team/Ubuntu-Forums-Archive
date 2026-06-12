---
title: "gpart"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by melasaurus on 2007-11-29
i don't know how to use it.  i currently have ubuntu on all 120gigs of my hard drive.  if you could walk me through it.. .. it would be amazing help.

for some reason every time i try to do anything in it.. it shuts down.. bug? 
or maybe i just don't know how to use it. =x

---

### Post by Silvain on 2007-12-16
I am currently looking for Gpart info also, Some advice next. If you have any data on the drive you consider important, you should burn it to a Cd or put it on a flash, before fiddling around any more. :cool:
     When and if I find any good links with how-to infos, I'll post here.

---

### Post by Silvain on 2007-12-16
This looks like a good place to get started,

 [http://gparted.sourceforge.net/faq.php]("http://gparted.sourceforge.net/faq.php")

Hope this helps, 
Silv  :)

---

### Post by High Camp on 2007-12-16
Alrightly,

To me Gparted is pretty hard to explain because, to me, it's so intuitive.

attached is a screen shot. In that screen shot you can see:
/dev/sda1 - / (Root file system)
/dev/sda3 - No nabel (Has my test OS on it so I don't screw up my every day one. If you set a mount point for this when you install you will screw things up)
/dev/sda2 - user_data (Were I store all my music, movies, documents, etc.)
/dev/sda4 - Extended (You can only have 4 primary partitions on a drive and after that you have to have an extended partition to house the rest).
/dev/sda6 - /home (My home folders with all my user data on it. It's worth having this in a separate partition because you can reinstall and still keep MOST of your settings)
/dev/sda5 - swap (My swap partition, which is something Linux uses as a temporary storage bin to speed up the processor)

You can resize partitions with Gparted but it's not accurate or fast so I never do it. If you can figure out how you want the partitions to look before installing and then deal with all this during install. If not use a Livecd to back up all your data and then move thigns around and resize them but I this will take very long. Try just right clicking on different partitions and see the menu you get to get a feel for the functionality. It won't apply any of the changes you make until you click the green check mark.

Hope that helps,

---

### Post by Silvain on 2007-12-17
Thats interesting High Camp , did you make all those partitions with Gparted before your Ubuntu install or after ? I have the Gparted boot Cd actually. I don't have it installed in Ubuntu yet here. I typed Gparted in at the terminal command line and bash was nice enough to tell me how to install it. 
      
      So far I have only tryed to get the Cd to run once and it seemed to come up at the command line, with no GUI type interface. I will have to try booting up with the Gparted Cd
disc again later. At this time I have two partitions on my Hd one for swap and one for the Ubuntu install. It is only a 10 Gbyte or so Hd so there is probably no real need for me to make more partitions, is there?

      Oh btw, I found on this site some pdf docs. 
[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

---

### Post by macogw on 2007-12-17
GParted is in System > Administration on the Ubuntu Live CD.  I always use it to partition the disk before starting my Ubuntu installation.

---

### Post by High Camp on 2007-12-17
Hey

I always install from the Alternate CD (no GUI or desktop, just installs the system without letting you test it) because I find it much faster and safer. There is a text based version of Gparted in there that I use. I find the Livecd mounts the hard drive, which makes it difficult for Gaprted to do it's thing.

That being said I have used Gparted from within the Livecd and it seems to work ok. The worst thing you can do, in my opinion, is partition the disk while trying to install. I find that almost never works.

I would say back up your data and spend a night installing Ubuntu and screwing it up and reinstalling. that's how I learned that I need a test OS to mess around with and all the other stuff.

Let me know if you need any more help,

---

