---
title: "newbie needs help with Mac OS X + ubuntu"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by rayne6 on 2006-07-25
Hi. I am completely new to using Linux. I installed ubuntu 6.06 for the PowerPC on my PowerBook G4 to experiment with it. However, I got in over my head. I have a better than average grasp on using OS X, but I have very little experience using command line based operating systems. Because of this, I have a two part question. I have not been able to access the internet through the wireless network in my house (three other macs currently have working connections to the same network). I have been able to log on using an ethernet connection, leaving my desktop computer unconnected. After doing some google searches, I was still unable to get Wireless Assistant to recognize a wireless network. Since it is a necessity for me to have a wireless connection, I am looking to do one of two things. The first would be able to establish a wireless connection through ubuntu without having to revert to OS X. If anyone would be willing to walk me through the steps of establishing this connection, I would be more than grateful.

The second part of the question is, if I cannot establish a wireless connection through ubuntu, how do I revert my PowerBook back to OS X? I tried booting from the original install disc, which worked fine, but once I got to the section where you choose a drive to install OS X, there were no volumes present. I tried repartitioning the hard drive in an attempt to create a second volume which the OS X installer would recognize, but again, due to my inexperience, I was without luck. Ideally, I would like to be able to dual boot OS X as well as ubuntu, but at this point, I have no problem single booting OS X. I apologize for the lengthy post, but again, I'm in way over my head here. Any help with any of the above problems is very, very appreciated. Thank you in advance.

Steve

---

### Post by chasisaac on 2006-07-26
See this thread to get wireless working

[http://www.ubuntuforums.org/showthread.php?t=142727](http://www.ubuntuforums.org/showthread.php?t=142727)

---

### Post by 3rdalbum on 2006-07-26
Installing OS X after Ubuntu is not recommended, and I don't even think there's a way to resize your ext3 partitions and install OS X in the free space. And if there was, I wouldn't do it.

However, it's easy enough for you to completely repartition, install OS X then Ubuntu. Boot up from your OS X CD, and run the Drive Setup program. Partition the drive so your OS X (HFS+) partition is first. The part of the drive which you want Ubuntu to sit on should be "unallocated" (i.e. no type, unformatted, etc). Now you'll be able to install OS X onto its partition, then install Ubuntu into its free space.

---

### Post by tvwatcherr on 2006-07-31
so you are saying that if install mac OS x *tiger* first, and keep a little extra for Ubuntu as free space, all i have to do is boot up my mac with the "C" key and it will install that easy?  anything i should do before or during installing it i should know about it before i try?  thanks for the help in advance

~Tvwatcherr

---

### Post by KonstantinosX on 2006-07-31
>Hello, I am also interested in Dual booting OSX & Ubuntu.. It seams that a) You'll need to BACK UP EVERYTHING before doing going on, b) Make sure you don't mess with the partition configuration, and c) Do a research of yourself before attempting that Dual Boot... (ppc and ubuntu).
I will be glad to hear news from you.

---

### Post by popper on 2006-07-31
> booting OSX & Ubuntu

always install OSX first and make sure to leave space to make a linux and a swap partition, then install ubuntu or indeed any other PPC linux on the other half.

the other option is to use Gparted a graphical GUI front end to the partitioning app rather like patition magic on the PC.

try and find a working ppc livecd with it on to re-partition your single drive without loosing your current installed OS/data (hopefully).

perhaps a better option is to get yourself a totally new seperate harddrive , install that inside the mac and just install all your linux OS's on that to test.

to be extra carefull, you could just pull your current OSX drive out of the case and replace it with your new blank hd, you dont need any OS (X or otherwise) installed to install from a livecd.

---

### Post by tvwatcherr on 2006-07-31
ok i just installed ubuntu on my ibook g4, and when i told it to install it hung there, and then the screen went black but the mouse is still working on a black screen.  do you recommend that i try to keep my computer on for a little longer to see whta happenes or restart and try again?  its been about 20 minutes right now.  thanks

---

### Post by sjuraud on 2006-08-02
I believe that OS X needs to have (or at least it use to) the installation on at least the first 8GB of a Drive. If you already have a bunch of stuff on a drive (and it's not defragged as well) could cause a problem with installing OS X after any other OSes that have been installed. You might have to back your data up and wipe the drive and start over with OS X being you first intallation.

---

### Post by tvwatcherr on 2006-08-02
i had a free 60 gig harddrive with free space on it, i just partitioned the harddrive to use, and it didnt work.

---

### Post by FierceBob on 2006-08-05
>>I had a free 60 gig harddrive with free space on it, i just partitioned the harddrive to use, and it didnt work.<<

Not sure I know what you were trying to do there.  Were you trying to install OS X on the 60 gig hard drive, or Ubuntu?  Also, when you say "it didn't work", I don't quite get what you mean.  Can you be more specific?  For example, what software did you use to partition the drive?  How did you define the partitions?  Was there a problem during the partitioning process, or did the OS you then tried to install give you an error?

FB

---

### Post by jsonder on 2006-08-05
I'm not sure if this will help or not, but lets give it a shot.

I was interested in keeping OSX when flight 5 for Dapper was released to rave reviews.  So, not having anything of value on the PPC mac mini, I reinstalled the operating system giving it 9 Gig.  I think that I might have just left one big (65 Gig) partition for Ubuntu, or, I might have made swap, root, and home partitions, plus the NewWorld partition, while installing 10.3.9.  For me, I had to upgrade to 10.4.3 **before** installing Ubuntu.  When I skipped the 10.3 --> 10.4 upgrade and did it later, it ate the grub and I couldn't boot Ubuntu!  

The home partition is nice if you're playing OS games; I've installed and removed Edgy Eft knot 1 already -- I now use this mini as my main computer -- without losing any data.

The trick with the Ubuntu install is to create a NewWorld partition when you are **manually** partitioning the remaining (not used by OSX) hard drive space, if you didn't do it earlier. If you aren't using a /home partition you may be able to avoid extended partitions, I couldn't, but then the final result was 7 partitions as shown below.

[IMG]http://members.cox.net/pasaderahoa/nonHOAstuff/partitions.png[/IMG]

I think that OSX in its wisdom is responsible for partitions 1 & 7; part. 2 is 954 megabytes for the NewWorld stuff (that lets or helps you to dualboot);  part. 3 is 9 gigabytes for OSX; part. 4 is the swap partition, 1.4 gig in size (I'm running 512 meg RAM); part. 5 is a 13.8 gig "/" partition; and part. 6 is a 49 gig "/home" partition.

There are days when I wonder why I bothered to keep OSX; probably for streaming graphics...

---

### Post by baldy1324 on 2006-08-05
hi i have my laptop (powerbook g4) running ubuntu perfectly - with minor execptions... (no java, nvidia driver packages dont exist for ppc). but i havent done a dual boot but i just followed the installation compiled a 2.6.17 kernel with kpkg (to create .deb) and then installed it. the 2.6.17 gives native support for the bcm43xx chipset used in the airport extreme card.
hope that helped

---

### Post by MoonWyrd on 2006-08-06
I've made several attempts at getting my PowerBook G4 to dual boot OS X and Dapper.  I've tried installing OS X and Ubuntu first.   Neither seems to see the partitioning set up by the other.  Or the disk will just show up as having no available space

One thing I know I'm not clear on is how to create a NewWorld boot partition under Ubuntu.  I haven't seen this option, where is it?

If it's not too much to as could some kind soul list the tools used and the steps taken to get a dual boot of OS X and Ubuntu set up? I'm not a total novice with either, but I've never setup up dual boot like this.

Thanks.

---

### Post by jsonder on 2006-08-07
Because of that partition 7 0f 128 mb, I am pretty sure that I did all of the partitioning using OSX when I was installing OSX the 2nd time (after my Tiger upgrade fiasco).

You just need a 9xx megabyte partition (I can't remember what the instructions were for the minimum size, 1 gig is safe).  I can't seem to find out how much of that space is actually used.

When installing Ubuntu, you have to select that partition and name it: NewWorld

as part of the partitioning process.

I guess that it is obvious that I kinda did it by trial and many errors...

John

---

