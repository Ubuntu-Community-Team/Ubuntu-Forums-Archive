---
title: "Very Important! FTP problems have rendered a website useless!"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ThinkBuntu on 2007-05-21
I'm hoping someone with FTP experience can answer this quickly. I am uploading some changes to a website via gFTP for the first time, and suddenly both the HTML page and the stylesheet, due to some permissions issue, have become inaccessible via a browser. Why is this? I used gFTP a few months ago and also experienced permissions problems like this. How do I keep this from happening?

I edited the file to allow others (groups and all users) to read the file; I even tried allowing write as well, but no luck. The website remains down. I tried using Kasablanca, thinking that maybe this was a client issue, but not the case. I don't have access to a Mac or PC to remedy this until tomorrow morning...

Note: This is very urgent for me because it's work I'm doing for a client. Bluefish and Quanta have proven great for web development, but FTP? Haven't quite got it down. Maybe I should've used a few dummy files before doing the real thing.

P.S. Forgive me for posting twice (one in General help) but this is really pressing. I "moved" it here, and would delete it there if I could.

---

### Post by louieb on 2007-05-22
assuming you are the file owner and the site is hosted on a Linux/unix machine. the permissions should be 644 or rw-r--r-- (same thing). Haven't used gFTP in awhile (I use gnome-commander) but it should allow you to change permissions on the remote machine.   Check the permissions on the local machine before uploading - don't remember gFTP changing them. 
Check the permissions on the directory should be 715 or 755. 
Just a guess

---

### Post by hartz on 2007-05-22
I have installed gFTP so I can see what you have.

You say that you "edited the file" but I assume you mean you changed the perissions.

using gFTP, you can Righclick on a file then select chmod from the menu.  This will bring up a panel with permissions options.  Turn on READ for USER, GROUP and OTHER.

Also make sure that the directory in which these files are located have both READ and EXECUTE for USER, GROUP and OTHER.

Leave Write-access enabled on the USER side only.

This goes for parent directories too.

---

### Post by andrew.46 on 2007-07-06
Hi,

 Read your problem:

> **ThinkBuntu said:**
> I'm hoping someone with FTP experience can answer this quickly. I am uploading some changes to a website via gFTP for the first time, and suddenly both the HTML page and the stylesheet, due to some permissions issue, have become inaccessible via a browser. Why is this? I used gFTP a few months ago and also experienced permissions problems like this. How do I keep this from happening?

 Same thing happened to me! You probably have "Preserve File Permissions" activated either as a general option or in a specific Bookmarked ftp site.

                        Andrew

---

