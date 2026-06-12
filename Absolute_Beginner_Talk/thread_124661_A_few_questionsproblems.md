---
title: "A few questions/problems"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by skyace888 on 2006-02-01
I successfully installed Ubuntu 5.10 on my Sony VGN-S260 laptop the other day (dual-boot w/NTFS) and for the most part everything seems fine.  I followed the helpful tutorial at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/).  I have a few issues though:

1.  My wireless card is recognized but I'm not given the option to connect to my wireless network.  I also don't see the option for WAP encryption instead of WEP.  I have a WRT54G router.

2.  When my system boots, I received an error about mounting the local filesystem.  How can I mount my ext3 partition and my FAT32 partition that I have?

3.  My built-in ethernet adapter is working fine online but I can't connect to my Windows share.  Is there a tutorial on this?

Are there any good Linux books that someone can recommend?

Thanks!

--Al

---

### Post by Herman on 2006-02-01
> 1. My wireless card is recognized but I'm not given the option to connect to my wireless network. I also don't see the option for WAP encryption instead of WEP. I have a WRT54G router.Try looking it up in the official Ubuntu Wiki, there is some very good help in there for wireless networking. I don't know enough about it, I haven't even bothered setting my own up yet.>  2. When my system boots, I received an error about mounting the local filesystem. How can I mount my ext3 partition and my FAT32 partition that I have?Try typing the following into a terminal: ```
sudo touch force/fsck
```, and rebooting your computer. It might help or maybe not, but it's worth a try. If not, read [http://users.bigpond.net.au/hermanzone/p10.htm]("http://users.bigpond.net.au/hermanzone/p10.htm") again, I just updated it, you might need to try pressing your refresh button on your browser for the newest version of that page. Thats all I can say about those two questions, I'll need a few minutes to work on the other two if no-one else answers them in the mean-time.

---

### Post by Herman on 2006-02-02
>  3. My built-in ethernet adapter is working fine online but I can't connect to my Windows share. Is there a tutorial on this? Okay, I recently re-installed my wife's Windows XP, and since you asked, I tried and was not able to connect up right away either. 
Normally a Ubuntu computer can easily connect to a Windows one by going 'Places'.'Network Servers', and clicking the icon for the Windows computer we want. It opens, and there we are!
The delay was I had forgotten to run the Windows network wizard for her since I did the re-install, and I had to dig around for a while to find the floppy disk it was on.
Since we both dual boot, it's better to use SHH networking between the two boxes while they are both booted into Ubuntu, so we didn't miss the lack of a Windows network.
I ran that, (network wizard), and it works fine. As long as WIndows networking is set up, you should be able to connect to it from Ubuntu. I didn't even need to do anything to the firewall settings, it looks like they are all opened up automatically now. (Just the home LAN IP address range). Hehe, :-D (Herman)
Oh, PS, as for books, I don't know, I take notes from other people's posts in these forums and/or bookmark them if I think they are pretty good. I also think I't will be a long time before I know everything in our own Wiki, help files (life ring on top bar of our monitor) and all the other wonderful information available on the internet. I used to be a real book worm before I got interested in computers. Now I save my money. :-D (Herman)

---

