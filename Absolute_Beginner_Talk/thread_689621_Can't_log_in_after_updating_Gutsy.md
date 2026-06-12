---
title: "Can't log in after updating Gutsy"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Scoobie_snack on 2008-02-06
Hey guys and girls,

I just updated Gutsy today (The red star in the toolbar thing) and when I logged back in, I lost my sound. 
This has happened before and I have a driver for my soundcard that worked last time.
 I installed the sound driver like before and everything seemed to be ok. I rebooted the system and now I have this odd thing happening..

I type in my username and password and less than 2 seconds later I get told that my "session has lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem" (~/.xsession-errors file)

I have tried to change the session but nothing will let me log in. The only thing that works in the Failsafe Terminal. 
I have no idear how Linux works so if someone  out there has any idea how I can undo the install from the terminal or how I can log in and back up my stuff, I will be forever grateful.

Thanks in advance,

Scoobie
:popcorn:

---

### Post by taurus on 2008-02-06
First thing I would check is to make sure you didn't fill up your disk.  What happens when you run this command from a prompt?

```
df -h
```

---

### Post by Scoobie_snack on 2008-02-06
Hey, thanks for the super fast reply!

I ran the command and I get a list of things.

FILESYSTEM      SIZE       USED    AVAIL       USED         Mounted On
/dev/sda1         227GB     62G       154G        29%         /
varrun               474M      248K     474M       1%            /var/run
varlock              474M      0           474M       0%            /var/lock
procbususb       474M      84K       474M       1%            /proc/bus/usb
udev                 474M      84K       474M       1%            /dev
devshm             474M      0           474M       0%           /dev/shm
lrm                     474M      34M      440M       8%           /lib/mdules/2.6.22-                                                                                     14-generic/volatile

That took some typing :P
I hope that helps

---

### Post by InsaneHL on 2008-02-06
Loginto the failsafe Terminal and delete the driver that you just installed. Im prettry sure thats whats causing it, if thats not it then theres something else that happened, and you'll just have to reinstall the sriver if it was something else.

---

### Post by Scoobie_snack on 2008-02-06
Hey,

Sorry to sound like a noob (I am a noob) but how do I do that?

And also, what does that stuff mean that I typed out in my last post?

---

### Post by Scoobie_snack on 2008-02-06
Just wondering something..

I remember in Windows that I could re-install over the top of an old install, keep all my files etc but replace all the sys files. Is there a way to do that in Gutsy?
Worst case is, if I can't get it working again, I'll have to just re-install. Would it be possible to get my files back from the old install, like the windows.old file that you get?

---

### Post by Scoobie_snack on 2008-02-07
Okay, I took the step of just reinstalling over the top. 
There wasn't much on there that I didn't back up to another comp and I can't find any info on the net that helps. 
Its probably something simple but I'm not clued up on linux yet lol
Lesson learned I guess :)
Anyway, thanks for the replies guys.

Scoobie 

:guitar:

---

