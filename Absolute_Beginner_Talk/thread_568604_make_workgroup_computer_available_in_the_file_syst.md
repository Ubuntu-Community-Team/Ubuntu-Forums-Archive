---
title: "make workgroup computer available in the file system"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by DrScum on 2007-10-06
my Ubuntu machine is part of a workgroup and I can see and access shares of other workgroup members in "Places". How do I include those shares into the file systems so that I have them available e.g. during File>Save operations?
I guess what I am asking for would be the Ubuntu equivalent of the "add network connection" in WinXP. 
When I am trying to create a Link to a Workgroup computer I am getting the error message: [Error "Operation not permitted" while creating link to "network://<name of share> ]

<name of share> is the name of the workgroup computer that I am trying to connect to.

---

### Post by mikeyphi on 2007-10-06
Since you can get to other shares through 'Places' - you should be able to do the same thing by using "File/Save as". 
Hope this is what you meant.

---

### Post by DrScum on 2007-10-06
Well, that was exactly my problem, that I couldn't do what you suggested. When trying to save a file only the local directories were available but not the network shares.

However, in the meantime I found out myself how it works: Select Places>connect to server and select the share you wish to be connected to then the share will be available in the file system. 

I hope I won't have to redo this manually after each boot. We'll see

---

