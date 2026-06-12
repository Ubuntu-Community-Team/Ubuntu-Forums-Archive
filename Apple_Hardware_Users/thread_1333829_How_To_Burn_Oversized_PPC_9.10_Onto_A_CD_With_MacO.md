---
title: "How To Burn Oversized PPC 9.10 Onto A CD With MacOS"
date: 2009-11-21
forum: Apple Hardware Users
---

### Post by iBookClamshell on 2009-11-21
So I downloaded Xubuntu and crap! It won't fit onto a disc! And I dont have a DVD writer on my iBook Clamshell. I ended up downloading Gentoo and trying that, but after huge amounts of stress from the Gentoo install I gave up. Then I found a good method. Overburning.
Overburning is where you can burn a little more data onto the disc than supported. The Xubuntu 9.10 is too big for discs, so overburning is essential.**DO THIS AT YOUR OWN RISK**! This is what I did (ON MACOS)

Insert empty disc

Open terminal (in MacOS only, not Linux or Windows)

Type in:  cd /Users/username/desktop  (thats where my iso is, be sure to change "username" to your user name)

Then type:  hdiutil burn xubuntu-9.10-alternate-powerpc.iso  (or whatever the name of your iso is)


I used a CD-RW but apparently a CD-R works too. I don't know if the using the "cd /" command is needed, but its what I did anyway.

The disc then overburned and I could install Xubuntu! I got the info from this originally:
[http://chrisduran.eu/it/tips-and-tricks/how-to-overburn-a-cddvd-in-mac-os-x/](http://chrisduran.eu/it/tips-and-tricks/how-to-overburn-a-cddvd-in-mac-os-x/)

---

### Post by Leslie Viljoen on 2009-11-22
Can you access all the files on the overburned CD? Or don't you need to, to install? According to the linked article overburning can do an extra 10%, so I wonder which of the images will work using this technique. If anyone else tries this can you report back on your results? 

Specifically, I'd like to know which images can be written, which can then install and whether you can also access all the files on the CD afterwards. (Is this perhaps dependent on the brand of CDR?)

---

### Post by iBookClamshell on 2009-11-22
Overburning is new to me so I am not entirely sure if it depends on the type of disc, although I imagine it wouldn't make a difference. I was also worried if some of the data wouldn't be read, but it didn't effect the install of Xubuntu so I imagine other variants would be fine. The iBook Clamshell is a pretty old computer and it had no trouble with the disc, luckily.

---

### Post by arquisto on 2009-11-24
Would just like to let others know that oversize burning seems to work on ubuntu-9.10-desktop-powerpc.iso.

---

### Post by skinnie on 2011-01-25
it seems to be working with the 10.10 too :)
thanks for the tip!

---

### Post by brazzmonkey on 2011-03-04
This post is only rants...

I have to revive an old iMac. I chose Xubuntu because I guessed it would be easier for me to setup and for my friends use. But that's a loss of time.

Honestly, this is really bad design to make an iso image larger than standard CD-ROM sizes. I fail to overburn the image and my legacy iMac cannot read DVD.
Don't tell me the devs couldn't squeeze installed package list by another 25-30 Mb.
It took me a while to download the image with my satellite connection (over)burned it, and now all I've got is a wasted CD the iMac can't read.

Fortunately, Archlinux PPC is there... I'll have to wait overnight to get the image (because of satellite quotas), and the iMac won't be fully functional for another few days...

---

### Post by macbookproi7 on 2011-03-04
Has anyone bothered to find out what is actually happening when you 'OVER BURN'. I mean obviously the disc doesn't just magically get more space for more data. So something is being lost to make room. I noticed in Disc Utility there is a 'Resize Image' o.. and I was wondering what that did? IWhen I downlloaded Mandrive Linux, the disc image came up and was called 'Resize me' (it was the Live CD option) I didnt do anything to it and just burnt the iso straight to CD, and it worked....
     	  	 		  
	   	   
     
 	pt      	 	 	[LEFT] 		 		 			Search Forums 		 		 			 				  					 					 					 					 					 	 					
 					 						Show Threads 						  						Show Posts 					
 				 			 		 		 		 			[Tag Search]("http://ubuntuforums.org/tags.php") 		 		 		 			[Advanced Search]("http://ubuntuforums.org/search.php") 		 [Get All New Posts]("http://ubuntuforums.org/search.php?do=getnew&exclude=121") [Last 15 Minutes]("http://ubuntuforums.org/search.php?do=getdaily&minutes=15&exclude=121") [Last 30 Minutes]("http://ubuntuforums.org/search.php?do=getdaily&minutes=30&exclude=121") [Last Hour]("http://ubuntuforums.org/search.php?do=getdaily&hours=1&exclude=121") [2 Hours]("http://ubuntuforums.org/search.php?do=getdaily&hours=2&exclude=121") [4 Hours]("http://ubuntuforums.org/search.php?do=getdaily&hours=4&exclude=121") [8 Hours]("http://ubuntuforums.org/search.php?do=getdaily&hours=8&exclude=121") [12 Hours]("http://ubuntuforums.org/search.php?do=getdaily&hours=12&exclude=121") [1 Day]("http://ubuntuforums.org/search.php?do=getdaily&days=1&exclude=121") [2 Days]("http://ubuntuforums.org/search.php?do=getdaily&days=2&exclude=121") [Find All Your Threads]("http://ubuntuforums.org/search.php?do=process&showposts=0&starteronly=1&exactname=1&searchuser=macbookproi7") [Find All Your Posts]("http://ubuntuforums.org/search.php?do=finduser&u=1255761") 		 		 	[/LEFT]
 	 	  	 	 	[LEFT] 		  		Quick Links 		[Today's Posts]("http://ubuntuforums.org/search.php?do=getdaily") 		[Mark Forums Read]("http://ubuntuforums.org/forumdisplay.php?do=markread") 		[Open Contacts Popup]("http://ubuntuforums.org/showthread.php?t=1333829#") 		  		Networking 		[Contacts & Friends]("http://ubuntuforums.org/profile.php?do=buddylist") 		 		 			[Pictures & Albums ]("http://ubuntuforums.org/album.php?u=1255761") 		 		  		[User Control Panel]("http://ubuntuforums.org/usercp.php") 		[Edit Signature]("http://ubuntuforums.org/profile.php?do=editsignature") 		 		[Edit Your Details]("http://ubuntuforums.org/profile.php?do=editprofile") 		[Edit Options]("http://ubuntuforums.org/profile.php?do=editoptions") 		  		Miscellaneous 		[Private Messages]("http://ubuntuforums.org/private.php") 		[Subscribed Threads]("http://ubuntuforums.org/subscription.php") 		[Your Profile]("http://ubuntuforums.org/member.php?u=1255761") 		[Who's Online]("http://ubuntuforums.org/online.php") 		  		 	[/LEFT]
 	  	  	    	 		 		 			Go to Page... 		 		 			 			 				 				 			 			 		 		 	
          	 	Ubuntu Forums Help	 	[About Ubuntu Forums]("http://ubuntuforums.org/index.php?page=about") 	[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") 	[Forum FAQ]("http://ubuntuforums.org/announcement.php?f=48")  	 
  	 	Forum Council Information	 	[Who we are]("https://wiki.ubuntu.com/ForumCouncil") 	[Forum Council Agenda]("https://wiki.ubuntu.com/ForumCouncilAgenda") 	[Forum Governance]("https://wiki.ubuntu.com/ForumsGovernance")

---

