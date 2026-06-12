---
title: "Access denied error trying rip CDs..."
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Marcus_Chaman on 2005-12-30
Hi all,

I'm new to Ubuntu and am slowly getting it to do all the things I do in windows. 

I'm trying to get Sound Juicer to rip CDs to MP3. I followed the instructions for installing gstreamer and adding  the mp3 profile to Sound Juicer, but when I try to rip a CD, I get an error saying 'Sound Juicer cound not extract this CD. Reason: Access denied'. 

Any ideas?

I am able to play my existing mp3 collection in Rhythmbox with no problems.

thanks.

---

### Post by ATAQ on 2005-12-30
yeah I think if you change the permissions it might work, worth a try.

use: chmod a+wrx /dev/cdrom  

look in dev and see what cd devices you have and then put in where cdrom is.

I hope this helps you.

Ant

---

### Post by fordfan753 on 2005-12-30
You might not be in the CD playing group. This is easy to fix in users and groups without having to resort to command line.

---

### Post by Marcus_Chaman on 2005-12-30
[QUOTE=ATAQ]yeah I think if you change the permissions it might work, worth a try.

use: chmod a+wrx /dev/cdrom  

look in dev and see what cd devices you have and then put in where cdrom is.

I hope this helps you.

Ant[/QUOTE]

Can you expand on that a little?... I'm still finding my way around linux. I can run the command ok, but what should it tell me?

thanks.

---

