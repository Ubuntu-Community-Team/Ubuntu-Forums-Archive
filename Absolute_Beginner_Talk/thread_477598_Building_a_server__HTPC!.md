---
title: "Building a server / HTPC!"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by virgil_disgr4ce on 2007-06-18
Hi everyone!  Help me spec out my new Ubuntu server/htpc!  I've been running a server in one form or another for many years, to do network file sharing and ftp, but it's always been some old piece of crap running windows 2000.  But now is the time for something more serious.  I want to build one pc to centrally store ALL of my data as well as host ftp and LAMP for development purposes.  Furthermore, it's going to also serve as my HTPC, hooked up to my huge projector, probably running MythTV.  (Don't worry, its purposes as a server aren't so important that they deserve to be on a completely different machine :) )

So I have a lot of questions regarding its ideal construction for Ubuntu.  Hope you all can provide some new ideas and insight!  And if this post would be better off in a different forum, please let me know or move it :)

Needs / Uses / Questions:

1) Storage: I've got three NTFS disks totalling about 420GB right now in my existing old HP desktop running WinXP (sigh).  But one of my main goals for the new server is mirrored SATA2 RAID.  I'm looking for maximum performance while spending as little as possible (I know, I know).  I'm intending to get 2 500GB SATA2 disks to mirror with an SATA2 RAID controller.  At first I was looking for a new mobo with onboard raid, but after reading around here about raid controllers it seems like it'd be much more reliable to get a PCI RAID controller.  What would be a good choice here?  I saw some hearty endorsements of the 3ward controllers but they're just too expensive.  Is this something I'm going to have to compromise on if I don't want to spend the money?  If you were going to build a server with a lot of space but redundancy in mind, what would you do?

2) Hardware: My existing server runs some kind of 800mhz AMD processor.  It works ok, despite running WinXP, which is a huge drag.  It's really slow, needless to say, over VNC and even for browsing files over the network.  So at first I was expecting to build a completely new system with onboard raid and so on, but if I get a PCI raid controller, I thought, maybe the existing hardware is good enough, especially running Linux (more about OS questions below).  Its uses as an HTPC consist of playing movies and music, not capturing live tv or anything like that.  So I'm inclined to save the money on a new mobo/proc.  However, is there any chance some old amd chipset is going to be supported at all?  I was hoping to use the onboard video and sound, so ... damn.  I'll have to look up the chipset when I get home.  If I need to get a new mobo+proc, do you have any suggestions for cheap, capable, compatible combos?

3) Ubuntu:  I'm unsure which version (desktop or server) to download, is there a comparison page?  Does the server edition just come with lamp but without gnome?  I've read plenty of times that it's easy to install gnome afterwards.  Question:  Say I run the server without gui normally, but I want to be able to press a button on my remote (I'm thinking of getting [this]("http://www.newegg.com/product/product.asp?item=N82E16811235002"), which I hear has good linux support) and instantly go into MythTV (or whatever).  Would this be possible or reasonable?  I'd guess there'd be a way to link a button to a script that would launch gnome and so forth.

That covers my main concerns for now :)  That's a lot of info,  but my main questions are really just about ideal hardware.  Thanks so much for your help and ideas!

--Ted

---

### Post by virgil_disgr4ce on 2007-06-18
Oh, and for those interested: my current hardware lineup is at:

[http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=3811729](http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=3811729)

---

### Post by timong on 2007-11-27
I'm also quite into the creation of a linux based HTPC around mythtv and ubuntu gutsy linux ! Check [http://silentlinux.blogspot.com/](http://silentlinux.blogspot.com/) if interested in the process. 

Cheers!

---

