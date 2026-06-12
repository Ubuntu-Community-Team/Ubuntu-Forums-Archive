---
title: "aMSN Problem"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Mattread92 on 2007-07-13
Hi. I downloaded and installed Ubuntu 6.06 last night, and just installed aMSN messenger, When I try to sign in I get this window pop up [see screenshot]. I don't know what my system architecture is! and I tried all of the linux ones and got an "Error installing TLS Module:: Couldn't get [url of file]" message every time! 

As you can guess I'm totally new to Linux, and any help would be greatly appreciated!

[IMG]http://img401.imageshack.us/img401/9064/screenshotvv1.png[/IMG]

---

### Post by Hendrixski on 2007-07-13
first off let me check how you installed it... did you go to Applications-->Add/Remove and select aMSN or did you install it from some website?  always check the Ubuntu way first because often times we modify it to make it easier to install stuff.  I mean WAY easier.


second I would assume that if you're on a regular PC you want x86.  If you're on a 64-bit PC then you want x86-64. (if you don't know, pick x86).
If you're on a mac you want powerpc and if you're on a sparc box you want sparc (though, unless you are using a server that can run the network of a fortune 500 company you are probably not using a sparc box)... everything else is for operating systems that are NOT Ubuntu (like BSD, Solaris, or MacOS X).

---

### Post by Hendrixski on 2007-07-13
Oh... and I see that you're new here... so I thought I would give you a warm welcome that comes from the heart...

**WELCOME TO THE COMMUNITY!**
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others.  Some of us here are even the same people who write the software you're using, or the documentation you're reading.  Why?  because we value freedom so we built a platform that is free.

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC. Installing IRC is easy and fun. Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too! Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it. A lot of it is written by the same people who answer questions on these forums. If dry manuals aren't your thing then relax and watch some videos. [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc. Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by Mattread92 on 2007-07-13
Hi, thanks for your reply! 

I installed aMSN using the package file that you can see on my desktop in the screenshot, which I downloaded from the aMSN website.

---

### Post by Hendrixski on 2007-07-13
> **Mattread92 said:**
> Hi, thanks for your reply! 

I installed aMSN using the package file that you can see on my desktop in the screenshot, which I downloaded from the aMSN website.

:-) I'm pretty sure aMSN is in the Ubuntu repositories.  We usually recommend that you check there first, and if you can't find the program you're looking for (which I doubt will happen, there's some 50,000 programs in there) then get it from the site.  The difference is 5 seconds to install from Ubuntu's Add/Remove or a few minutes to find the site then DL from the site and run their installer.

:-) like I said in the welcome message.  We're happy to have you on board.  :-)  enjoy.

---

### Post by Mattread92 on 2007-07-13
Where can I find the repositories?

---

### Post by Mattread92 on 2007-07-13
Can anybody else help??

---

### Post by kittyhawk63 on 2007-07-13
Sorry that you had to wait so long to get an answer about the repositories. Here you go.
System -> Administration -> Synaptic Package Manager. You are now in the repositories. This is where you find approved programs.
kh

---

### Post by Mattread92 on 2007-07-13
I have done a bit of googling for a while and found the repositories, thanks!

---

### Post by kukibird1 on 2007-07-14
> **Mattread92 said:**
> Hi. I downloaded and installed Ubuntu 6.06 last night, and just installed aMSN messenger, When I try to sign in I get this window pop up [see screenshot]. I don't know what my system architecture is! and I tried all of the linux ones and got an "Error installing TLS Module:: Couldn't get [url of file]" message every time! 

As you can guess I'm totally new to Linux, and any help would be greatly appreciated!

[IMG]http://img401.imageshack.us/img401/9064/screenshotvv1.png[/IMG]



Open a terminal  and issue the following commands .

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz) 
tar xvzf tls-1.5.0-linux-x86.tar.gz 
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50
Make sure /usr/lib/tls1.50 is set in the  tools>preferences>advanced options menu in Amsn. 

Restart Amsn

---

### Post by ace-n-wifey on 2007-08-20
I have tried the above in the terminal and I type the first line with the url in it and it seems to be doing something and says files.1 has been saved and then I enter the second line and it says:
tar: tls-1.5.0-linus-86.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

So now I don't know what to do, I think I origninally got it from add/remove and I just tried to reinstall in the synaptc package manager - Can anybody help me with this??

---

### Post by monroetransfer on 2008-01-06
Thanks, kukibird1, I had the same problem. This has been bothering me for a while, cause I really need webcam support!

---

### Post by patrickfromspain on 2008-01-06
In dapper, if I remember correctly, the fix was the following:

sudo apt-get install --reinstal tcltls
gksudo gedit /usr/lib/tls1.50/pkgIndex.tcl

in that file, it says something package ifneeded tls 1.5. The bug is because is should be 1.50 instead 1.5. Just add that 0, save and close. close amsn completely and then restart it. Should work now. If now, in the preferences window set tls to: /usr/lib/tls1.50

Hope it helps!

---

