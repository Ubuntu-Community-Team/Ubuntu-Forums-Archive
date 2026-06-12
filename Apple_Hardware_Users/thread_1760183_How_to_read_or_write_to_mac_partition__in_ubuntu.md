---
title: "How to read or write to mac partition  in ubuntu"
date: 2011-05-16
forum: Apple Hardware Users
---

### Post by unagimiyagi on 2011-05-16
Hi,

Is there an easy way to read/write to a mac partition inside ubuntu 11?

Any graphical ways to mount / umount?  

Thanks

---

### Post by jerrycal on 2011-05-17
> **unagimiyagi said:**
> Hi,

Is there an easy way to read/write to a mac partition inside ubuntu 11?

Any graphical ways to mount / umount?  

Thanks


Yes, use Nautilus: Go to your Home folder and MacintoshHD should be visible there. Mount it and then you can browse your file system. There will be some issues with permissions, so you will only be able to access your Shared/Public folder. If you want to get to all other directories you'll have to start Nautilus as root by: gksudo nautilus
You can copy files to your Ubuntu folders, but again - permissions will be issue...so while logged in as root you'll have to change the permissions to "you - the user"

---

### Post by unagimiyagi on 2011-05-17
> **jerrycal said:**
> Yes, use Nautilus: Go to your Home folder and MacintoshHD should be visible there. Mount it and then you can browse your file system. There will be some issues with permissions, so you will only be able to access your Shared/Public folder. If you want to get to all other directories you'll have to start Nautilus as root by: gksudo nautilus
You can copy files to your Ubuntu folders, but again - permissions will be issue...so while logged in as root you'll have to change the permissions to "you - the user"

Hi jerrycal,

Could you go into more detail please?

My mac partition (snow leopard) is already visible in ubuntu 11.04.  I didn't have to do anything.  When I want to see my documents or downloads folder on the mac, There's a gray x over the folder icon and it won't let me view it.  

Clicking on it gives me a "the folder contents could not be displayed. you do not have the permissions necessary to view the contents of "Downloads"  "

I am on a fresh install of snow leopard and ubuntu 11.04 dual boot.
I did this fresh install b/c other posts said that you have to format the mac partition as hfs but without journaling. Of course, I did this only to find out that mac os x won't install unless your mac partition is journaled, so I don't know what that post was talking about.  

All the other posts of command line wizardy, unless they can be explained in more detail, I could not get to work although I tried.

I did your gksudo nautlius command from a terminal window, and nothing happened at all.  

Thanks!

---

### Post by jerrycal on 2011-05-17
> **unagimiyagi said:**
> Hi jerrycal,

Could you go into more detail please?

My mac partition (snow leopard) is already visible in ubuntu 11.04.  I didn't have to do anything.  When I want to see my documents or downloads folder on the mac, There's a gray x over the folder icon and it won't let me view it.  

Clicking on it gives me a "the folder contents could not be displayed. you do not have the permissions necessary to view the contents of "Downloads"  "

I am on a fresh install of snow leopard and ubuntu 11.04 dual boot.
I did this fresh install b/c other posts said that you have to format the mac partition as hfs but without journaling. Of course, I did this only to find out that mac os x won't install unless your mac partition is journaled, so I don't know what that post was talking about.  

All the other posts of command line wizardy, unless they can be explained in more detail, I could not get to work although I tried.

I did your gksudo nautlius command from a terminal window, and nothing happened at all.  

Thanks!

Like I said, the problem is permissions. You are browsing your OSX partition from your Ubuntu username and the files in OSX are set to be readable from OSX user name...
So you need to be root.
First do this: in Ubuntu, open terminal and type: 

gksudo nautilus

That will open your nautilus, which is the window manager, as root...And from there you will be able to go to your OSX partition and be able to view all files and move them to Ubuntu...

---

### Post by unagimiyagi on 2011-05-17
Hi Jerrycal,

Thanks alot! I'm retarded.  gksudo nautilus absolutely worked.  

If I can squeeze another piece of advice from you--is it possible to write to the mac partition as well?  

I guess the idea would be to save my say, documents and music to a common partition that I can access between mac and ubuntu.  

If you don't know, no problem.

---

### Post by jerrycal on 2011-05-17
> **unagimiyagi said:**
> Hi Jerrycal,

Thanks alot! I'm retarded.  gksudo nautilus absolutely worked.  

If I can squeeze another piece of advice from you--is it possible to write to the mac partition as well?  

I guess the idea would be to save my say, documents and music to a common partition that I can access between mac and ubuntu.  

If you don't know, no problem.

Glad it worked...
I guess you could store them in Shared folder. As you noticed, if you go to the OSX partition logged in as user, rather then root, all the folders will have the grey X over them telling you you don't have the permission to access the folder. Except for Public folder. That won't have the X. So, you can go to OSX preferences, turn on File Sharing and set the permissions to read and write by "everyone" for whatever folder you want to designate for the files. Now, if the folder already has some files in it, like documents, you'd have to change permissions for every file as well. Changing it for the folder alone won't automatically change the file permissions. Or just use DropBox. But I agree, the best thing would be to partition where you would store files for both systems...
Or use separate external hard drive or NAS. Also, if you do google search, there are lots of guides how to share files using Samba.

---

