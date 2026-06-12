---
title: "MythTV on Mac OS X"
date: 2009-09-16
forum: Apple Hardware Users
---

### Post by aresgodofwar30 on 2009-09-16
I'm hoping somebody will be willing to help me.

I have Snow Leopard (10.6) installed on a Mac Mini. I am trying to install MythTV and am running into a problem.

I got MySQL installed and ran the commands listed on the wiki page: [http://www.mythtv.org/wiki/Mac#Installing_MythTV_Backend_on_Mac_OS_X_using_prebuilt_binaries](http://www.mythtv.org/wiki/Mac#Installing_MythTV_Backend_on_Mac_OS_X_using_prebuilt_binaries)

When I run the MythTV-Setup.app, I choose english then I get a page that allows me to type in all the information about the database. After typing it in, I get an error saying that it wants to update my schema from 0 to 1214. Then it says it couldn't backup my database. At this point there are two buttons to click on. Exit and Update. If I click either button, the app closes and nothing happens.

I have searched the web furiously and found no website dedicated to MythTV and Mac OS X. Hopefully someone here can lend a hand!

---

### Post by Nigel Pearson on 2009-09-17
The mythtv-users mailing list is the best place to ask questions, but I will take pity on you :)

1) 10.6 is still new. It isn't possible to build Qt and mythtv on it yet.

2) Others have reported that the 10.5 built binaries (*i.e.* what you downloaded) worked OK for them, so you will need to dig deeper and find out what errors are being reported. To do that, open Console.app and look for the MythTV-setup output.

3) What are you trying to do with MythTV on the Mac? Connect to an already working Ubuntu backend? If so, then you should try MythFrontend.app first and see if it can connect to the backend, view your recordings, et c.

4) If you are trying to record stuff on the Mac, then it makes sense to have the database locally (*i.e.* on localhost). That way, you wouldn't have had to enter the database information. In fact, delete the file ~/.mythtv/mysql.txt - you shouldn't need it for a local database.

---

### Post by aresgodofwar30 on 2009-09-17
Thank you for the help, Nigel.
My primary goal is to record on the Mac Mini, then I'll have a look at the Frontend and see if it is something I want to use. I've also read elsewhere on the web where people use Plex as the frontend. So at this point I just want to tinker with what I have and see what works.

I ran into one other site late last night that had almost an identical setup to me. I emailed him and he told me that  10.6 is probably causing the problem, so I think I'll have to downgrade or wait for MythTV to be updated for the new version. Seems Apple did a lot of tinkering and changed many things with Snow Leopard. I also found that the new OS changed the way the system receives commands from the Apple Remote and that is causing problems with Plex and Boxee as well.

However, I will give your suggestion a try. I'll post my results here for others to see. :KS

---

