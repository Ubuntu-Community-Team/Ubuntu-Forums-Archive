---
title: "Measure Twice, Cut Once"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by tonydawn on 2007-07-06
Good Day Everyone,

I'm preparing to jump in completely and want to get some opinions from this friendly group.  I've spent a week or so lurking and searching so I think I know what I want...  Just want to make educated decisions right off the bat so this goes as smooth as possible.

I'm not a complete linux newbie, I'd call myself a linux first or second grader...  I'd say I know enough to know that I don't know alot...  Have tinkered/loaded Red Hat, WhiteBox, Mandrake, and am currently running Fedora Core 5 on a computer which uses Samba give my XP machines a safe place to backup photos, music, and files (I keep it turned off unless backing up).  I tried a complete switch to linux three years ago with Fedora Core, but only had one computer and "needed" XP for games so that fizzled out. 

Well, now the kids are older (12, 10, 6, 3), the Wii is the primary gaming platform, I have three computers running with a laptop on the way, and the XP machines are limping along and ready for the regular delete everything and reload to get it running.  Computer use is 95% browsing, email, simple word/excell documents, photo management (picassa) and music (itunes for my ipod).  I think it is time for a linux centric home network...  I'm going ubuntu this time because I am attracted to the basic core values (free, friendly, and functional).

Hardware wise here is the setup:  In my bedroom I have a DSL connection, a Linksys wired/wireless router, an HP printer/scanner/fax, one handbuilt PIII and 250 mb drive that I plan to run as a basic file server with potential to grow into an email server and web server (family webpage and photos via gallery or the like) (was thinking of running xubuntu on this), and a  3 year old Dell desktop that I was planning to swipe clean and load with ubuntu for my wife and I to use as our main computer.  Downstairs I have another Dell on a wireless connection for the kids that I plan to setup as dual boot (ubuntu/XP), mainly to run ubuntu but to have XP available for the ocassional game or windows need.  This is the computer that I expect to break often due to kids changing settings, windows doing it's thing, etc.  There is also a laptop in my future that I plan to have as dual boot XP/u/ku/bunto and use wireless for me to toy around with.

I'd like to have things setup so that no matter which computer someone logs onto they have seamless access to their files, email, the shared music collection, printer access, etc.  That way, if my wife logs on downstairs to check the mail, things are the same as if she logged on upstairs... And if the kids are doing homework and one comes upstairs, the file they worked on yesterday downstairs is still in the "same" location from their perspective (likely on that basic file server computer).  Then I can just do regular backups from the file server to one of the other computers and all my precious photos/files/music should be safe and in two locations...

Until things are running well and the family is adjusted I plan on using whatever software is "standard" with ubuntu for browsing, email, music, open office, etc to keep things simple.

Here are my direct questions:

Does this make sense or is there a more logical way to do things.  I guess the basic structure is what I have here at work... log onto any computer and my email and files are reconnected...  Where do I start on making that happen... Do I just create identical user profiles on each machine that look to the server for the home directory?  is it that simple?

Not too worried about the ipod... I'm not a fanatic syncher, now that it is loaded with all my CD's I just connect it to charge it.  Any suggestions on a good place to start for music management/playback?

Is there a Picassa2 type photo manager software for linux?  (Yeah I know I could search this but I've already got your attention).

Am I fine with Fiesty Fawn for all of this?

Anyone have a link to a good overall howto to do a good XP/Ubuntu intall on a fresh drive?  All I could find assumed the windows install was already existing (or maybe that is the best way to do it?)

Anyone out there with a similar family situation who has made this jump?  (Wife is simply point and click user, kids are getting more into the weeds, oldest is 12 and is starting to think computers and operating systems are cool, he'll be designing our family webiste before long I bet).  Any roadblocks/successes?

Would be very interested in any general comments or bits of advice that you may want to share.

Thank you very much for any replies.

Tony
Ps107:23-32

---

### Post by lbelloq on 2007-07-06
I'm a n00b so I'll try to answer as much as I can.

- The mobile profiles: I think you'll need 2 things: a directory/authentication service and a file server (for profiles). I know how to do it, but in Windows's Active Directory. Dunno about Linux alternatives.
- Music management/playback: Rhythmbox can fill that place really well. If you need iPod, Rhythmbox can read iPod libraries, dunno about synching; try gtkpod for that.
- Picasa for Linux: [Rejoice, my brother.]("http://picasa.google.com/linux/")
- Feisty Fawn: I think you'll be alright with Feisty. Go for it.

And that's all I can answer.

---

### Post by tonydawn on 2007-07-06
Great news about Picasa... I like it and assume it rocks in linux as well.

I'll try Rhythmbox for music.

Still looking for comments on how to setup the network, or at least someone to tell me what tools to use and what they are called so that I can search for them...

And lastly, when setting up a dual boot machine is it best just to do a fresh XP install, and then use the ubuntu install disk to set up the linux partitions and go from there?

Maybe the length of my post scared you all away... sorry about that, just wanted to give enough background...

---

### Post by lbelloq on 2007-07-06
I didn't answer too much because I was in my job, LOL.
For dual boot:
1. Use XP installation to create a NTFS partition that doesn't fill the disk (leave at least 20 GB unassigned). Install normally after that.
2. Run Ubuntu installation and LOOK CAREFULLY before clicking Next! The wizard is really simple, but in the partitioning step, the default is to DELETE ALL PARTITIONS in the hard disk. Just change it to use the disk's free space (not the exact words) and you'll be OK.

Other useful tips:

- Write down all the hardware of the computers where you want to install Ubuntu. Then Google everything and look if that hardware is supported under Ubuntu. That way you won't have bad surprises. That includes printers, scanners, cameras and webcams, etc.
- Install Ubuntu in one computer (dual-booting) and try all the software recommended. In that way you can see if it really fits your needs. Install alternatives, get used to the Ubuntu way of doing things.
- Backup. Backup. BACKUP. Do not waste tears over the loss of that beautiful photo of your marriage.
- Do it when you have time. There's nothing worse that the frustration of a Linux that doesn't work as you expected and you don't have time to fix it.

I assume your Linksys router works as your network's gateway. In that case, if Ubuntu supports your network card, the system will be automagically connected to the Internet when you run the LiveCD. If not, use another computer to post here/check Google/read a FAQ/etc.

Cheers,
Léster

---

### Post by p_quarles on 2007-07-06
When you said your server has a 250 mb drive, I'm guessing that's a typo? If you didn't mean GB, then you're not going to have anywhere near enough room to run anything on it. (therefore I'm assuming it was a typo). 

The setup sounds very reasonable. Setting up mobile profiles might get a little complicated, but it can be done, and I'm sure that searching the forums or asking in the Networking section will get results with that. Easier would be to simply set up server shares for each user, and then a public share with all common files, but that might be a bit daunting for younger children to handle.  

As for setting up the dual-boot machine, definitely install XP first, defrag the drive twice, and then use the live CD to create a new partition for Ubuntu. For the point-and-click users, you might just want to add desktop icons for the program's they use frequently, and they'll be at home.

Finally, I used Picasa for Linux for about two days before I got rid of it. It's all right, but it's actually just the Windows version installed via Wine. If you need the editing features (which are redundant in Linux; the GIMP is far better), go ahead, but I'm really very happy with the F-Spot photo manager that comes with Feisty Fawn. 

Good luck.

---

### Post by tonydawn on 2007-07-07
Yes, typo... drive is 250 GB.  I remember when 2 MB was cool...

I won't be back home to make all this happen for another week so I've got time to ponder...

I don't need photo editing, just logical photo management including organizing, printing, and emailing, so I'll try F-Spot.

Thanks for the help on the XP install, I'm kinda looking forward to not running very often.  Right now it is very slow despite being proclaimed spyware and virus free by various tools.

I'll do more searching for the mobile profile question and maybe post it in the networking forum. 

Thanks for all your help!

---

