---
title: "Using backup partition and other noob questions..."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by godssiren on 2007-05-09
Hello!
Alright, first, just in case it helps, I have a Gateway M320 and 4500 Series Intel Pentium M processor 1.50GHz, 480 MB of RAM currently running Win XP Home (Ver 20002 Serv pack 2).

     I'm very new to the whole Linux thing, though I was first introduced to the idea back in the late 90s. I just sadly never got into it. I've been doing a lot of reading lately about linux, including a pretty decent walk-through I found on another site that used Debian as it's example dist. (as well as leading me here.) I have also been reading all I can on the forums, but can't quite get my head around some things.
     I don't have a long hate list of MS or Mac OS, but I have been a lazy windows user since about 2000. I had some experience with DOS, but I just fell into the OS that was generally provided me... Windows.
     Now that I have more time I'd like to change to Linux, and from what I've seen, Ubuntu sounds like a dist that would really fit. However, I have some questions as I transition.
      My laptop being my only computer, I would like to dual boot with XP until I can get my bearings with Ubuntu. (I have to use this computer for school work unfortunately, and my professors just wouldn't understand my "I couldn't get my printer to work with Ubuntu yet" excuse. Otherwise I'd just sit and fiddle until it worked the way I want it to...) This being said:

1. Can I use the "Recovery Partition" for Ubuntu?  I have had this 4 GB  partition on my computer for 2 yrs now, and I still don't know that it does me any good. I read that it takes about 2 GB to effectively run, but what about any files (docs, music, etc) that I want to use with Ubuntu. Do they need to be on the same HD? Or can they be accessed just as easily if they stay on the Windows HD? 

2. If I use the windows backup functions, or better yet, the one I get through McAfee, is that the kind of backup that is being referred to when they say backup before installing? (i've never had a situation where I had a backup disk that was current when I needed to re-install, i've never done it myself) or do I just need to make copies of the pictures, music, documents that I want to keep? What about preferences on programs like Trillian or Firefox Bookmarks. (I know this might seem silly, but I haven't seen a lot on this, and I don't want to mess it up and not be able to fix it ^_^) Also, will I need to re-install windows to do a dual boot? or only if I mess it up? lol.

3. What is the difference between the ".iso image" and a live CD? And can someone explain a little more explicitly the "burn the iso image" Honestly, I'm not sure what an iso image is... so I'm not sure if I can just click on the "download" button or not to take care of this. (if there's already a post to explain this, just point me to it)

4. Since I'd like to be able to choose which OS I want to use each time I log in... I read about things like GRUB and there was another program I heard mentioned too for a Debian system, though I can't remember the name. But I read somewhere that it has to be on the very first part of the hard drive in order to come up when you boot. I don't really know how to do this though. If there is a string on this I'd be very thankful just to be pointed in it's direction.

Thank you so much, in advance, for any help you can give me. I'd really like to start using Ubuntu so I can begin a transition (hopefully a complete transition in the not too far off future) from Windows. I love the idea of open source programs, and I'm learning more on the topic each day, but I really do learn better when I have something to fiddle with and get first hand experience.

^_^ Happy Posting!

---

### Post by Snowcat on 2007-05-09
I'll try and answer at least some of these questions:

About the recovery partition, I wouldn't know, but often backing up means simply making a CD (or a few) of your important data. Firefox (and maybe Trillian as well, I wouldn't know) allows exporting its bookmarks to a file: "Bookmarks" -> "Organize Bookmarks", then choose "Export" from the File menu.

You don't have to reinstall Windows after setting up a dual boot. Ubuntu, if installed on a different partition than Windows, will create a Grub menu for you, that will allow you to choose which OS to run on startup.

The .iso image file contains the files that will eventually make up the live CD, in a single file. It can be burned properly by choosing to burn a disc image or burn image to disc or something (most burning programs have an option similar to that). If you try to directly burn the file to a CD, you'll probably get a disc with one huge, unusable file, so don't do that.

Oh, and welcome!

---

### Post by hyper_ch on 2007-05-09
Regarding the recovery partition:
Did you get a Windows CD or Recovery CD with your laptop? It seems to me, that this recovery partition will hold some kind of an image of the system the way it was delivered to you. So if you ever need to start from scratch and you very likely will need that partition.

---

### Post by BaffledMollusc on 2007-05-09
> **godssiren said:**
> Hello!
1. Can I use the "Recovery Partition" for Ubuntu?  I have had this 4 GB  partition on my computer for 2 yrs now, and I still don't know that it does me any good. I read that it takes about 2 GB to effectively run, but what about any files (docs, music, etc) that I want to use with Ubuntu. Do they need to be on the same HD? Or can they be accessed just as easily if they stay on the Windows HD? 

I don't know if you can use the recovery partition. You can access files on your Windows partition from within Linux without any problem.

I'm not sure what you mean by the "Windows HD" and "the same HD". I assume you only have one hard drive? Anyway, if you don't want to (or can't) use the recovery partition, the Ubuntu install process will allow you to resize the Windows partition (i.e. make it smaller) and add a new partition on the hard drive in which to install Ubuntu.
> 
2. If I use the windows backup functions, or better yet, the one I get through McAfee, is that the kind of backup that is being referred to when they say backup before installing? (i've never had a situation where I had a backup disk that was current when I needed to re-install, i've never done it myself) or do I just need to make copies of the pictures, music, documents that I want to keep? What about preferences on programs like Trillian or Firefox Bookmarks. (I know this might seem silly, but I haven't seen a lot on this, and I don't want to mess it up and not be able to fix it ^_^) Also, will I need to re-install windows to do a dual boot? or only if I mess it up? lol.

Don't really know about backup solutions. I just burn important files to DVD. Also, as the above poster said, you can export Firefox bookmarks. 

You won't need to reinstall Windows to set up dual boot; you just need to install Ubuntu.
> 
3. What is the difference between the ".iso image" and a live CD? And can someone explain a little more explicitly the "burn the iso image" Honestly, I'm not sure what an iso image is... so I'm not sure if I can just click on the "download" button or not to take care of this. (if there's already a post to explain this, just point me to it)

The above poster explains this pretty well.
> 
4. Since I'd like to be able to choose which OS I want to use each time I log in... I read about things like GRUB and there was another program I heard mentioned too for a Debian system, though I can't remember the name. But I read somewhere that it has to be on the very first part of the hard drive in order to come up when you boot. I don't really know how to do this though. If there is a string on this I'd be very thankful just to be pointed in it's direction.

The Ubuntu install process automatically installs GRUB. This means at boot you'll have a menu where you can choose which OS you want to boot into.
> 
Thank you so much, in advance, for any help you can give me. I'd really like to start using Ubuntu so I can begin a transition (hopefully a complete transition in the not too far off future) from Windows. I love the idea of open source programs, and I'm learning more on the topic each day, but I really do learn better when I have something to fiddle with and get first hand experience.

Welcome to Ubuntu :) Feel free to ask any questions you need!

---

### Post by lefen on 2007-05-09
Regarding the downloading and burning of .iso's you can check out this excellent tutorial:

[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

Edit: BTW, I'd download Ubuntu as a torrent since it'll reduce your chances of getting a corrupted .iso.

---

### Post by rfs1970 on 2007-05-09
hi Godssiren,

Welcome to the Linux World. 

Now, answer your questions:

1) You can perform the Ubuntu installation in one partition and keep all your documents (/home folder) in your windows partition. In the past, to write files in a NTFS partition was quite hard, but in now days it is pretty stable.

2) Backup is always important, imagine that your computer explode when you are installing linux (lol), it will be nice if you could recover all your data, don't you think ? Well, I'm just joking here... but if you could backup the folder "C:\Documents and Settings\<your username>\*.*" you will save pratically every settings and documents that you have and use in your computer.
2a) About your bookmarks... there is a very nice extension that you could install in Firefox to keep all your bookmarks in a virtual area (internet web space)... so... everytime that you need to reinstall your computer, or if you are using another computer you will be able to access all your favorites sites. To check it out, take a look at: [https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410)

3) ISO image is just one big file compressed with the entire CD content (folders/files). So... if you have this file, you just have to use a burn CD program (like Nero for example) to create a CD. LiveCD doesn't have nothing to do with that... you can have a iso image of a LiveCD!  Anyway... a LiveCD, it's a CD that you can insert in your CDROM before you turn on your computer to run and test a new Operating System without make any changes in your computer/hard disk.  So, imagine that you would like to pick a linux distribution, but you are not sure about which one will better fit your needs... So... all you have to do is: pick a LiveCD from a few distributions and test it in your computer before you start the installation process... 

4) You don't have to worry about that, the installation process will set Grub (or Lilo) to be installed correctly in your computer to manage your dual boot.


I hope my english is enough to help you !
:) 

r.

Ps:

If you would like to know more about linux distributions, take a look at this site:
[http://distrowatch.com/](http://distrowatch.com/)

Its possible to run the Windows OS inside Linux. Its much better than a dual boot,
but I believe your computer doesn't have ram memory enough to do that. But if you 
want to know more about it:
[http://www.vmware.com/products/ws/](http://www.vmware.com/products/ws/)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

And finally, if want to find out what program you could use in linux to replace the ones that
you are using in windows, here its a nice reference:
[http://www.linux.ie/newusers/alternatives.php](http://www.linux.ie/newusers/alternatives.php)

---

### Post by godssiren on 2007-05-09
First I'd like to say Thank You! I kinda knew some of this stuff, but I was so unsure and nervous about just doing it. The links really help. I think I should be able to go home and try the live CD tonight or tomorrow. I didn't expect such a fast response, but I'm very happy I did! 
I can hardly wait to try it out, and to learn more about it... ^_^

---

