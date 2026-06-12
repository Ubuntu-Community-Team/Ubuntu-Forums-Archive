---
title: "Why is my desktop in the trash?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by mabtifro2 on 2008-02-26
when i try to copy a file onto my desktop, i receive this message:

"you cannot copy items into the thrash"

then i discovered that my desktop was in this directory:

"/home/marc/.Trash/Desktop"

but when i save downloaded files to the default "my desktop" location, they end up here:

"/home/marc/Desktop"

i was always wondering why they never actually showed up on my desktop after i finished downloading them, now i know. but one question... is this normal?

---

### Post by glennric on 2008-02-26
No.  Your Desktop should not be in the trash.  That is not normal.  You must have accidently moved it there.  How this could happen accidently--I don't know.

---

### Post by mabtifro2 on 2008-02-26
ok, well do you know how i can change it so i can see files on my desktop that are actually saved in my /home/marc/Desktop directory (assuming this is the correct directory for one's desktop)?

---

### Post by wolfen69 on 2008-02-27
you'l figure it out

---

### Post by spiderbatdad on 2008-02-27
run ```
gksu nautilus
``` and drag it out and drop it in your home folder.

---

### Post by mabtifro2 on 2008-02-27
i tried the above command and it seemed to work until i tried to drag the desktop into my home folder. i got an error: "You do not have permissions to write to this folder."

---

### Post by spiderbatdad on 2008-02-27
That is strange. It would actually be /home/username directory.

---

### Post by spiderbatdad on 2008-02-27
Notice how I write to my home directory in the screenshots below, by dragging and dropping the file, "Modem." And really you don't need gksu nautilus for this, as you are the owner of all those directories.

---

### Post by mabtifro2 on 2008-02-27
thanks spider it appears to be working except one little thing. new files that i download and save to my desktop are not shown. but i know they are there because i can find them when i search for them. and one more think when i go to Places-> Desktop it says: "Could not open location 'file:///home/marc/.Trash/Desktop'" how can i change that directory to eliminate the .trash part?

---

### Post by spiderbatdad on 2008-02-27
IDK looks like you tried to make a url out of it to me. Why don't you just empty the trash? If you have to, remove and reinstall ubuntu-desktop from synaptic.

---

### Post by mabtifro2 on 2008-02-27
spider, i restarted the machine and now all is good. those files appeared on the desktop and places-> desktop takes me straight there, PERFECT! thank you a million times. by the way, the layout of your desktop is very attractive, it looks like a mac OS. is there any simple trick to modify mine to look like yours?

---

