---
title: "Azureus starts and then closes automatically"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by kjaggu on 2007-05-26
Hi All,

I was downloading a file on Azureus. While waiting for it to get completed (as it was nearing completion), i decided to play around with the software. 

I tried creating a self-signed certificate. 

As soon as i filled in my details and pressed enter, it just closed. I thought, Azureus needed a restart. But when i tried opening Azureus again, it loads and then closes automatically. 

As i am downloading a very heavy file and i have a download limit, i do not want to reinstall the software. Please help me asap. 

When i tried loading it through Terminal, i get this error:

> 
Error ID: 43113F32554E54494D45110E4350500308
#
# Problematic Thread: prio=5 tid=0x0805be08 nid=7996 runnable 
#

Heap at VM Abort:
Heap
 def new generation   total 576K, used 499K [0xab8f0000, 0xab990000, 0xabdd0000)
  eden space 512K,  89% used [0xab8f0000, 0xab962e90, 0xab970000)
  from space 64K,  62% used [0xab980000, 0xab98a028, 0xab990000)
  to   space 64K,   0% used [0xab970000, 0xab970000, 0xab980000)
 tenured generation   total 6032K, used 3617K [0xabdd0000, 0xac3b4000, 0xaf8f0000)
   the space 6032K,  59% used [0xabdd0000, 0xac158670, 0xac158800, 0xac3b4000)
 compacting perm gen  total 13568K, used 13564K [0xaf8f0000, 0xb0630000, 0xb38f0000)
   the space 13568K,  99% used [0xaf8f0000, 0xb062f028, 0xb062f200, 0xb0630000)
Aborted (core dumped)


Please help me asap!!! 

Thanks a ton in advance guys and gals....

---

### Post by irish_flu on 2007-05-26
As long as you make yourself a backup of the .torrent file associated with your download and the partially-downloaded file, you should be able to uninstall and reinstall Azureus and then load the torrent back into it.  Make sure you put the torrent and the data in the same place they were before.

---

### Post by kjaggu on 2007-05-26
Thanks buddy!!!

;)

Greatly appreciate the help. 

Even I had thought the same. And, hence I backed up everything and solved the problem by replacing azureus2.jar in /usr/share/java/ with the latest azureus jar file provided by sourceforge.

So, after backing up all the .torrent and partially downloaded files, if any, you can try this method. 

Anyway, after downloading the file from [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php), ensure that you rename the file to Azureus2.jar before copying it to the folder.

It worked for me. Hope it works for you.    :)

---

### Post by lunaticHIGH on 2007-05-26
Question: 

I'm having the same problem. 

So you give this link to replace the jar file - which file is it? many of these are the entire program

Do i DL the whole program again, then replace the file? What's the original name of the file i need? 

Thanks.

---

