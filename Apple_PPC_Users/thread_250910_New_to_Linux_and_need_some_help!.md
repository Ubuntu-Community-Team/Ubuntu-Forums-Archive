---
title: "New to Linux and need some help!"
date: 2006-09-04
forum: Apple PPC Users
---

### Post by Patch^ on 2006-09-04
Hi everyone, I'll get straight to the point I'm a complete n00b at linux and I am using a Apple PowerMac G5.

It is my first go at using Linux and I wanted to experiance it and try new things, even though I'm a hardcore Mac user lol!!!!.

I installed ubuntu on a spare 160Gb Drive and it worked fine however there were some complications and I had to erase it etc.

I have created 3 partions using Disk Utility in OS X on the 160Gb drive and I want to install ubuntu on a 35Gb partition.

However when I go to the installation from the LiveCD etc I get to step 5 and try to setup to go on to the 35Gb partition (I just click on it :S). Then I get to the next stage and there is a drop down menu and I have to place the "/" "home" "swap" etc and select a partition. This is the part that is confusing! I have no idea what do do..I select "sdb7" because the size thing says "35Gb". So I select all drop down menus to go to partition "sdb7". However I cannot click on the forward box because it is not highlighted.

My next question is that the fans are constantly on max power while in ubuntu, is there a way to fix this?

Also is there a way to adjust the resolution to fit 1680x1050 via the preferences? (A friend gave me this command: - "sudo dpkg-reconfigure xserver-xorg". This worked (on my first attempt etc) But I want to be able to select resolutions from the preferences, is this possible?

Lastly is there any useful guides on how to install XGL on ubuntu? Because thats one of the reasons I want to try out Linux.

Thanks in advance

(Wow, I wrote a load stuff lol, sorry)

---

### Post by Patch^ on 2006-09-04
*bump* I know it has only been an hour, but I am really eager to start using ubuntu! About 14 people have looked at this thread, do you have any advice? especially on manual partitions! :'(

---

### Post by Patch^ on 2006-09-04
I'm getting really pissed off with the fans now..I had a look at the "fix" from here: - [http://opensource.bureau-cornavin.com/fans/](http://opensource.bureau-cornavin.com/fans/)

I downloaded the kernal updates. Nothing changed :S.. I'm not sure if they even installed per se.

This whole experiance with Linux has left me hating it and wondering why so many people would go through this much trouble. I had high hopes for ubuntu . But I find the linux community makes it hard for new users to join, with not making instructions easy to understand i.e. "qconfig" how do I access that!? I have years of experiance with Windows and Mac OS, so I'm not a computer/tech n00b etc.

I have also had no response from to this thread when there are tons of people online?!

Sorry, But I'm really angry and am considering giving up on Linux all together.

---

### Post by Mimsy on 2006-09-04
I don't know about the Linux community as a whole, but I like the Ubuntu forums a lot. One of the things I like the most is that when I finally get a reply to my post about my problem, it's inevitably from someone who knows what they're talking about and who are willing to spend the time to help me out. :)

Personally, I would rather wait a day extra for a reply that can help me, than see five different relies to my post, that all five say "I have no idea how to help you, but luck finding a solution!".

And of course there are tons of people online. All the people with problems are here looking for answers. Of every ten people looking at your post, at least nine are as ignorant about Ubuntu as you and me are. I browse threads all over the place to try and learn from them, and I'm willing to bet you a lot that the 14 who had looked at your thread earlier did that for the same reason.

Just a thought. :)

/Mimsy

---

### Post by AlphaMack on 2006-09-05
Seriously, chill out.

Either no one has the answer to your specific issues at hand or those that do haven't run across this thread yet.  If you want to ditch Linux because of your experience with these forums and the issues you have right now with it, that is your call.  Do not expect immediate replies.

Sit back, be patient, read the wiki, search the forums, and research.  I have already posted about partitions in the past, but I'll reiterate my suggestion again in this thread:

1.  If you choose to dual boot OS X and Ubuntu you'll certainly need to back up your stuff in OS X as you will need to wipe the drive.

2.  Using Disk Utility on your OS X installation CD, create your desired number of partitions.  In my case I made 3:  one for OS X, one for Ubuntu, and one for my shared data between the two.  Format the OS X partition as HFS+ journaled, the Ubuntu as *free space*, and your shared partition as HFS+ (without journaling).  Install OS X on your first partition as usual.

When you get to Ubuntu, have it *automatically partition the free space* so that you'll have your own boot, /, and swap partitions created for you.  If you choose, you can even further add a /home partition (highly recommended) and this can be better accomplished using the alternate install CD if you're uncomfortable with GParted.

As for the rest, I don't know the answers.

Linux isn't that much trouble at all if you are patient enough and willing to learn.  Case in point I reinstalled Kubuntu and Ubuntu on my PowerBook and had everything back up, customized, and running in a few (..FEW) hours.  And I've only been using Linux since January.

---

### Post by xerman on 2006-10-04
> **Patch^ said:**
> Hi everyone, I'll get straight to the point I'm a complete n00b at linux and I am using a Apple PowerMac G5.

I installed ubuntu on a spare 160Gb Drive and it worked fine however there were some complications and I had to erase it etc.
I have created 3 partions using Disk Utility in OS X on the 160Gb drive and I want to install ubuntu on a 35Gb partition.

Actually, partitioning a Macosx hard drive for use with ubuntu or any other distro takes certain difficulty, as there's a need for a small partition of about 1GB for the "yaboot" boot loader. So there are a couple of options:
1- erase entire disk and let ubuntu autopartition (i've never done this, so I can't tell how it works, but i presume it will do fine)
2- erase entire disk and set a group of partitions yourself:
    2.1 Partition of about 1GB for yaboot in hfs, this will have the startup flag
    2.2 Partition of RAM size, 1+1/2 RAM size, 2 RAM size for swap
    2.3 Partition of your liking for osx in hfs+
    2.4 Partition of about 10 GB or more for Linux root filesystem with mount point "/", in ext3 or reiserfs filesystem format
    2.5 Partition of your liking for your Linux files with moutn point "/home", in the same filesystem format as 2.4

You should take note of the partition numbers for later use, for example:
Let your HD be IDE, and you have just 1 HD, then:
HD is named "hd(0,x)" and "hdax" depending on the place, so for the partitions set before you should have something like:
hd(0,0) - hda1 -> apple bootstrap (about 35 MB) never touch this one
hd(0,1) - hda2 -> yaboot, startup manager (about 1 GB)
hd(0,2) - hda3 -> swap, size you set depending on your installed RAM
hd(0,3) - hda4 -> hfs+ filesystem for OSX (sizeof "yourliking")
hd(0,4) - hda5 -> "/" ext3 or reiserfs filesystem for Linux (10 GB or more)
hd(0,5) - hda6 -> "/home" ext3 or reiserfs filesystem for your linux files (sizeof "yourliking").

If there is no yaboot partition, installation will fail.

> **Patch^ said:**
> 
However when I go to the installation from the LiveCD etc I get to step 5 and try to setup to go on to the 35Gb partition (I just click on it :S). Then I get to the next stage and there is a drop down menu and I have to place the "/" "home" "swap" etc and select a partition. This is the part that is confusing! I have no idea what do do..I select "sdb7" because the size thing says "35Gb". So I select all drop down menus to go to partition "sdb7". However I cannot click on the forward box because it is not highlighted.

If you use the LiveCD you might have problems, as GParted does not support yet the creation of Yaboot partitions with startup mark. You should use the Alternate CD install. Is in text mode, but is still fine.

> **Patch^ said:**
> 
My next question is that the fans are constantly on max power while in ubuntu, is there a way to fix this?

I presume this is due to kernel version. In my iMac G3@400MHz I can't notice as the computer has no fans. In my Powerbook G4, the fans are not working all day. But I'm running edgy on that machine. So I presume it deals with new versions.

> **Patch^ said:**
> 
Also is there a way to adjust the resolution to fit 1680x1050 via the preferences? (A friend gave me this command: - "sudo dpkg-reconfigure xserver-xorg". This worked (on my first attempt etc) But I want to be able to select resolutions from the preferences, is this possible?


Well, I presume that is possible. I would add that resolution to xorg.conf, always after backing up that file:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.base_install"
then
"sudo gedit /etc/X11/xorg.conf"
and add in the section that shows screen size, color depth and so, another with your resolution, and make it default.

To have that be changed through screen preferences in "System -> Preferences -> Screen" I can't tell. Sorry.

> **Patch^ said:**
> 
Lastly is there any useful guides on how to install XGL on ubuntu? Because thats one of the reasons I want to try out Linux.


There are guides all over the forums. First of all you need to know what kind of video card you own, as the process varies from Ati to Nvidia. Do a search for xgl-compiz and your video card (Ati or Nvidia) and follow that instructions.

Hope this helps
Regards

---

