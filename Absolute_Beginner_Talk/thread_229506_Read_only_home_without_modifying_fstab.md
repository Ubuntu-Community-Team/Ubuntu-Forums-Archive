---
title: "Read only /home without modifying fstab"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Tortanick on 2006-08-04
I was wandering if there is some way to block users from writing to the /home directory (and by extension the hard drive) without touching fstab, any ideas?

---

### Post by ewl1217 on 2006-08-04
Just out of curiousity, why exactly would you want to do this? This seems like it may cause problems with some programs, considering they all store settings somewhere in the user's home directory.

---

### Post by Tortanick on 2006-08-05
User's will mount a partition on one of several servers as /home, thus ruleing out automount, having /home in Fstab will cause a collison when you try to monut /home. And I don't want users to acidently save their work on the local hard drive.

---

### Post by taurus on 2006-08-05
Then set the permission to /home as read only...

```

sudo chmod 444 /home

```

---

### Post by Tortanick on 2006-08-05
That simple :D thank you :)

---

### Post by Tortanick on 2006-08-06
didn't work :(

I did ```
sudo chmod 444 /home
``` and it blocks me from logging in, fixed that easily but I still need a way to block write access to /home. Any other ideas?

---

### Post by bscbrit on 2006-08-06
"didn't work" - yes it did.  What did you expect it to do?  You were prevented from logging in because it couldn't update your session data i.e. your home directory is read-only.

If you could explain exactly why you feel you need this capability (i.e. what are you trying to achieve?) perhaps someone could tell you an easier way to do it.

---

### Post by Tortanick on 2006-08-06
Want I want is for users to be able to login, then mount a /home partition on a remote server as /home, since there are sevral possible partitions I can't use automount and I was trying to protect forgetfull users from saving stuff locally rather than mounting the remote server.

---

### Post by bscbrit on 2006-08-06
I'm thinking......

---

### Post by bscbrit on 2006-08-06
My first thought -

You need a home directory in order to log in, therefore you cannot log in before selecting a home directory.

If you boot up and then change your home directory, you will have to have some way of moving your current session data to the new 'home' before you can use it.

If you make the home directory quite small, you will effectively stop them from saving too much data to it because it will fill up - but this is guaranteed to upset your users and will probably leave you trying to recover user areas that are full!

[Have you thought of hitting them on the hand each time they save something to the wrong directory? - It used to be a popular technique in schools but I gather it is frowned upon nowadays...]

Back to more thinking.....

---

### Post by bscbrit on 2006-08-06
How about letting them save it to their home directory and then using rsync when they log off to update the data on the remote 'home'.  Why do they need to have a choice of home directory?  What will it achieve that cannot be done by separating data into different directories within the same 'home'?

---

### Post by Tortanick on 2006-08-06
Hitting them over the head sounds effective :)

I could use Rsyinc, just hoped it would be sligtly easier.

---

### Post by bscbrit on 2006-08-06
I'm still not clear why the users musn't have write access to their home directories?  If it is to prevent the user from changing their own desktop settings (which is counter productive - but that is a separate argument) then there are better ways of stopping them.
The whole point of a home directory is that it belongs to the user - (s)he should be able to do anything in that area.  I need my screen set at a different resolution from my wife (poor eyesight), I prefer a different background, my gpg keys are _my_ keys and should not be accessible to anyone else.  These are all things that should remain under my control.  
If you are trying to control data so that different users share the same files then there is a better way of achieving that also.
If you want the computer to adopt a different 'personality' depending on the 'home' drive selected then this can be achieved by using separate hard drives in a drive caddy and plugging in the one that you want. I do this for much of my repair work.  My computer is configured quite differently when I insert the 'repair' drive than when, for example, I insert the 'personal' drive that I am using at present on this forum.  I don't need the repair tools to chat to people, and I don't need 3 separate NICs configured when I am on Ubuntu forums.

---

### Post by Tortanick on 2006-08-06
If a user saves on the local HD rather than the server chances are they'll have trouble finding what computer its on, just wanted to prevent acidents. 

I did figure out how to do it though, if you set the /home/user and /home/user/desktop to read only but leave the rest it works fine.

---

### Post by bscbrit on 2006-08-06
Are you trying to set up a network in a business or at a school perhaps?  In which case it is probably just as easy to educate the users to always read and write from a specific directory (say, 'data' or 'shared').  Tell them that, unless they do so, you cannot guarantee that their data will be backed up.  But, I'm just guessing....

---

### Post by Indras on 2006-08-06
The only way I can think to do it is to set the /home partition in fstab as a smbfs or nfs partition, that way it gets mounted before logging in.  But then again, it won't be user-selectable.

---

### Post by Tortanick on 2006-08-06
Indras, I managed to do it by chmoding the /home/user and /home/user/desktop folder. It dosn't prevent them from giving themselves write permission (I may just chown/chgrp if a test shows that works) but a chmod alone gives them enough of a reminder that they forgot to mount the remote partition

bscbrit, you guessed right but I'd think its better if you see if there is a quick and easy safe guard rather than hopeing someone important dosn't lose files then assume my job was to protect him from ID10T errors.

---

