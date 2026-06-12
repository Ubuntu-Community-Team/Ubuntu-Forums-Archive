---
title: "Ubuntu Add/Remove program issues (+ possible fix)"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Forceflow on 2006-12-02
Hello everybody.

I'm pretty new to ubuntu and linux in general (started actively using debian/fedora a half a year ago), but I wanted to share my story with you:

I recently installed Ubuntu 6.10 on my pc. Note that I'm using the i386 version, instead of the 64-bit version (my CPU is an AMD64 bit). I just heard there was lousy flash support for the 64-bit edition, so I went for regular.

One of the first problems that occurred was the inability to update ubuntu. Only a few packages were downloaded, and I had to try 10 times before all the packages were in. I tried disabling my router firewall, yes.

Most of the downloads would fail stating: 

[B]Failed: connection reset by Peer.
or
Error in Gzip: not a gzip file.[/B]

Another thing that happened that - after an unsuccessful try of installing an application - most of the applications were marked as **"unable to install on your system (i386)"**. After a bit of fiddling around with other repositories this disappeared - sometimes.

Note that I was still using **standard** ubuntu configuration. The only thing that I did install succesfully was the Binary X.org driver for ATI cards. (Running X1600 in dual-screen now ... phew, glad that worked. If you want to know how I did it, check the thread in the graphics board)

After a few ubuntu re-installs, I decided that **I** did not create the problem. It was there from the beginning.

The thing I did to fix this problem was this: 
I emptied my source.list, after backuping it, and opened up the software resources window. All of the checkboxes were unmarked now. I checked the ones I wanted, and re-opened my source.list. I tried an update, but got the same errors. Then I changed the **http:// tags to ftp:// tags.** 

Things went flawlessly and fast. I just succesfully installed VLC, which was impossible before because half of the .lib-packages failed to download.

Hope this helps someone. I

---

### Post by Kurt` on 2006-12-02
The first thing that popped into my mind when reading your post was "IPv6 is slowing everything down".

If your Firefox/OtherBrowser feels sluggish as well, refer to my last post in this thread:
[http://ubuntuforums.org/showthread.php?t=219016](http://ubuntuforums.org/showthread.php?t=219016)

You could also try other HTTP repositories, the main ones are usually a bit slow because EVERYONE uses them. :)

---

### Post by Forceflow on 2006-12-02
I don't think it has something to do with the repositories themselves. I've used the same repos on a different computer, and they work perfectly well there.

They just seem to lose connection very fast on this computer, when using standard http.

---

