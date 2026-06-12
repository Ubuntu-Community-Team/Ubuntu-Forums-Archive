---
title: "Id10t's guide to ATI AIW and GATOS for 6.10"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by richpor_1 on 2006-12-21
Hello all.

First off, don't give up, I was about to toss ubuntu into the shredder, but with the information in thses forums, I've got it up and running and am very happy.

Now I'm trying to get my ATI AIW X600 TV to work and I understand that I need to get the GATOS "ati.2" and "Xawtv" files to watch as mythtv does not like ATI cards!

As I'm an XP convert, I'm looking for the easy way to get this done and wonder if anyone has found the "ATI TV for Dummies" guide.

If you know the steps to install GATOS, or can point me to to the simplest instructions, I would be forever greatfull.

Thanks,

Richard in Toronto.

---

### Post by richpor_1 on 2006-12-22
*bump*

O.K. anyone out there got this working properly.

I've done a lot of reading and I would like someone to confirm that the GATOS package is or is not already integrated into the 6.10 xorg file...  

In my reading, I've found out that TVtime will not work and downloaded Xawtv, but when I launch the app, it's fail as well.  (it won't launch from the Gnome and when I launch it from the terminal, it tells me that it can't discover the device).

Can anyone help me find out haw to make my AIW work with 6.10- I'd really like to make this work! 

Anyone have any ideas or can you point me in the right direction?

I'm not asking to be spoon-fed, just some guidance would be appreciated!


Thanks,

---

### Post by superm1 on 2006-12-26
> **richpor_1 said:**
> *bump*

O.K. anyone out there got this working properly.

I've done a lot of reading and I would like someone to confirm that the GATOS package is or is not already integrated into the 6.10 xorg file...  

In my reading, I've found out that TVtime will not work and downloaded Xawtv, but when I launch the app, it's fail as well.  (it won't launch from the Gnome and when I launch it from the terminal, it tells me that it can't discover the device).

Can anyone help me find out haw to make my AIW work with 6.10- I'd really like to make this work! 

Anyone have any ideas or can you point me in the right direction?

I'm not asking to be spoon-fed, just some guidance would be appreciated!


Thanks,
I experimented a bit with the AIW during 6.06 days, and I did have to patch to enable TV-out support, but I saw messages in /var/log/Xorg.0.log indicating that the tuner was detected.  GATOS should be integrated in the current packages.  Have you checked your /var/log/Xorg.0.log at all?

---

### Post by richpor on 2006-12-27
> **superm1 said:**
> I experimented a bit with the AIW during 6.06 days, and I did have to patch to enable TV-out support, but I saw messages in /var/log/Xorg.0.log indicating that the tuner was detected.  GATOS should be integrated in the current packages.  Have you checked your /var/log/Xorg.0.log at all?

Nope,

Like the post title reads, I needed the idiot's guide  ;-)

I'll check that though...

I have spent days googleing and reading wiki's and posts, everything points to GATOS, but when I do a sudo apt-get gatos, nothing comes up.  I'm looking for the TV IN, not the TV out.  I like to watch battlestar gallactica while I work on my spreadsheets!
Thanks for your reply!!!

---

### Post by randytuggle on 2006-12-27
I don't know anything about GATOS...but I got my ATI card to work by using instructions provided by tseliot in the forums. See if you can find the ATI posts by tseliot. He may even give you a hand by email.

---

### Post by superm1 on 2006-12-27
> **richpor said:**
> Nope,

Like the post title reads, I needed the idiot's guide  ;-)

I'll check that though...

I have spent days googleing and reading wiki's and posts, everything points to GATOS, but when I do a sudo apt-get gatos, nothing comes up.  I'm looking for the TV IN, not the TV out.  I like to watch battlestar gallactica while I work on my spreadsheets!
Thanks for your reply!!!
I wish I still had my AiW card.  I'd be glad to pop it in and see what my logs are gonna show.  If you get this going though, I'll write "the idiots guide to gatos and AIW" :).

Post your /var/log/Xorg.0.log using the open source ati drivers if your not sure how to interpret what its listing there about it.

---

### Post by richpor_1 on 2006-12-28
Well,  

I've spent days on it, I'm going to give up and but a $20.00 el-cheapo tv tuner card and see if that works.  the threads I've read do not come up with any definitive answers about this problem. Even the "new" ATI Linux driver DOES NOT SUPPORT TV IN.  I tried (and tried and tried) to install Avview and FFmpeg, but keep getting stuck at various places (it does not seem to want to compile properly for me.. could be a 64bit problem?).

In any case, I'll post the log tomorrow and perhaps someone can help me decypher it :-? 

Thanks in advance... Now..on to my USR Fax modem!!

---

