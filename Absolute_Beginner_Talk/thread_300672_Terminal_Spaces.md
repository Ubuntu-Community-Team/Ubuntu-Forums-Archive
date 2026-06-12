---
title: "Terminal Spaces"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by 4cesmoker on 2006-11-16
I am trying to mount my windows directory to linux but i can't get it to work. I put in :  sudo mount //thejew/Downloaded%20Files%20C /media/download

I already created the "download" folder in my media, all lowercase.

I get : 

22234: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed


also, the %20 I thought was used as a space, I checked the "Always use text-entry location bar" in the Edit->Preferences.

Could someone please help me ?

---

### Post by CatKiller on 2006-11-16
The easiest way to type a path in the Terminal is to use the Tab-completion feature of bash. Start to type the path and then press Tab - it will fill in as much of the rest as it can. Press Tab again, and it will give you a list of the remaining ways that you could fill in the path. Very handy. And you don't have to worry so much about the fact that your filenames are case-sensitive.

Otherwise, I believe you can use double-quotes and use the spaces, like **cd "my Imaginary directory"**. Or you can "escape" each space (or other freaky character) with a \, like **cd my\ Imaginary\ directory**.

As far as mounting Windows things in Ubuntu goes, you might find these guides helpful:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows](http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

EDIT: I've just realised you're looking at network Windows folders - Samba shares or the like. I'm afraid I don't know anything about those, but the guides I've linked to are useful nonetheless.

---

