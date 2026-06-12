---
title: "Editing files in Windows from Ubuntu"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by novinthen on 2007-06-25
Hi there.

I'm wondering how to edit files inside my Windows(C:) from my Ubuntu ( D: )

I can access the files(while im in ubuntu ) , can copy and move them to ubuntu. But I cant delete / edit the files. It says im not the OWNER ...no  permission etc ...

Before this I backed up all my files from C: to D: when i reformatted my C:. Now having tough time to move back all the files from D: to C: ...:(

so how do i set permission in Windows so that i can edit files in windows from Ubuntu?

And one question , Why i cant see any Ubuntu files inside D: when im in Windows. ?? 

Thanks in advance!:popcorn:

---

### Post by Jimmyfj on 2007-06-25
> **novinthen said:**
> Hi there.

I'm wondering how to edit files inside my Windows(C:) from my Ubuntu ( D: )

I can access the files(while im in ubuntu ) , can copy and move them to ubuntu. But I cant delete / edit the files. It says im not the OWNER ...no  permission etc ...

Before this I backed up all my files from C: to D: when i reformatted my C:. Now having tough time to move back all the files from D: to C: ...:(

so how do i set permission in Windows so that i can edit files in windows from Ubuntu?

And one question , Why i cant see any Ubuntu files inside D: when im in Windows. ?? 

Thanks in advance!:popcorn:

First of all you need to install NTFS read/write capability in Ubuntu - You can do that through Programs/add - Remove/system tool.

Next - To be able to see your linux-files from windowes you'd need aditional software like this:

[http://www.it.fht-esslingen.de/~zimmerma/software/ltools/ltools.html](http://www.it.fht-esslingen.de/~zimmerma/software/ltools/ltools.html)

Enjoy

---

### Post by Taliskerd on 2007-06-25
I solved this by allowing samba when I installed Ubuntu, after that, all I need is a windows account with enough rights to the filesystem. 
Using the Administrator account is Bad, so don't use it unless you have to -like when you check if any rights work as they should...
Sometimes (and I've never understood why this isn't a must) the windows account you use need to have a password or the connection will fail.

---

### Post by novinthen on 2007-06-25
OK jimmy. Will try it now and post the outcome. thanks to taliskerd too.

---

