---
title: "Install w/out cd???"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Newbie_Chavo on 2005-12-27
Hi all,

I am trying to get Ubuntu up and running on my Powerbook G3 Bronze '99 Lombard.

Problem is that, when the installer starts installing the base system, my built-in cd-rom drive opts out. It's a tattered one that has had trouble reading home-burnt cd's for ages. During large operations, such as installs or mounts, it just jitters arount without actually getting any data. The install stalls at about 6 % and gives load error saying it can't copy from the cd-rom.

I wondered whether it was possible to transfer all requiered documents to a mounted drive or partition via my 265 Mb USB-stick (probably in two or three batches) and to install from the partition in stead of a cd-rom. Other options are welcome to!

You will have to spell out any command line ops because I'm green as grass at Linux.

Thanks a lot for taking the trouble.

Chavo

---

### Post by ninotob on 2005-12-27
Not exactly for the faint of heart, but you can always netboot "yaboot" -- yaboot is an installer for PPC hardware.  That's the method I've used on G3s w/ dodgy cds:

[http://www.ubuntuforums.org/showthread.php?p=311246#post311246](http://www.ubuntuforums.org/showthread.php?p=311246#post311246)

---

### Post by Newbie_Chavo on 2005-12-27
Thanks Ninotob. I checked it out but I do not think it is the best option in my case. I do not have trouble starting up the installer, nor booting the linux kernel. Moreover, I think you used a linux host for the netboot, and I do not have one. Any net connections would be difficult anyway in my WLAN environment. Thanks for the post. I will keep it in mind if nothing else works!!!


Chavo

---

### Post by ninotob on 2005-12-27
Just to be clear, the netbooting of yaboot downloads a very small kernal to run the installer from.  The OS that you'll actually use is installed directly off the net -- almost as if you installed with the "server" option from the cd, then did "sudo apt-get install ubuntu-desktop".  This would solve the problem with the CD not tranfering data because all the install files would come straight off the net.  Of course, this requires a decent network connection.

In fact, the server install might even work for you because the installed amount is so small, it won't tax your CD.  You get to a text login prompt, login, then issue the apt-get command above.

If you find no other solution, I could set up yaboot on a server (that old suse system has been changed to ubuntu and I haven't had to netboot anything since so I'd have to resetup everything -- good practice though) and you could start it from there instead of setting up your own.  Once it's going, it actually just uses the ubuntu repositories to download the necessary install files so you'd only grab a handful of megabytes from me.

Personally, I don't know why netbooting isn't more of an option w/ ubuntu generally.  It's really cool and wastes no media.

---

