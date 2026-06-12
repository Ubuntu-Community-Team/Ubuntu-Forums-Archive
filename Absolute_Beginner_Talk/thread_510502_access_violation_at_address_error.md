---
title: "access violation at address error"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by K_Soze on 2007-07-26
Okay, so I start the wine file, go to avitodvd.exe and doubleclick.

It starts up okay, but as soon as I select my avi file it gives me the error

 "access violation at address 00410C5 in module 'avi2dvd'exe. Read of address 00000000"

I have tried the file on my "desktop" and in "my documents" with all the permissions on the file set to read and write for everyone.

What should I try next?

---

### Post by Rocket2DMn on 2007-07-26
I think the file needs to be in a subdirectory under ~/.wine/drive_c/ because that is where wine sees the imaginary c:\ drive.  Anything outside of there might not exist to wine.

---

### Post by K_Soze on 2007-07-26
I search for anything with "wine" in it using filebrowser and get nothing. This is *&^%$#@! because I can locate some in user/bin but I can't find this "c" drive. 

How do you search with wildcards? I have used ? and * in filebrowser and I don't get jack.

---

### Post by Rocket2DMn on 2007-07-26
.wine is a hidden folder inside your home directory.  Anything that starts with a "." is hidden.  * is the wildcard.
Navigate in Nauitilus to your home directory and hit CTRL+H to view hidden files/folders.  You will see .wine and can open it and see the drive_c folder.  Open that and it should look like a windows c:\ drive.  You can put your avi file in here, then run avi2dvd.exe.
Why do you need this program anyway?  There are native linux programs that should be able to burn .avi files to DVD video.

---

### Post by K_Soze on 2007-07-26
thanks, I'll look around.

PS, I've tried avidemux but I'm having some difficulties with a specific file. Avidemux is okay but...

---

