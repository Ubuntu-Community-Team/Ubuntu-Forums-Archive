---
title: "Apple MobileMe (.Mac) in Ubuntu"
date: 2009-01-15
forum: Apple Hardware Users
---

### Post by happenstobe on 2009-01-15
Hey all!
I've been trying to figure this trick out for a while.
My primary machine is a mac, and I'm a long time user or Apple's MobileMe service. I've been trying to search through different forums to find a way to connect to my iDisk under ubuntu and I've followed a few methods, none of which seem to work the way others are describing them.

The first/best method I found was to use the file browser, go under the file menu and select "Connect to Server..."
All the guides that use this method say to select WebDAV as the service type, server = idisk.mac.com (or idisk.me.com (doesn't matter)), then make the folder and user name your mobile me user id. Some of the guides said to set the port to 80, but i have found that this is not necesary. I click Ok, this asks for my mobileme password - i enter it and hit ok, and it seemingly brings up my idisk.

I thought all was good, I can browse through the folders, see my files, but if I try to drag anything to/from the idisk from/to my own drive, I get an error each time. Also, if I try then later on to select the webDAV entry for the server from the sidebar in the file browser, i get an error that says "Not a webDAV enabled share. Please select another viewer and try again." No one else on the previous forum entries I've found seems to have this problem.

Any ideas/suggestions?

---

### Post by landonjh on 2009-08-17
I seem to be having the same issue. Any thoughts out there?

---

### Post by JedTheHead on 2009-09-19
I don't even get that far... I get "Not a WebDAV enabled share" when I try to open the mounted folder.  This has been driving me nutz... Anyone else get this to work?

---

### Post by BrianMCollins on 2011-11-05
I was getting that error, then I changed the server name to idisk.me.com, and I got connected. 

Still not solved however, because if I try to open for example. a .doc file with LibreOffice, I get a dialog box claiming "General Input/Output error.  I can however, copy to/from my iDisk.  I found that I needed to first get the properties of my iDisk folder and let it inventory everything there.  Then it worked.

Hope that helps.

---

