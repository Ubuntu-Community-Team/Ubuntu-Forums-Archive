---
title: "Networking question"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by zodwallop on 2006-02-10
I feel like I'm missing something obvios, so hopefully the answer will be quick and painless.  I installed Ubuntu 5.10 earlier this week and have been, for the most part, loving every minute of it.  I think the only hurdle I have left before being completely satisfied is getting it to talk with my Winodws XP machine.  

I have download and installed numerous samba packages, clients, and other various things without much luck.  

When I am on my Windows machine, I can see both computers in my workgroup but cannot access the shared folder I set up in Ubuntu.  

When I am on my Ubuntu machine, at one point I was able to see the Windows machine via Smb4k, but no longer see it.  

I can access the internet from both computers without any problems.  

I also have Xbox Media Center installed on my Xbox which uses samba to connect to my Windows machine with no problems.  (with xbmc i use smb://windows.machine.ip and I can access all of the folders I have shared)

From Ubuntu, I can ping the router, any internet site, and it's own ip address, but it times out if I try to ping anything else connected to the router, ie. my vonage router, the windows machine, or the xbox.

Any ideas?  Thanks in advance!

---

### Post by zodwallop on 2006-02-11
Update:

When I go to Places > Network Servers from Ubuntu, I see "MAIN" (My Windows XP box), "UBUNTU_SERVER" (My Ubuntu box), and "Windows Network" (The workgroup set up on my Windows XP box).

If I double-click on "MAIN," I get an error message that says:
"The folder contents could not be displayed.  
Sorry, couldn't display all the contents of "Windows Network: main". "

I receive the same error message if I navigate though the "Windows Network" icon to the "MAIN" computer.

 :confused:

---

### Post by Discretion on 2006-02-11
not to sure, as i am as new as you but it maybe a Partion table thing.....i think you can only view one way.....just a guess
sorry cant help anymore

---

### Post by Zimmer on 2006-02-11
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
Post #5 should help you, and the links to the wiki pages for Samba.
It is normally down to setting Samba users on the Ubuntu machine properly and setting the sharing options correctly in the samba config file.
Regards

---

### Post by zodwallop on 2006-02-11
Thanks everyone for all your help!  I can now access the files on my Windows box from my Ubuntu box.\\:D/

---

