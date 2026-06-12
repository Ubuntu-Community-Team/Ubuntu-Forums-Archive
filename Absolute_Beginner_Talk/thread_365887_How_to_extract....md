---
title: "How to extract..."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by David_UK on 2007-02-20
Erm, I'm following some instructions on installing Ndiswrapper on 6.06.  I downloaded the .zip file using windows and then copied the archive over to linux. It's on my desktop at the moment.
I'm told to type:
> tar -zxvf ndiswrapper-1.37.tar.gz
to extract it, but I get an error to say the file cannot be found.
Can you tell me where to move it to so it can be found, or what to type to point linux to where it is?
Thanks.

---

### Post by Maestro23 on 2007-02-20
> **David_UK said:**
> Erm, I'm following some instructions on installing Ndiswrapper on 6.06.  I downloaded the .zip file using windows and then copied the archive over to linux. It's on my desktop at the moment.
I'm told to type:

to extract it, but I get an error to say the file cannot be found.
Can you tell me where to move it to so it can be found, or what to type to point linux to where it is?
Thanks.

It's on your Desktop?

cd /home/username/Desktop

---

### Post by David_UK on 2007-02-20
So after I've typed that, I then use my original command to extract?
Thanks

---

### Post by Maestro23 on 2007-02-20
> **David_UK said:**
> So after I've typed that, I then use my original command to extract?
Thanks

When you get to your Desktop directory, type "ls"(lower case L) and it if your file is there, you should see it.  Then just extract it with your tar command.

---

### Post by David_UK on 2007-02-20
Maestro23

Thanks!

---

### Post by mcduck on 2007-02-20
yes. (Of course you could just right-click the file on your desktop and select 'Extract here' ;))

---

### Post by jvc26 on 2007-02-20
Also from terminal by default you are in the /home/user directory and hence you can just use cd Desktop to change to your desktop.
Il

---

### Post by aktiwers on 2007-02-20
You could also do it like you would on windows. Double-click the file, and drag/drop it on your desktop.

---

