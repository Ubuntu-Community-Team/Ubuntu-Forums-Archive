---
title: "Help using MacBook Pro Intel Based with Parallels"
date: 2006-07-29
forum: Apple PPC Users
---

### Post by Tom_Linux on 2006-07-29
I´m running Ubuntu under Mac OS X using Parallels Desktop for Mac

[http://www.parallels.com/en/products/workstation/mac/](http://www.parallels.com/en/products/workstation/mac/)

It works OK in this virtualization but have a great disadvantage: Can't access the files under Mac OS X Environment.
I try everything... install ubuntu HFS+ resources, configurate correctly the LAN in both sides (Ubuntu and Mac OS X) and the result is that can see the share volumes but all are empty and can't access the files.
If I connect to the LAN a PC with Windows XP Pro then can share all the stuff with the Mac and Ubuntu under Parallels Desktop for Mac but only across the PC with Windows XP Pro.
CONCLUSION: How can access the Mac OS X volumes or shared folder in the Ubuntu desktop under Parallels AND/OR access the Ubuntu volumes or shared folder under Parallels in the Mac OS X desktop.
This is ESSENTIAL for use Ubuntu under Mac OS X. If I can't share the information then, it's a pity, but can't be use it in virtualization way. :sad: 

Can someone help me, please ?

Thank you.

Tom

---

### Post by chasisaac on 2006-07-30
I ran into this problem also. The bad news is that we are going to have lobby the Parallels people to provide support.

---

### Post by nimbuscott on 2006-09-01
I had the same problem sharing files between Ubuntu running under Parallels and Mac OSX. I found two solutions:

1) Turn on Personal Web Sharing on the Mac. Put items that you want to access on the Mac from Ubuntu in the *username*/sites folder then navigate to them with your web browser by entering:
```
http://youripaddress/~yourusername/
```

in your web browser's url box. Right click to download contents. Cumbersome and no way to get files onto mac from Ubuntu, it is download to Ubuntu only.

2) Best Way: Download [sharepoints]("http://www.hornware.com/sharepoints/") for Mac OSX. This worked great! Turn on Windows File Sharing on the Mac. Set up a folder on your mac to share using Sharepoints ( I chose my Public Folder) then you can move files to and from this folder from Ubuntu :grin: 

Thanks to the users on this Ubuntu forums post for the solution:
[Samba Problems with Ubuntu and Mac OSX]("http://ubuntuforums.org/showthread.php?t=206539&highlight=folder+share+mac")

---

