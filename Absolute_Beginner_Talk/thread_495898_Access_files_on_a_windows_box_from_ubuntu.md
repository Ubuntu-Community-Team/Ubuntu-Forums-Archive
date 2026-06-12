---
title: "Access files on a windows box from ubuntu?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-08
Hey!
I've set up and installed samba so that windows can read the files on the home partition of my ubuntu box
Now I need to be able to access the files on my windows box from ubuntu
Does anyone have any ideas how to do this? Is there a how-to or something I can follow?
Thanks!!!!

---

### Post by Dyegov on 2007-07-08
I had Windows in my machine, and installed Ubuntu Feisty to double boot. When I go to Places -> Computer, it shows my window's partition as x.xxGB Volume: disk

All I do is double click it, write my password, and there are my files!!!

---

### Post by Taliskerd on 2007-07-08
Try using [menubar]Places - Network and click your way down to the volumes list.
Not sure if you need a windows Admin account in the logon-as window, but use that if your regular account isn't allowed.
(Also, Domain is not always needed -if so, leave it blank.)

---

### Post by tartarian on 2007-07-08
No dyegov, the files I want to access are on a different computer, not another hard drive partition. 

And frustratingly I've tried that. But none of the password combinations that I can think of work. My user account on windows with their password or the administrator account with that password all link back to the login screen. I've tried leaving it blank aswell. 

Any other Ideas?
All help really is appreciated :)

---

### Post by Taliskerd on 2007-07-08
Sorry, I just assumed this was in place; the win accounts must have 'remote access' rights.

---

### Post by tartarian on 2007-07-08
I'm probably being dumb and stupid....
But how do I do that?
:)
(I'm running windows vista ultimate btw)
Thankyou!!!

---

### Post by robertc36 on 2007-07-08
Silly question but are they set up as shared folders?

---

### Post by tartarian on 2007-07-08
I have two partitions on my windows box. I only really want to share one of them, so I've enabled sharing on that partition. 
And no its not a silly question, because knowing me I would overlook something like that :P

---

### Post by robertc36 on 2007-07-08
The default xp shared folders shoild show up under network if configured correctly so if you are not seeing them .
You may need to set up the network again or check settings also in shared properties there is an option to allow other users to write to these folders

---

### Post by tartarian on 2007-07-08
When I click on network on Ubuntu I see my workgroup and the computer connected to it, I just can't access the computer. It asks me for a username and password yet my win user accounts username and password combinations don't work. Neither does just leaving it blank. Surely the network is configured correctly if I can see the computers???
Also I have granted everyone permissions to read/write and exexute
Thankyou for all your help
Its really appreciated

---

### Post by robertc36 on 2007-07-08
Hi have found this thread about setting up network maybe you could find something in that you may have missed or not tried [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+setup](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+setup)

---

### Post by tartarian on 2007-07-09
haha, I've already followed that thread perfectly and it works really well. But it only allows me to access files on my ubuntu box on my windows box. I need it to be the other way round.

---

### Post by kitty500cat on 2007-07-09
When you go to Places->Network and try to access files on your Windows computer, does it ask you for user name, domain, and password?  If so, enter your Windows user name and password in the appropriate text boxes, and enter the Windows computer name in the domain box.  It might not work correctly if you don't have the domain entered.

---

### Post by Dyegov on 2007-07-09
> **tartarian said:**
> No dyegov, the files I want to access are on a different computer, not another hard drive partition.

Ohh sorry. Misunderstood your question :(

---

### Post by artemen on 2007-11-15
In my case i can get in the winXP folders, however don't have a right to even reath files.
I've shared a bunch of folders on th XP box, even let everybody to modify my files,
installed samba, trying pinging xp 100% data loss. can access ubuntu box from xp side, but not vise versa, please advice what to do:confused:
thanks in advance, everybody!!!!

---

### Post by JKyleOKC on 2007-11-15
> **artemen said:**
> In my case i can get in the winXP folders, however don't have a right to even reath files.
I've shared a bunch of folders on th XP box, even let everybody to modify my files,
installed samba, trying pinging xp 100% data loss. can access ubuntu box from xp side, but not vise versa, please advice what to do:confused:
thanks in advance, everybody!!!!I don't know whether Vista handles LAN security the same way my Win98SE boxes do (probably not but this may give you a hint or two anyway); I had to set up the sharing on each Windows box for the kind of access to allow (read only, or full read-write) and also specify passwords for each mode. This was on a dialog that came up from the "Sharing" choice when right-clicking on "My Computer." The log-in password has no meaning at all for Samba, but in smb.conf you have to enable or disable "encrypted password" ( it should be enabled to work with any version of Windows more recent than Win95). Once you've set the sharing password on the Windows box, the first time you try to connect through Samba you'll be asked for the password. Once you've given it, you should not have to give it again.

You also need to specify, in smb.conf, the sharing mode as "SHARE" rather than "USER" for all of this to work. If you specify the "USER" mode then you have much more configuration to do (and I've never done it, since my own need was for universal access).

Hope this helps some. Getting all the wrinkles smoothed out in a Samba installation can be very frustrating, but once it's done, things "just work" and do so very well!

---

