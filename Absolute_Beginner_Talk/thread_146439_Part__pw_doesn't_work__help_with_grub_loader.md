---
title: "Part / pw doesn't work / help with grub loader"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-18
So I finally got Ubuntu installed...

One thing worries me you might be able to help with - I had to manually partition as the automatic setting failed at 33% of installing file system.  Each partitioned drive on my PC had a gig or two of free space next to it.  When I partitioned this time, I included a free space portion that was next to the XP partition.  I was hoping that wasn't needed for anything?

Used to be:
Drive 1:  
NTFS part
free space
xandros part
free space
fat32 part
free space
Drive 2:
NTFS part
free space

Now it's:
Drive 1:
NTFS Part
Ubuntu Part
Swap file
Fat32 part
free space
Drive 2:
same as before.

No idea what the free space parts are for....
Anyhow, now I have ubuntu installed but for some reason it doesn't like the username and password I used during the install process and asks me to use a new one which I enter exactly the same as I did in the install.  Now I get to login, and it doesn't work.  Does this mean I need to reinstall Ubuntu?

Last problem...  How do I get the grub loader to default to load XP if no one selects anything?  Sure in a perfect world I can get rid of XP and just use Linux, but until I have Linux as my main use, I want XP to load automatically like it did with the laoder I had from Xandros.

Kersus

---

### Post by chuckyp on 2006-03-18
1) You could always select recovery mode from grub and change your username or password.  Selecting this option will boot you to a root terminal.

2)  There is a line in /boot/grub/menu.1st called default  #  this # is which one you want to boot by default.  Example the first kernel would be 0 second grub entry would be 1 and so forth so if your xp partition is the 6th or so down you would put a 5 for the default option.  (remember we started at 0).

---

### Post by Kersus on 2006-03-18
Okay, how? - I'll expand...

I boot into recovery mode and I get a prompt like this:

root@Myusername-Ubuntu:~#

I do not know what to type in to fix the password situation.

Also, in the grub loader you tell me to edit the line in a file, cool, I can do that if I knew how to find and open the file...  Would I do this by going to a command line from the grub loader itself?  What do I need to type in.

Thanks for your help!

---

### Post by Kersus on 2006-03-18
Can anyone help with the password situation...  I'd at least like to get to an Ubuntu desktop :-k 

I can eventually figure out the grub loader myself if no one wants to help with that, but I'm lost as far as restoring and fixing the username and password....

Also, why is there no password for the root/administrator but I need one for my username?  When I used Xandros I needed a password only for the root and had the choice of a password or not with any usernames on top of that.  Yet here it seems I need no root password, but do for usernames?

---

