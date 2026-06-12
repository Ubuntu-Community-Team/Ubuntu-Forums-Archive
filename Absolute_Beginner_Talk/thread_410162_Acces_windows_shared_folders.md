---
title: "Acces windows shared folders"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by colinireland on 2007-04-15
Can anybody tell  me how I can connect to windows shared folders using ubuntu?

I am new to linux and want to get music, movies etc from my housemates laptops that are on our wireless networks.

any help would be greatly appricated.

Colin

---

### Post by tchoklat on 2007-04-15
I found out today that you also need ntfs-config to work with ntfs-3g here is a how to link.[_[COLOR=#bd5900]http://ubuntuforums.org/showthread.php?t=217009[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by FuriousLettuce on 2007-04-15
You don't need ntfs-config or ntfs-3g, simply go to Places (in the panel at the top) -> Network Servers -> Windows Network

---

### Post by steve.horsley on 2007-04-15
Easy: 
Launch nautilus.
Make sure you have a text-input location rather than boxes, by clicking the pencil icon to the left of the location if needed.
Enter the location like this:
smb://domainname;username@computername/share
That's a semicolon between the domain name and user name.
Or you can use the nautilus menu File->Connect to server...

---

