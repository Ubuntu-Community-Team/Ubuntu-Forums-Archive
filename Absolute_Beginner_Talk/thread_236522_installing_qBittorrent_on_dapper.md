---
title: "installing qBittorrent on dapper?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by wbc1228 on 2006-08-14
hi
I'm trying to install qBittorrent on my computer (running on ubuntu dapper).  The deb files are here -> [http://www.qbittorrent.org/?page_id=21](http://www.qbittorrent.org/?page_id=21)
The website states that qBittorrent has been tested on dapper.  However, when I tried to install it, I got multiple dependency errors (libc6 and a few others).  So, what piece of the puzzle am I missing?  How do I install qBittorrent when it requires libs that are found only in Edgy???  I tried to install the newer, unstable libc6 on computer but I failed miserably (got even more dependency errors.  to the point that Snaptic Package Manager couldn't correct itself and I had to do a clean install.  Good thing I'm just playing around with Linux at this point and the clean install was painless).

thanks in advance.

edit:
seems like qbittorrent has been updated to 0.61.  this time there are multiple install packages and there is actually one for ubuntu dapper.  yea!  (in the previous version, .50, there was one install file which was SUPPOSE to be for both edgy/dapper).
thanks everyone!

---

### Post by zxee on 2006-08-14
I'm guessing here since I don't have experiance with qbittorrent but if you're installing from the 6.06 desktop cd you may want to have synaptic install all upgrades i.e to 6,06,1 and then try installing qbittorrent.

---

### Post by wbc1228 on 2006-08-17
My system is up to date so that is not the problem.
Anyone else wants to take a stab at this?

thanks

---

### Post by signet on 2006-08-23
To fullfill the required dependencies for Dapper you can download files at this url: [http://packages.ubuntu.com/dapper/libs/](http://packages.ubuntu.com/dapper/libs/)

While installing the qBittorrent I downloaded and installed each library that was mentioned as a dependency error which included several libs - then I installed the rb-libtorrent_0.10-1_i386.deb package and finally installed qbittorrent_0.6.0_i386.deb.

I opened a terminal and typed 'qbittorrent' and the program opened

I am new to this linux thing aswell

I hope this helps

---

### Post by signet on 2006-08-23
I just found where the program resides on the desktop after the install - it is listed under applications > internet

If you are still having trouble I also used the Synaptic Package Manager to install three libraries using the search utility with a partial string of the first dependency that I ran into - I don't think it did anything to help because I kept getting the same dependency error.

I am pleased with Ubuntu after trying SUSE and Debian it seems much easier for someone new to linux

---

### Post by ChristopheDumez on 2006-09-05
Hi, I'm qBittorrent creator.

Please check that you have the following dependencies (provided by Ubuntu dapper):
*sudo apt-get install libcurl3 libqt4-gui libqt4-core python libboost-regex1.33.1 libboost-thread1.33.1 libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-program-options1.33.1*

Then you should get the following packages on qBittorrent.org:
[qbittorrent_0.6.1-0ubuntu4_i386.deb (new!)]("http://hydr0g3n.free.fr/qBittorrent_DEB/ubuntu/dapper/qbittorrent_0.6.1-0ubuntu4_i386.deb")
[rblibtorrent_0.10-0ubuntu8_i386.deb (new!)]("http://hydr0g3n.free.fr/qBittorrent_DEB/ubuntu/dapper/rblibtorrent_0.10-0ubuntu8_i386.deb")

Install the packages and everything should run fine ;)  It was tested on Ubuntu dapper/edgy, Debian Sid, Mandriva 2006, Gentoo. Please send me a mail (chris <at> qbittorrent <dot> org) or file a bug report [here]("http://bugs.qbittorrent.org") if you still experience probems.

I hope this fixes your problems.
Regards,
Chris.

---

### Post by TSP on 2006-09-05
First all thanks Chris for this client! much luck1 we really need a bittorrent client like this.
I always test your deb's bu i found bugs that make me to stop using it. for example the latest deb (2 September) don't install qbittorrent :()
Anyway, it would be great if i found the way to compile Qt 4 and then compile qbittorrent to test it better. or even better if someone make a guide to do this.

Keep up the good work! Cheers!

---

### Post by ChristopheDumez on 2006-09-06
Yes, someone has just reported that my last deb packages are really small and that they don't install anything. As you can see, I'm no debian packager but I'm learning : be assured you will have working debian/ubuntu packages soon :)

Concerning the Howto compile qBittorrent, I guess I could write it. Good idea.

---

### Post by microsafe17 on 2006-09-06
I am glad I was not the only one having problems with the deb package.  I just saw your client and it looks great was looking forward to switching (been dabbling with uTorrent through Wine and Ktorrent).

I was going to try the compile method but failed to make QT4 this morning before I ran out the door so I will have to check on that later.

Thanks again for your help and your work in creating this client.

---

### Post by TSP on 2006-09-06
> **ChristopheDumez said:**
> Yes, someone has just reported that my last deb packages are really small and that they don't install anything. As you can see, I'm no debian packager but I'm learning : be assured you will have working debian/ubuntu packages soon :)

Concerning the Howto compile qBittorrent, I guess I could write it. Good idea.

Great, please if you can jelp i can build deb's for ubuntu, i always build my fav pack like ktorrent, k3b, BMp, etc
I just get libtorrent compiled and working, but i have problem building qbittorrent 
If you post to compile the deb's maybe can i help you with that.

PS: Was me in irc the one who tel you that, yes the packs are really small 5 K and 8 K or something like that.

---

### Post by ChristopheDumez on 2006-09-08
Ok, I updated the dapper packages on qBittorrent.org and I also updated my earlier post here with the new urls. Could you please tell me if they are working fine for you ?

---

### Post by microsafe17 on 2006-09-08
Just verified them, they work wonderfully.  Thank you for your hard work, I would have compiled it myself but for some reason I just couldn't get qt4 to compile on my machine.  Installed them both and it showed up fine and ran fine.  Thanks again for the great work.  

Looks pretty solid so far, obviously I will have to use it more, but it is already looking much improved over the other alternatives in Linux.

*Edit - Unfortunately it doesn't look like it is allowed on a couple of my private trackers.  Hmm.... off to see why that might be.

---

### Post by ChristopheDumez on 2006-09-09
Hi,

I'm happy that the Dapper packages are finally working :) I'm quite busy these days but I'll work on debian sid / ubuntu edgy packages now.

Indeed, some trackers are allowing only famous BT clients : Hence, being able to make the tracker think we use Azureus would be a good solution.

If you can provide me with some torrents whose trackers are banning qBT I can start working on Azureus spoofing :) This should be very easy to do.

---

### Post by TSP on 2006-09-09
Chrins why do that? better talk with the owners of the tracker who abn you client. I am the owner of a tracker and i know for sure that this would be a good way.

PS: I can get QT4 to compile in my pc either, but i would be glad to help you making deb or testing the client :D

---

### Post by amgeex on 2006-09-10
Hey, I just found out about this client and I find it quite nice and easy to use. Thanks a lot!! 

There's a small problem, though I'm not sure if it's qBittorrent's fault entirely: Sometimes qBittorrent just closes without any errors. It justs closes itself. I just reopen it and it's all good, but its annoying.

I don't know if this has anything to do with XGL/Compiz?

Here's my specs:

Ubuntu Dapper - 6.06.1 all packages up to date.
Running latest XGL/Compiz without any problems.

Thanks for wonderfull client!

---

### Post by wbc1228 on 2006-09-11
> **amgeex said:**
> Hey, I just found out about this client and I find it quite nice and easy to use. Thanks a lot!! 

There's a small problem, though I'm not sure if it's qBittorrent's fault entirely: Sometimes qBittorrent just closes without any errors. It justs closes itself. I just reopen it and it's all good, but its annoying.

I don't know if this has anything to do with XGL/Compiz?

Here's my specs:

Ubuntu Dapper - 6.06.1 all packages up to date.
Running latest XGL/Compiz without any problems.

Thanks for wonderfull client!

That happens to me quite often (qBittorrent disappearing, crashing?).  What sucks is that once I try to run qBittorrent again, I get an error that the port that I have assigned to qBittorrent can not be opened (still being used by the previous qBittorrent that disappeared/crashed).

A few other issues that I'm running into with qBittorrent
- ports only go up to 9999 (why can I not use the other 50000 or so ports?)
- unicode files don't decode correctly.  not sure if this is a bug or is just a feature that hasn't been implemented yet.
- if a torrent has multiple files, I'm forced to download all the files first.  having the ability to deselect the files before downloading them first would be a nice feature.

I'm not running XGL/Compiz or anything fancy on my computer.

PS:
I realize this post sounds pretty negative but you're doing an awesome job with this, ChristopheDumez!  Can't wait until the next release of qBittorrent.

---

### Post by TSP on 2006-09-11
> **wbc1228 said:**
> That happens to me quite often (qBittorrent disappearing, crashing?).  What sucks is that once I try to run qBittorrent again, I get an error that the port that I have assigned to qBittorrent can not be opened (still being used by the previous qBittorrent that disappeared/crashed).

A few other issues that I'm running into with qBittorrent
- ports only go up to 9999 (why can I not use the other 50000 or so ports?)
- unicode files don't decode correctly.  not sure if this is a bug or is just a feature that hasn't been implemented yet.
- if a torrent has multiple files, I'm forced to download all the files first.  having the ability to deselect the files before downloading them first would be a nice feature.

I'm not running XGL/Compiz or anything fancy on my computer.

PS:
I realize this post sounds pretty negative but you're doing an awesome job with this, ChristopheDumez!  Can't wait until the next release of qBittorrent.

The problem is one option (minimize to try) just unselect that option. Qbittorrent is not really closed is in the system try but we can't see it.
You can use a port gihher than 9999, type it manually.

There is a guide to compile the last version but for me don't work i have to compile libtorrent with other option and install libqt4-dev to get qbittorrent from svn working.

---

### Post by wbc1228 on 2006-09-12
> **TSP said:**
> The problem is one option (minimize to try) just unselect that option. Qbittorrent is not really closed is in the system try but we can't see it.
You can use a port gihher than 9999, type it manually.

There is a guide to compile the last version but for me don't work i have to compile libtorrent with other option and install libqt4-dev to get qbittorrent from svn working.

thanks for the suggestions, TSP.
I unselected that option (minimize to tray) and qBittorrent is now disappearing (crashing) less often than it did before.  I guess that is what happens when qBittorent tries to minimize to a system tray that is nonexistence (I'm running Xubuntu, XFCE.  Not sure if the system tray thing is working for Gnome).

As for using ports higher than 9999, it is kind of working.  Seems like qBittorrent won't let me select a port bigger than 9999 as the min port range unless I enter in 9999 and click on the up arrow (going to port #63636 is going to take quite a while so this isn't a good solution).  Selecting a max port range above 9999 is a little easier, but is still kind of weird.  Like before, I have to enter in the number 9999 and then click the UP arrow.  Only this time, qBittorrent allows me to manually enter in a 5 digit number after doing so.  I guess this issue is still a problem since I only want to forward 1 port to qBittorrent from my router.  The only way to do that is to select a port below 9999 and enter in the same port number in the min and max range.

---

### Post by rider_royal on 2007-01-27
> **ChristopheDumez said:**
> Hi, I'm qBittorrent creator.

Please check that you have the following dependencies (provided by Ubuntu dapper):
*sudo apt-get install libcurl3 libqt4-gui libqt4-core python libboost-regex1.33.1 libboost-thread1.33.1 libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-program-options1.33.1*

Then you should get the following packages on qBittorrent.org:
[qbittorrent_0.6.1-0ubuntu4_i386.deb (new!)]("http://hydr0g3n.free.fr/qBittorrent_DEB/ubuntu/dapper/qbittorrent_0.6.1-0ubuntu4_i386.deb")
[rblibtorrent_0.10-0ubuntu8_i386.deb (new!)]("http://hydr0g3n.free.fr/qBittorrent_DEB/ubuntu/dapper/rblibtorrent_0.10-0ubuntu8_i386.deb")

Install the packages and everything should run fine ;)  It was tested on Ubuntu dapper/edgy, Debian Sid, Mandriva 2006, Gentoo. Please send me a mail (chris <at> qbittorrent <dot> org) or file a bug report [here]("http://bugs.qbittorrent.org") if you still experience probems.

I hope this fixes your problems.
Regards,
Chris.

Did exactly as you told here, and is worked perfectly:D . Version 0.6 is old but working good, I think its the latest one that is not working for me , yet:( ...
But still its a great piece of software...

---

### Post by Soarer on 2007-01-27
I just installed on Edgy - worked first time. Looks great too! I liked Azureus, but it decided not to run any more for me after something got updated, probably Java. This seems to do everything I need though - Azureus is great, but it did a lot of stuff I didn't understand :)

---

