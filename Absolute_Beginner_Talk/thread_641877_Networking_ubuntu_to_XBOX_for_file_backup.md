---
title: "Networking ubuntu to XBOX for file backup"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by TurboGoKart on 2007-12-15
Hi, I'm new.  Well, to *this* forum anyways. :)  I searched here looking for ways to network my computer so I can backup my files to my modded first gen XBOX running XBMC as a dash.

After searching I saw that you can use samba to network the XBOX somehow.  However, here is my situation:

Computer went down from a virus.  I tried to re-install XP w/o formatting the HD because I have a lot of music and other files that I want to try and keep before I re-format.  However, now when I try to boot XP, it says I need to register the version of XP, but then it freezes.  Can't boot in safe mode because you can't register XP in safe mode.  So I'm running ubuntu via the DVD/CD drive. 

My thought is that I can't download new programs (samba), because I can't store them on the ubuntu disc, or can I?  Or is samba already in ubuntu, and I just can't find it?


I don't care about running files from the xbox, I just want to temporarily back up some files from my computer's HD so that I can re-format my HD.  The XBOX has a 250gig hard drive with about 140gigs left.   Any takers?

---

### Post by antharr on 2007-12-16
I must say before I say anything that I always created another partition to store files when I use to run Windoze. That way if I had to reformat, I would not lose my data. 
With that being said I think you should still be able to ftp files over to the Xbox using a Ubuntu LiveCD. You should not need Samba to do a basic ftp transfer.

---

### Post by TurboGoKart on 2007-12-16
I didn't see that under Applications.  Is that LiveCD somewhere else?  Or do I have to create that?  I'm sorry, I've just never used ubuntu before.  :(

---

### Post by TurboGoKart on 2007-12-16
Bump!


Just trying to figure out how to back up my HD before I re-format it.  


I have an external HD, but it requires copying some files to the computer so that it will recognize it I guess.  It doesnt work quite like a flash drive does.  Can I use that?  Or would it be better to get the XBOX networked with Ubuntu?

---

### Post by mongose7en on 2007-12-17
Hey there this is another noob, just thought I would post this in case it might help cause it sounds like you're semi-desperate. I'm pretty sure Ubuntu comes stocked with some neat tools like ftp, etc built into the command line. I don't know anything about the XBox, but you may want to look into (type "man ftp" into the terminal) to see about transferring files that way.

On another note, do you like the software you're running on the XBox? I would really like to get my hands on an XBox and use it primarily as a media center.

---

### Post by TurboGoKart on 2007-12-17
Yeah, I saw those.  I must be doing something wrong though with trying to FTP to the XBOX.

I get this message when I think I'm doing it right:    

**The folder contents could not be displayed.**
Sorry, couldn't display all the contents of "Windows Network: 192.168.1.102".


Not sure if I'm doing something wrong or what the dealio is.  I'll have to search some more.




Yeah, I really like the program I'm running the XBOX with.  I modded it myself, and I'm running a 250gig hard drive.  :)  Plenty of room for really whatever I want.

---

### Post by mongose7en on 2007-12-17
Sorry I couldn't go through all this material (have to get out Christmas shopping) but XBMC has a whole area (apparently) for FTP in their forums
[http://www.xboxmediacenter.com/forum/showthread.php?t=22758](http://www.xboxmediacenter.com/forum/showthread.php?t=22758)
If you haven't checked that out already maybe give that a try

---

### Post by jba6511 on 2007-12-17
check the network settings in the live cd and make sure that you are on the same subnet as the xbox. Also, like everyone says you can ftp your files to the xbox, I beleive the user and password are just xbox (at least on my softmod ones they are). If you have an external drive, you can mount that in ubuntu and just copy the data that way as well. To get ubuntu to recognize my windows machines I had to add them to the hosts file, so this may need to be done as well. 

Side note: XBMC is the ****. I use it in conjuction with mythtv as a frontend as well as for streaming all my media files to tv's in the house. Easy mod to do to the xbox if you softmod it.

---

### Post by anjilslaire on 2007-12-17
Yup,
I've had my xbox softmodded for about 4 years; used to be heavily into th 'scene. Its a great media system
Anyway, samba is for th PC side, to stream media to the xbox. If you want to drop files onto the xbox (it DOES indeed make a handy backup server) you'll want to use FTP from ubuntu to the xbox as others have mentioned.
I recommend gftp for a nice gui (even tho I use kubuntu), username/pass is xbox/xbox.
In some cases I've seen xbox/Xbox, but its easily changed from the network settings in XBMC

---

### Post by TurboGoKart on 2007-12-17
The search button wins again!

I found this link:
[http://ubuntuforums.org/showthread.php?t=218630&highlight=ubuntu+FTP](http://ubuntuforums.org/showthread.php?t=218630&highlight=ubuntu+FTP)


I followed that, and got the FTP working.  I backed up all my files to my XBOX.  Woot woot!  Thanks for the help!  Much appreciated. 


Yeah, I love my modded XBOX.  I'm running a Xenium chip, with a 250gig hard drive.  I just recently got XBMC working as my dash, before that I had EvoX.  XBMC is waaaay cooler.  I still haven't hardly played around with anything on there, and it already blows the socks off of EvoX, lol.

---

