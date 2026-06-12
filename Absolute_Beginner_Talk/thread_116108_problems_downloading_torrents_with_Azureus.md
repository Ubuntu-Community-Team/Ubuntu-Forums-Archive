---
title: "problems downloading torrents with Azureus"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by kelticwolf on 2006-01-11
Hi there I just started using Unbuntu and have Azureus on my machine. It worked fine for the first three days and now anything I try and download O get an error saying "/tmp/phillcollins.collection.torrent could not be opened because an unknown error has occurred Try saving to disk first and then opening the file"

Well I tried that with another file and when I tried opening it I got this error: 
Failed to access torrent file 'file:///home/****/My%Music/Korn_See_You_On_The_Other_Side.torrent. Ensure sufficient temporary file space is available (check browser cache usage}

My questions are what could be causing the first error message out of the blue and how do I check my/clear my browser cache usage?

Thanks for any help you can give :)
Jenni

---

### Post by Zelut on 2006-01-12
Is the file phillcollins.collection.torrent still intact & where Azureus thinks it should be?  I think i had a similar problem in the past where I had moved a file & then Azureus couldn't find it... just an idea.

The other--clearing the browser cache--is easy.  You'll find it in Edit > Preferences > ...one of the tabs (depending on your version of firefox).

---

### Post by kelticwolf on 2006-01-12
I wish it was going to be something simple llike that ... This error happened when I was trying to download it from it's site, and is happening on any/every file I try and download. They are not on my system for me to move except the one I save to my desktop and that got the 2nd error message I wrote about.

---

### Post by kingsidy on 2006-01-12
try downloading the torrent index file to your desktop instead of opening it directly through firefox, then drag the file onto azureus (already open) and see if you still get the error. if not then the problem is with the way firefox handles the torrent index. if you still get the same error then try reinstalling firefox

---

### Post by joura05 on 2008-01-03
I have this same problem and just figured it out. Kingsidy is right, just download it to desktop and then open it from azureus. It seemed a little slow starting for me but its going good now.

haha, i didnt realize how old this thread was... i guess im a bit behind the times

---

### Post by ~LoKe on 2008-01-03
> **joura05 said:**
> I have this same problem and just figured it out. Kingsidy is right, just download it to desktop and then open it from azureus. It seemed a little slow starting for me but its going good now.

haha, i didnt realize how old this thread was... i guess im a bit behind the times

Old topic, yes, but perhaps an explanation:

The /tmp file is automatically cleared after a certain period of time.  So, Azureus would be looking for a file that no longer exists.

---

