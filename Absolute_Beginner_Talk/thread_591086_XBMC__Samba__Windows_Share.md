---
title: "XBMC / Samba / Windows Share"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by jdb1981 on 2007-10-25
Pretty easy question here, I just can't seem to find a consensus as to what my smb.config file should look like. I have a folder on the desktop called "shared" that will contain everything I want to share with Samba. I've already set it up, set a password, etc, I just need to get a simple template for the config file that has everything I want, and all the threads I read and files I tried don't seem to work. 

Here's what I want:
[LIST]
[*]Share folder to windows (no password needed)
[*]Share to XBMC Xbox (also no pwd) - The Xbox has a static IP, it's 192.168.1.22
[*]Possibly a list of allowed IPs, but not really necessary.
[*]The ability to add an internal HD to the share at some point (again, not needed, but a commented-out template would be great.)
[*]If I'd be able to store my itunes library on the secondary HD, and set up itunes to access it normally, that would be a plus. Again, not really needed at this point. 
[/LIST]
That's it. Just a really easy share, but it seems like the only ones I can find that work with Xbox Media Center are specialized to that person's system. I don't really need it to be secure, or have a million bells and whistles, I just need it to work.

I'm running Ubuntu Server 7.10 with Xubuntu Desktop. This is a headless server that is wired to a DD-WRT router (so I can make any adjustments to the router no problem,) and the other computers/xbox will connect wirelessly, for the most part. The idea is to be able to stream video to the Xbox, and eventually add a 500g HD to the server for backup and storage, and Samba will just share that whole volume. (I can format it whatever way will be easiest, since it doesn't yet exist, but definitely not NTFS, which is all I seem to find info about.)

Anyhow, I hope someone can help, or at least point me in the direction of some good ideas. Someone should have a list of Samba config templates that are kind of modular, that you could just stick together what features/ functions you want, or one big one that would fill most people's needs that you could just comment out the parts you don't need. If I find a solution, I'll at least post what I end up with, so people searching for XBMC, etc. can find it... 

Thanks in advance, and if anyone needs me to post any other info, just let me know.

---

### Post by johnny9794 on 2007-10-27
diddo

---

### Post by jdb1981 on 2008-01-05
Bumping this after many months of no answer- My system has changed a bit, now running Ubuntu Desktop 7.10 with Gnome, not XFCE. Got a new computer, still having the same issue. 

I just need to know what to put in smb.conf to share...

Anyone out there?

---

### Post by rkd on 2008-01-05
Sorry that no one has responded to your question. The folks here are usually pretty quick to help. Let me give it a try.

Let me warn you at the start that I don't know much about Samba. I'm trying to learn about it now.

This thread seems to give some pretty simple directions for setting up thing so you don't have to give passwords when you access the shared files:

[http://ubuntuforums.org/showthread.php?t=658056](http://ubuntuforums.org/showthread.php?t=658056)

It doesn't seem to say anything about setting the netbios name and the workgroup name (both in the [globals] section of smb.conf), so don't forget to do that.

If you want a description that covers more things, this thread has one:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

It is aimed at setting up things so that the userid/password for each user must be set up on the samba system so they match the users on the Windows systems that are going to access files on the server.  That is more secure, but a bit more work. Perhaps you could ignore that part, but benefit from the more detailed descriptions. One thing I'm not sure about -- it says you can't use WINS if the Samba machine doesn't have a fixed IP address. I'm not sure why that would be so. When you are sharing between two Windows machines, neither has to have a fixed IP address. The writer might be wrong on that point, or it might be a limitation of Samba that Windows doesn't have.

The Samba projects official guide is here:

[http://www.samba.org/samba/docs/using_samba/toc.html](http://www.samba.org/samba/docs/using_samba/toc.html)

but it is quite long and seems rather complicated, so it might not be very helpful.

The first link might be all you need to get things going, though some clues from the second link might be necessary. If you don't get it going after looking at those, ask some more questions and I'll see whether I can figure out what you need. It will probably help me learn about it, too.

---

### Post by jdb1981 on 2008-01-05
Thanks for the reply, unfortunatley I did something stupid to my XBOX, and now it's not connecting to my network anymore. I know how to fix it, but it's going to involve moving a lot of crap around, and I won't be able to try anything until I do.

I'll repost once I get things sorted. Thanks again!

---

