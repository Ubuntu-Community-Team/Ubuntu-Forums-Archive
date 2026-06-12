---
title: "Default Location of Mounted Remote Servers"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by sjxm9203 on 2007-03-21
I have added a remote windows file system to my places by using the "connect to server" choice on the drop down places menu.

The filesystem appears as an icon on my desktop and as a place in my file browser.

My question is: Where does this directory actually live on my filesystem right now? I would like to go to the command line and cd to it, but i cannot find it.

Coming from a Mac background I am used to these things showing up in the /Volumes folder. Is there any equivalent in Ubuntu?

Also, I have already tried making my own directory and running mount -t smbfs to make the directory connection myself, but I could not get the file permissions with the server to work. That is why I have gone the GUI route to mount the remote directory.  The connection is easy and straighforward.

Thanks.

---

### Post by sjxm9203 on 2007-03-21
Nevermind.  I got smbmount to work, so I can mount the filesystem anywhere that I like.

My problem was that I needed to add my NT domain name to the front of my username to make the authentication work.

---

