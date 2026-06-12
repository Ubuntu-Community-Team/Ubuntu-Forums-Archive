---
title: "Help Please!  Locked Out"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2006-12-23
Someone please help...

Last night I've been working in Ubuntu (6.10) just fine, shut down the computer, went to bed, and this morning I'm locked out.

When I turn on Ubuntu I get to the log in screen, everything looks normal, I enter my username & password, it looks like it's going to log in but a few seconds later it brings me back to my log in screen.  I am absolutely sure I am using the correct username & password (tested using intentionally wrong data & it tells me that I've used wrong login info, as I would expect).

I can log in using my username & password from the terminal so I know that it works, but from the login screen trying to get into gnome I can't get past the login screen.

Bottom line is I am completely stumped.  I am able to enter terminal mode (and am comfortable bashing around), and so would appreciate anyone's help in how to fix the login screen stuff to let me in.

Thanks in advance for anyone's help,
LuckyLucky

---

### Post by taurus on 2006-12-23
Boot into recovery mode from GRUB and paste the output of this command here!

```
df -h
```

---

### Post by luckylucky on 2006-12-23
Thank you Taurus!
As soon as I saw your post I immediately understood what you were getting at, and sure enough my disk was full.  I moved some files from my user's home directory to a backup drive and then no problem logging in.

[COLOR="Red"]**SOLUTION EXPLAINED**[/COLOR]


For the benefit of others reading this post I will explain what happened with a mini tutorial to explain how to solve it yourself...

Symptom = can't log in from login screen
Possible Reason = your hard disk is full
Possible Solution = remove some files from hard drive to free up space

How To:

Boot computer and from GRUB select to enter failsafe terminal mode.  This will give you a command line terminal to type stuff (linux commands)

type:
df -h
This will show you all your hard drives, how much memory is used & free.  Chances are you'll see your main drive where your linux is is 100% full

Change directory to your Desktop directory, type:
cd /home/YOUR-USERNAME/Desktop

List everything on your desktop to see what is there, type:
ls

If you are savvy at using linux commands then move a file(s) to a backup place to free up some space on your hard drive, however I'm not going to explain how to do that.  For you more "basic" here is a simpler solution...

Find a file or a folder containing some stuff you don't mind deleting.  You only need to free up a little space on your hard drive to be able to login, so just find some useless junk to delete then later you can do further backups and cleaning up from the comfort of working in a GUI environment.

To delete a file type:
rm filename

To delete a folder type
rm -rf foldername

BE VERY CAREFUL DELETING STUFF!!!  YOU CAN'T "UNDO" THIS!  Furthermore don't delete anything outside your home directory (/home/YOUR-USERNAME) because it'll likely break your linux.

Now to reboot the computer type:
sudo shutdown -r now

When your computer reboots then log in as normal and you should find everything is working fine.  Since your drive is nearly full now would be a good time to clean up your files, backup files, and delete some junk.

ADDED AS AN EDIT:  I forgot to mention that you should empty your trash bin to complete the deletion process of stuff from your computer.  Right-click on your trash and select "Empty Trash".  Now you will have really freed up space on your computer.

Happy Linuxing!

LuckyLucky

---

### Post by taurus on 2006-12-23
> **luckylucky said:**
> Thank you Taurus!
As soon as I saw your post I immediately understood what you were getting at, and sure enough my disk was full.  I moved some files from my user's home directory to a backup drive and then no problem logging in.


So, you read my mind, eh!!!  :mrgreen:

---

### Post by luckylucky on 2006-12-23
Taurus, you Canadian?  Yeah, I guess I did read your mind.  Thanks BTW for tipping me into the right direction for the solution.  Wow, you sure made a ton of posts, you're definitely a valuable member of this community.  Thank you!

---

### Post by taurus on 2006-12-23
Actually, I am not a Canadian but know a few people who are...  ;)

---

### Post by ivanoats on 2006-12-24
I am having a similar symptom, but my disk is not full, I have 4GB available.

---

### Post by luckylucky on 2006-12-26
Hi, could you elaborate upon the problem?  describe your symptoms?

You also might get some more attention if you start a new thread explaining your problem.  You can refer to this thread, but starting a new one will likely get more people seeing it because if they see a "solution" earlier in the thread they figure you're all set.

Good luck...

---

