---
title: "Problem Adding Users in Dapper"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by popkid on 2006-05-20
Hi, first post, so sorry if this is a stupid question, I have installed dapper drake beta on a laptop I'm running.

I am trying to add a user to the machine by using the users/groups gui in the administration part of the drop down toolbars.

This lets me type in the user and password etc.

Subsequently however, if I try the log out or switch user option from the gdm, I just get a blue screen and a message saying that there is a problem with x.

If I reboot, then the new user info I had entered is no longer there anymore in the add user gui.

I've also noticed that after closing the add user gui, I can't start a terminal window anymore.

Any help appreciated.

---

### Post by Sef on 2006-05-20
> Hi, first post, so sorry if this is a stupid question,

It is not a stupid question, but one that needs answering.  If I find anything, I will post an answer to it.

---

### Post by popkid on 2006-05-20
Thanks, I tried searching the forums but couldn't find any other posts on this specific issue

If you want any further info regarding the machine or installation, just shout, and I'll try and get to it asap.

pK

---

### Post by popkid on 2006-05-20
OK, some new info which may help, it is the action of opening the users and groups gui that is the problem, not adding a user...

Checking dmesg I get the following when the user and groups option is selected:

[4294812.502000] EXT3-fs error (device dm-0): ext3_add_entry: bad entry in directory #278815: rec_len % 4 != 0 - offset=0, inode=1734502764, rec_len=28526, name_len=109
[4294812.502000] Remounting filesystem read-only
[4294812.507000] EXT3-fs error (device dm-0) in start_transaction: Readonly filesystem

I'm guessing this may be the root of my problem?

pK

---

### Post by Sef on 2006-05-21
> [4294812.507000] EXT3-fs error (device dm-0) in start_transaction: Readonly filesystem

It should not be a read only file system.  Should be read-write.  Check out this thread:

[http://ubuntuforums.org/showthread.php?t=178620&highlight=ext3+read-write]("http://ubuntuforums.org/showthread.php?t=178620&highlight=ext3+read-write")

---

### Post by Koech on 2006-05-21
Just use the terminal as root to set new users.
The code:
   sudo adduser <nameofuser>
   eg sudo adduser jack
Hope it works for you.

---

### Post by popkid on 2006-05-21
Hi again, the filesystem is only being remounted as read only when I open the users and groups gui, it is fine before that, the lines I posted from dmesg only appear when the gui is opened.

I can add users via the terminal, I've done that before, but the gui should work shouldn't it, otherwise why have it?

pK

---

### Post by catlett on 2006-05-21
[QUOTE=popkid]Hi again, the filesystem is only being remounted as read only when I open the users and groups gui, it is fine before that, the lines I posted from dmesg only appear when the gui is opened.

I can add users via the terminal, I've done that before, but the gui should work shouldn't it, otherwise why have it?

pK[/QUOTE]
Adding users through the terminal will make a user account like all others (i.e. with a gui) This seems more like a bug in the Dapper version. As you know Dapper is a beta and I wonder if this is a bug that hasn't been noticed before.
 Try the terminal way suggested, hopefully it isn't working read-only and the account will take.

---

### Post by Sef on 2006-05-21
> Originally Posted by popkid
Hi again, the filesystem is only being remounted as read only when I open the users and groups gui, it is fine before that, the lines I posted from dmesg only appear when the gui is opened.

I can add users via the terminal, I've done that before, but the gui should work shouldn't it, otherwise why have it?

pK

It worked fine for me on two different computers.  I would think that Dapper did not get downloaded correctly to your computer.

---

### Post by popkid on 2006-05-21
Ok, thanks, I guess the version of dapper I have and my machine just don't want to play nice for this rather than it being a more general bug.

I have added user now anyway using "adduser"

I would reinstall and see if it helped, but it takes me 3-4 hours to get my linksys wireless card working every time I reinstall! So I'm trying to stick with this install for the moment (at least for a week!)

My girlfriend only has so much patience with me spending my (our!) spare time messing around with operating systems!

Thanks for your help guys.

pK

---

### Post by richbarna on 2006-05-21
[QUOTE=popkid]

My girlfriend only has so much patience with me spending my (our!) spare time messing around with operating systems!


pK[/QUOTE]

LOL, you are not alone there.

---

### Post by popkid on 2006-05-22
As an update to this issue, my whole install went under yesterday after this with unrecoverable errors on the filesystem... after the same error but this time when opening networking gui

I think therefore the problem was probably with my machine rather than ubuntu!

What is worrying is that this is similar to what made the laptop crash before when running kubuntu breezy (this is what precipitated my move to dapper) so I'm concerned that the hard drive may be on the way out.

Anyway, I reinstalled off the live CD this time (wanted to see the pretty installer everyone has been talking about!) and chose ext2 as the file system instead of ext3, this seems to be working better at the moment. Is there any reason why this maybe so?

I've managed to add my girlfriend's user account via the gui with no repeat of the errors so I'm keeping my fingers crossed!

After some fiddling I've even got my linksys wpc54g working with the new native bcm43xx drivers in dapper now, even have wpa encryption workiing under network manager (no more ndiswrapper!) So I really hope it holds up this time... 

Hopefully I'll be around here for a while, thanks again for your help

pK

---

