---
title: "Dreamweaver MX fatal exception closes program"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-07-01
Hello,

I hope it's ok to post this question.  The CrossOver Forums don't get much traffic. I've pulled my site from Frontpage 2003 and migrated it into DW MX, so I've got some hopes I can wean myself off of Frontpage with this site. (FYI, I have successfully used DW in the past but went back to Frontpage for certain reasons. Those reasons of course do not apply to this site here) 

My title says it pretty well. When I try to access my remote site - and I've double-checked the Remote FTP settings with my Hosting Co. - I get a message "Dreamweaver MX has encountered a fatal error and must now close". Then bam, the program closes out.

The thing is, this hasn't always happened. I have had a slight learning curve getting the correct FTP settings, but for the most part, I either connected or got a FTP Error. Now, out of the blue, I get a fatal exception.

Also, I have installed MDAC successfully (which is needed for MX to run) and I have also installed the recommended 6.1 updater for DW MX.  

I'm using Ubuntu Feisty on an HP Pavillion Media PC, 2 GB, AMD Athlon X2 Dual-Core 4600+ Processor, 1.8 gHz.

I appreciate any assistance on this question. Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-01
I want to post an update on this thread because I've discovered several other posts on the CrossOver Dreamweaver MX forum dealing with exactly the same issue. Unfortunately, not only are the posts generally left unsolved, but a couple of the posts are also 1+ years old !!!!

:( My conclusion has been to try installing DW MX in wine and seeing how that goes. Unfortunately, CrossOver won't even let me uninstall DW MX. It gets stuck and I get a red X window saying that there is an installation file missing. 

This all seems pretty buggy so far. I'll try to keep you posted of any significant changes, just in case anyone else out there is interested.

Thanks, Frank B.

---

### Post by expatCM on 2007-07-01
Think you will find that it does work under Wine.

Frank's Corner has some simple comment at this link
[http://www.frankscorner.org/index.php?p=dreamweavermx](http://www.frankscorner.org/index.php?p=dreamweavermx)

But you will find some details on the Wine site
[http://appdb.winehq.org/appview.php?iVersionId=1054](http://appdb.winehq.org/appview.php?iVersionId=1054)
It seems that it runs but it is not 100% perfect and not all versions work so well ....

---

### Post by Brightbelt on 2007-07-03
Thanks Expat,
I could use a tip on how to first Uninstall Dreamweaver MX from CrossOver. For some reason, my system gets stuck and it won't uninstall.

Maybe if I tried doing it by code, it would work, but I don't know what command to run.

Thanks For helping - I appreciate it,

Frank B.

---

### Post by expatCM on 2007-07-04
I do not use CrossOver so I really cannot be sure.  If the uninstaller does not help then what I would do myself is find the Dreamweaver directory and rename it and then look for the entry in Documents and Settings and also rename that.  

After restarting Dreamweaver should be gone.  If there is some unfortunate problem then simple change the directories name back to what it was and then you should be fine.

On the FTP issue, I know that there is a built in function in Dreamweaver but it does not mean that you have to use it .....   if it is giving a problem why not use a stand alone FTP client, there are many of them available and they do work well.

---

### Post by Brightbelt on 2007-07-04
Would a stand alone FTP client be a completely separate program or a plugin to DW?

Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-04
I've installed gFTP via Automatix and will give it a try.

Many Thanks, Frank B.

---

### Post by expatCM on 2007-07-04
No a totally separate program, one which is native to Ubuntu (rather than Windows).  Perhaps you want to try Filezilla but there are lots of choices and they all work ....

Since the data files are independent of Dreamweaver and since you know there is a problem with the inbuilt Dreamweaver utility then why not use a stable external program ....

---

