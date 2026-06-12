---
title: "Problems with Live CD"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by KevRus on 2005-09-28
I burned the LiveCD as an image and the boot works perfectly fine until I get an error saying the X Server couldn't be loaded correctly (I think it was X Server, It was something with an X, I'm sorry, I don't exactly remember)
I viewed the log and it said "no symbols found" for /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o" and the same paths but with "a:m_debug_clip.o" and "a:m_debug_norm.o"
and finally, "fatal server error:
no screens found"
It then says something about fixing it and it will restart after that.  But it just goes back to the boot log, so I assume I can type commands in or something to fix it (?)
How can I fix this, and will Ubuntu still work if I install it on my hard drive?
And if I make a partition for Ubuntu, what are the chances that something will go wrong? I realllllly am not in the mood to backup my whole hard drive.  So please don't respond with "It is a very good idea as the risk is always there" because I promise I will not blame anyone here and I am aware of the risk....I just want to know how often people have had problems using the partition tool in the Ubuntu installer.
Thank you for reading, and I hope I don't sound too n00bish. :P

---

### Post by Wolki on 2005-09-28
[QUOTE=KevRus]I viewed the log and it said "no symbols found" for /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o" and the same paths but with "a:m_debug_clip.o" and "a:m_debug_norm.o"
and finally, "fatal server error:
no screens found"
It then says something about fixing it and it will restart after that.  But it just goes back to the boot log, so I assume I can type commands in or something to fix it (?)
How can I fix this, and will Ubuntu still work if I install it on my hard drive?[/quote]

If the LifeCD fails to work, this is not a sign that a hard disk install will not work either.
What Graphics card do you have?

It's also a possibility that your CD is corrupt. Maybe you have to burn it at a lower speed, and check the ISO's MD5 with the one on the ubuntu web page. Did you download Hoary or the Breezy preview?

Or use another liveCD, if that one works it's likely ubuntu will work too.


> And if I make a partition for Ubuntu, what are the chances that something will go wrong? I realllllly am not in the mood to backup my whole hard drive.  So please don't respond with "It is a very good idea as the risk is always there" because I promise I will not blame anyone here and I am aware of the risk....I just want to know how often people have had problems using the partition tool in the Ubuntu installer.

The risk is slim (but there of course :P). I've done some dual-boot installs on various pcs with no partitioning errors ever. Make sure the drive is freshly defragmented before partitioning. If you want to, you can do it with another tool, either another linux or a windows program. Be careful to read the instructions while partitioning closely, a look at the wiki page might be good too.

---

### Post by KevRus on 2005-09-28
My graphics card is an ATI Radeon X800XL.

I burned it at 8x and as an image, the same way I burned Knoppix when I used that a while back, and it worked fine.

And I don't think an MD5 came with my .iso....I just downloaded the .iso of Hoary version on this website.

---

### Post by Wolki on 2005-09-28
[QUOTE=KevRus]My graphics card is an ATI Radeon X800XL.[/quote]

I heard ATI can be a bit problematic, but that's more with regards to hardware acceleration. They should usually work ok. 

> I burned it at 8x and as an image, the same way I burned Knoppix when I used that a while back, and it worked fine.

If everything works in Knoppix, you should usually get it to work on ubuntu. If you're on broadband you can also try the Breezy preview live-cd, it's just 14 days before release.

> And I don't think an MD5 came with my .iso....I just downloaded the .iso of Hoary version on this website.

They're in the MD5SUMs file where you downloaded it. (If you're lazy like me, you'll just start the bittorrent download on it and it'll check for you whether the checksums  match :))

---

### Post by KevRus on 2005-09-28
I'm a little confused, I didn't download the file as a bittorrent file, so no MD5 came with it other than within the .iso, but I don't know how I'm supposed to match them up.  I'll download the torrent and re-burn anyways though. :P

EDIT: The torrent is a direct .iso too.....Exactly how do I check the MD5SUMs? O_o

---

### Post by KevRus on 2005-09-28
Alright I downloaded and burned the Breezy preview live CD and it gave me the same errors....Should I just install the hard drive version?  I've been reading lots of comments on the Live CD being glitchy.

---

### Post by Wolki on 2005-09-29
[QUOTE=KevRus]EDIT: The torrent is a direct .iso too.....Exactly how do I check the MD5SUMs? O_o[/QUOTE]

Torrents are checked automatically, you don't have to do anything special :) The relevant checksums are in the torrent-file to see if downloading worked correctly.

To compare them manually, use one of the programs that generates md5sums, and compare it with the one contained in the MD5SUMS file on the ubuntu web page.

> 
Alright I downloaded and burned the Breezy preview live CD and it gave me the same errors....Should I just install the hard drive version? I've been reading lots of comments on the Live CD being glitchy.


Hm you can try, I know some cases where hard disk installation works and the live-cd doesn't. be careful while partitioning too. I suggest keeping the copy of Knoppix that works on your system around, just in case something goes wrong during the install; often you can fix some errors with that. Otherwise, good luck :)

---

### Post by KevRus on 2005-09-29
I'm afraid to install Ubuntu to my hard drive because I think the exact same error will come up....Is there any way I can fix this problem?  It has something to do with X Server, I've tried running xorgconfig and restarting X Server but it still gives me the same error...Please help!

---

### Post by KevRus on 2005-09-30
Alright I did a hard drive install of Ubuntu and everything went fine when I partitioned my drive, so that's good.

But I get the same problem, I can't load X Server.  I've tried installing all of the "fglrx" drivers but I still can't get to the GUI....I'm unable to find a way to edit the xorg.conf file which may be a reason why I can't fix this....Can anyone pleeeease help me?

---

### Post by xmastree on 2005-09-30
[QUOTE=KevRus]I'm unable to find a way to edit the xorg.conf file[/QUOTE]Assuming you're logged in at a console, you can edit the config file with **vi**
It's not exactly the most user-friendly application though, [**here**]("http://www.chem.brown.edu/instructions/vi.html") is a list of commands.
All you really need to know are a few of those commands.
Open the file with ```
sudo vi /etc/X11/xorg.conf
```
You can scroll through it with the cursor keys, or hjkl. Once you've found the part you wish to edit, press **i** to enter insert mode. Once you've finished, escape to get back (you should hear a beep), then **:wq** to write and quit.
You should see the **:wq** at the bottom left of the screen.

---

### Post by Wolki on 2005-09-30
[QUOTE=xmastree]Assuming you're logged in at a console, you can edit the config file with **vi**[/QUOTE]

Don't let new users use vi ;)

If you're not experienced with it I would suggest nano. "sudo nano /etc/X11/xorg.conf"
Nano displays the most important commands at the bottom of the screen, quite easy. :)

I'm absolutely no expert on ATI cards, but do you get exactly the same errors?

You can also try "sudo dpkg-reconfigure xserver-xorg", it will start the configuration "wizard" :)

---

### Post by xmastree on 2005-09-30
[QUOTE=Wolki]Don't let new users use vi ;)[/QUOTE]Oh, I don't know about that...
First time I ver used it (following instructions in a book) I felt like I'd earned my first belt in geekhood. After all, the **real** experts use nothing else for things like programming, html, etc... :-)

---

### Post by KevRus on 2005-09-30
Okay thank you for the replies, I'll go try out the nano command and edit xorg.conf later when I get back this afternoon.  And I've already tried the x-server-xorg command and had no luck.

---

### Post by Wolki on 2005-09-30
[QUOTE=xmastree]Oh, I don't know about that...
First time I ver used it (following instructions in a book) I felt like I'd earned my first belt in geekhood. After all, the **real** experts use nothing else for things like programming, html, etc... :-)[/QUOTE]

Well, i always used it in the beginning too... following instrucitons in the man page ;) No, it's a good editor for people who are used to it, but the two-mode interface takes time to get used to. Everyone can use nano, even those who don't want a belt in geekhood :)

KevRus, try to look around for ATI threads or even start a new one, your problem should be solvable.

---

