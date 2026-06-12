---
title: "Can I delete this now?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-05-27
So I followed instructions on [this Wiki page](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndis%29), right. Down at four, you know, installing a new version of ndiswrapper, I made a file in my Home directory called 'ndis'.

Since now I have my Network Adapter up and running, can I delete the file 'ndis' that was used through those instructions? Is ndiswrapper installed somewhere else now, or in this file?

Also, I made a folder called 'Drivers' where I put the driver for ndiswrapper to use. So now since ndiswrapper has the drive, can I delete the 'Driver' folder?

---

### Post by dmizer on 2006-05-27
i really am not sure what files and directories you are referring to, but if it has a .tar.gz or .deb on the end of it, you can delete it.

tar.gz is just like a windows zip file.  if you created a directory to contain all the files you extracted from whateverfilename.tar.gz ... you can delete that directory and all it's contents once your install is complete.

---

### Post by SZF2001 on 2006-05-27
I'll post some pictures to show what I'm talking about.

[IMG]http://i3.photobucket.com/albums/y88/cheaptrick905/ndis.png[/IMG] - Home Folder
[IMG]http://i3.photobucket.com/albums/y88/cheaptrick905/ndis2.png[/IMG]
[IMG]http://i3.photobucket.com/albums/y88/cheaptrick905/ndis3.png[/IMG]

Last two show whats inside the ndis folder.

---

### Post by uzi09 on 2006-05-27
lol, sorry no one has replied yet. i guess no one really knows, or no one that knows has seen this yet :S

usually in cases like this, i just try to make the directory hiddin, or change its name and see if everything still works. if that works, then i guess you don't need it.

(btw, something that struck me while i was writing this, try just changing the permissions so no one can read the directory :D -- see if that'll work. it think this may be a better "test" then what i said above).

try:
sudo chmod a-r ndis
(or w/e the dir is called)

---

### Post by SZF2001 on 2006-05-28
Ola! It works!

Thank you, friend!

---

### Post by dmizer on 2006-05-28
[QUOTE=uzi09]lol, sorry no one has replied yet. i guess no one really knows, or no one that knows has seen this yet :S[/QUOTE]
heh ... sorry, i had to step out for lunch.  but it's always good when you can solve problems on your own. :cool:

---

