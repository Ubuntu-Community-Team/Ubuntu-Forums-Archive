---
title: "gFTP can't handle big folders?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-04-24
When I ftp a big folder with a lot of subfolders and different files (zen-cart folder) from my website's ftp account to my computer with gFTP, gFTP simply closes after a while.

Is it possible that Gftp can't handle this? I thought that that would not be a problem..

---

### Post by alanphil on 2007-04-24
I've used gFTP to move huge amounts of data and have never seen it close before finishing. Are you using the secure sFTP protocol to connect to the remote server? Is the remote server timing out?

---

### Post by saultpastor on 2007-05-01
Having the same problem, I've never used sftp?  

There is no timeout restriction or bandwidth restriction on the account.

gftp just closes, this wouldn't have anything to do with the account.

Smaller subdirectories are ok but if it takes too long then it just closes, no crash report, nothing ???

---

### Post by linux4me on 2007-09-26
I'm having the same problem with gftp v. 2.0.18 in Feisty and haven't been able to find a solution in the forums or a way to troubleshoot it. 

It seems to happen both with a large number of files in a folder and with a large number of folders. No sign of trouble, it's working away counting folders and files prior to the actual transfer and then just closes abruptly. It seems to happen around the 700 folder range or so...

Has anyone found a solution? I really like gftp but this is causing a real problem on larger sites I'm attempting to back up.

---

### Post by linux4me on 2007-09-26
I got a little more information about this problem, though I don't know yet what it means. I started gftp from Terminal and tested it. When it spontaneously closed during the folder/file counting process of a download, it generated this error in Terminal:
> Segmentation fault (core dumped)

---

### Post by linux4me on 2007-09-26
Apparently, it's a confirmed bug in gftp. [Here's the link.]("https://bugs.launchpad.net/ubuntu/+source/gftp/+bug/70555") Now if I can only find a fix...

---

### Post by linux4me on 2007-09-27
I found a solution; however, it isn't what I had hoped. 

I installed Filezilla using Synaptic, and it rocks. I just did a series of massive file transfers that would definitely have caused the crash with gftp, and it handled them perfectly.

---

### Post by Dr Small on 2007-09-27
Same thing happens to me, and gFTP freezes.

---

### Post by skotos on 2008-06-26
> **kramer65 said:**
> When I ftp a big folder with a lot of subfolders and different files (zen-cart folder) from my website's ftp account to my computer with gFTP, gFTP simply closes after a while.

Is it possible that Gftp can't handle this? I thought that that would not be a problem..

Yes, this has been for a few years, by now. I think at least 3 or 4... :(
And this is bad enough cos the gftp interface is the one I like best and - as soon as an update comes in - I do always go and check for gftp...
Don't know, I have never seen it working fine and this is a big problem that should not be underestimated for so long...:shock:
It is incredible, it is a full featured ftp,ssh,sftp client...
I AM SOO SAD ABOUT THIS!

---

### Post by BUDA20 on 2008-06-26
Try FileZilla is very similar and works fine for me.

Regards

---

