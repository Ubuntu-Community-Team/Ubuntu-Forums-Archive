---
title: "SOHO LAN: practical experience"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-04-10
Does anyone have practical experience setting up and running an XP/Linux small LAN?

This is my scenario...
1. I use a variety of softwares title for the work I do (OpenOffice, MS Office, Acrobat Pro, Macromedia (pre-Adobe), Photoshop.

2. My wife surfs, Skypes, plays onboard games (solitaire, etc.), e-mails, looks at pics.

3. Two Teenagers: Two big BF2 fans, Youtube, facebook, MSN, listening to music, watching video.

Two PCs (gaming PC and an older kitchen laptop are XP boxes, I have am Ubuntu 6.10 box for e-mail and basic writing function (OpenOffice). I also have been playing with an old P266 box (6.06 server, command line) to store images and music.  I will be building a new box for my work (likely be an XP type...just can't seem to find something comparable to Dreamweaver/Fireworks in Linux). My one teeneage wants to set up another older laptop for farting around on the internet. So, I have boxes now and this will increase to 6 soon.

The one thing I would like to do is easily share files.  The big ones are music, images, and home files.  Of course, Windows XP is a real breeze for this. However, I have been trying avoid Windows.  I have tried setting up a file server of sorts on the p266 and amazingly, I have had it servings MP3 simultaneously to the other boxes until it just stops working after about 5-10 minutes (this also happens when I'm transferring many or big files to it.  An out of sync errors appears.  I haven't yet figured out a cure for it.)

I would also like to be able to connect to my network remotely.

I have been using and learning SAMBA...I've had some issues but I think its because I'm still learning. It certainly is messier to use than straight window Network Neighborhood but then again, it is more flexible.  But I'm not at all sure about which OS/network setup is most secure (firewall/antivirus).

My apologies for rambling...to the question I think I'm trying to ask...is there an easier way to set-up a home LAN for file sharing in a mixed XP/Linux/remote environment?  Or is it easier just to stay with Microsoft?

---

### Post by devnulljp on 2007-04-10
Set up the linux box as a fileserver over samba, then mount that share on the windows machines as you would any windows share.

---

### Post by Ian-on-the-Trent on 2007-04-10
When you say mount, is that mapping the drive as well (from the Windows boxes)?  I have imperfectly setup SAMBA and can access files on the lInux boxes from the Windows ones.  With regard to security, accessing file remotely, and administering the server remotely, is SAMBA the best way to go?

---

