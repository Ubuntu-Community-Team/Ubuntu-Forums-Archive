---
title: "I've lost XP..."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by drewc1138 on 2007-06-02
I just installed Ubuntu on my machine this morning, but I know my wife will want to continue to use XP.  But when I get into the GRUB menu, it only shows the Ubuntu kernels.  How do I get my XP back?

---

### Post by noodle43 on 2007-06-02
lawl

---

### Post by floke on 2007-06-02
Not funny, really.
From a terminal try 'sudo fdisk -l' - if it lists your XP partition (NTFS) then you could rescue it - but if it ain't there then you will have formatted the entire drive.

---

### Post by plcdfa on 2007-06-02
> **drewc1138 said:**
> I just installed Ubuntu on my machine this morning, but I know my wife will want to continue to use XP.  But when I get into the GRUB menu, it only shows the Ubuntu kernels.  How do I get my XP back?
You'll have to modify your /boot/grub/menu.lst file. Please start gparted and post here what is the name of the ntfs partition.based on that I can tell you what to write in that file. I suppose you didn't get your whole drive wiped out by Ubuntu installer...

---

### Post by khardbored on 2007-06-02
First and foremost, congrats! This mishap is a blessing in disguise. Now that I got that out of the way, uhm, looks like the other guys got you set up in the right direction. Gparted will let us know where your XP partition is located and will then allow you to edit grub to get that sucker back in your boot list.

---

### Post by locke.dragon on 2007-06-02
ouch.  bad.  how'd you install ubuntu?  if you hit "use entire drive" or something similar, XP and all your data there is gone and you'll have to re-install.  grow up noodle43.  this is NOT funny.

---

### Post by jacquesvn on 2007-06-02
> **locke.dragon said:**
> ouch.  bad.  how'd you install ubuntu?  if you hit "use entire drive" or something similar, XP and all your data there is gone and you'll have to re-install.  **grow up noodle43**.  this is NOT funny.

Yes noodle Naughty!!! ;)

And I suppose whether its funny or not has to be based on the missus' reaction ... does she have a big frying pan?? :p

Only joking, hope you get it sorted - especially if your couch is uncomfortable :)

---

### Post by mijj on 2007-06-02
judging from the above .. i would say it's not a good idea for anyone who wants a reliable os to use any flavor of  linux.

it's way too cavalier in the way the system updates -  ppl are left floundering after system updates have messed with config files.

Linux  is ok if you regard getting it working and keeping it working as a hobby.  But dont rely on it as a reliable robust system on which to base your work.

---

### Post by khardbored on 2007-06-02
Linux is as reliable as the person using it.

---

### Post by mijj on 2007-06-02
nonsense, khardbored ...

... Ubuntu messes with config files without regard for who the user is. (I assume all flavours of Linux have the same approach to sys updates

Messing round fixing config files after a sys update is not what anyone would consider reasonable activity in a robust reliable system.

---

### Post by weblordpepe on 2007-06-02
OK This thread has gone a bit off topic. Get back to helping this guy with his HDD problem.
(And besides...Linux isn't unstable just because it uses config files & you dont know how to configure it. Its not Windows, mmkay. Its different. Thats not a shortcoming)

---

### Post by candtalan on 2007-06-02
It suggests to me that a good way to obtain Linux is to get a pre-installed unit, if you are not confident about installing a dual boot system with data to loose.

I have found all the flavours of Linux I have used to be utterly reliable, unlike the non linux OS I used before that.

The only real trouble I have ever had with updates were certainly not with Linux! I have edited Linux config files to my heart's content, and have had excellent and fast advice on forums such as this, in Linux, though, not for the non Linux OS.

I install Linux for a few of my very elderly friends - they have a thoroughly reliable system, no problems, -and- I do not get calls for support, because things stay working. Unlike when they had a non linux OS.

---

### Post by weblordpepe on 2007-06-03
Isnt it amazing? You just don't get calls for help. I wish I had a peanut for every time a Windows user has asked me to help them with spyware troubles.  Then I'd have lots of peanuts!

---

### Post by cantormath on 2007-06-03
> **mijj said:**
> judging from the above .. i would say it's not a good idea for anyone who wants a reliable os to use any flavor of  linux..

Then clearly your opinion does not mean......ok I changed it.......but you get what Im saying.  This comment is FUD.

---

### Post by helliewm on 2007-06-03
See my post here with a similar problem. It offers some detailed instructions. 

[http://ubuntuforums.org/showthread.php?t=339101&highlight=lost+xp](http://ubuntuforums.org/showthread.php?t=339101&highlight=lost+xp)

My end result was rather disastrous but  I made a new friend another Ubuntu user who literally lives down the road from me.:D

My Sister and Brother-in-Law nearly killed me!

Some of the suggestions may help you.

Helen

---

### Post by rickycodie on 2007-06-03
i had this problem recently, here's the fix

[http://ubuntuforums.org/showthread.php?t=456819](http://ubuntuforums.org/showthread.php?t=456819)

---

### Post by rickycodie on 2007-06-03
> **cantormath said:**
> Then clearly your opinion does not mean sh@t

this forum is to help people not to insult them.if you want to do that try the social forums.

---

### Post by cantormath on 2007-06-03
> **rickycodie said:**
> this forum is to help people not to insult them.if you want to do that try the social forums.

Not trying to hijack the thread here, just voicing my opinion to this unecessary comment.  This forum is not a place for FUD either........:-).
> **mijj said:**
> judging from the above .. i would say it's not a good idea for anyone who wants a reliable os to use any flavor of linux..
and this is FUD......

---

### Post by rickycodie on 2007-06-03
i agree. drew i hope we helped and have not discouraged you this is not typical behaviour for this forum.

---

