---
title: "Error messages ........................."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by baekeland on 2007-04-23
..............................Synaptic Package Manager gives me the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Under applications >add >remove I receive the following error message:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

Could someone please help before I lose my mind ............................:KS

---

### Post by tbroderick on 2007-04-23
Try opening a terminal and typing;
```
sudo dpkg --configure -a
```

---

### Post by baekeland on 2007-04-23
Thanks for the command this is what I got back from the terminal:

 Configuring virtualbox &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474;                                                                          &#9474;  
  &#9474; Compilation of the kernel module FAILED!                                 &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; VirtualBox will not start until this problem is fixed. Please consult    &#9474;  
  &#9474; /var/log/vbox-install.log to find out why the kernel module does not     &#9474;  
  &#9474; compile. Most probably the kernel sources were not found. Install them   &#9474;  
  &#9474; and execute                                                              &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;   /etc/init.d/vboxdrv setup                                              &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; as root.                                                                 &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>

---

### Post by baekeland on 2007-04-23
I tried -su:  etc/init.d/vboxdrv and received the following

No such file or directory

Thanks,

Bill

---

### Post by igknighted on 2007-04-23
> **baekeland said:**
> I tried -su:  etc/init.d/vboxdrv and received the following

No such file or directory

Thanks,

Bill

It needs the kernel source.  Install the source file for your current kernel from synaptic.  You might be able to get away with installing the headers file, but I would go with the kernel source just to be safe.  Then run it again.

Also, do check that log file it listed for the reason why... you might not have compilers installed (if not, install build-essential as well).

EDIT: Read the entire error message carefully.  Both times here it told you what to do to remedy the issues, and this in not uncommon in linux.  Unlike in windows where you get some cryptic message that means nothing, reading the error message carefully often tells you what is wrong.  Not scolding for not catching that, but just a heads up to save you some time later.

---

### Post by baekeland on 2007-04-23
Thanks ...................but I can't open Synaptic it gives the following error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by baekeland on 2007-04-23
I don't mind the "scolding"  When it tells me to MANUALLY run the command error I just got I did so in the terminal (which is the only place I would know where to run a command and I am told NO SUCH COMMAND. Is there another place I should be running a manual command?

Bill

---

### Post by igknighted on 2007-04-23
> **baekeland said:**
> Thanks ...................but I can't open Synaptic it gives the following error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

You need to clear out the broken package before apt/synaptic will work again.  Try "sudo apt-get remove <broken_package>" .  Then "sudo apt-get -f install" to finish anything else needing configuring.  Then update/install the source and build-essential.

This is step is more knowledge of apt than anything else.  If you ever get stuck "man apt" is your friend.

---

### Post by pebo on 2007-04-23
...and you may have to use sudo with dpkg```
sudo dpkg --configure -a
```
hth

---

### Post by baekeland on 2007-04-23
man apt is a great resource.  Man anything is a great resource.  But I will have to go deeper into Man to resolve my problem. And, all I want are the Emerald Themes!  Imaging the average Joe having to go through this he'd beat a path back to WinBlows so quick it would be scary.

Funny thing is O/S 2 Warp was almost exactly the same -- a brilliant Operating System!  Why did it fail?  For the same reason this will fail.  It is far too difficult for the majority of Winblows users that have an attention span of three seconds. I am excluding myself and wanting instant answers at this time because I am preparing my Mother's house for sale, she died, I am trying to tend to a terrible pressure burn that I got that is soooooooooooo painful, et cetera.  With all this going on I just do not currently have the time to look through Man - no matter how excellent it is.  With OS/2 even when developers started writing for it there was too much of these little nuances going on.  We love computers playing with them, blowing them up, taking them apart.  The average user wants the internet, mail, IM and other goodies that work then and there.  They do not want to post and then wait for a reply as to why Winsocks isn't working.  I've come to the realization-- the more dumm'd down the OS the better the public likes it.  Let us hope history does not repeat itself.

Best,

Bill

---

