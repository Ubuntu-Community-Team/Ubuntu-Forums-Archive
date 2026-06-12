---
title: "How do i open VLC music player?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by d1111 on 2008-03-04
I have converted to Linux, and am hitting a few stmubling blocks along the way,howveer i am enjoying Linux very much!
I have down loaded VLC music player as i want to play my music files...Mp3s
When i click(right)and click open,it takes me to all the file folders? How to i open this program to run the music player?
I am using xubuntu.
Thank you
David

---

### Post by FrozenFox on 2008-03-04
I'm not exactly sure where you're clicking, as we can't see what you are doing. However, I'm on the assumption that you opened the folder .vlc. Program settings for your current user are saved under /home/yourname/.Program (notice the dot), and I'm guessing you went into the vlc folder?

If you want to run vlc, just open a terminal (xterm for instance. i dont know what it is in xfce ie xubuntu...) and type vlc. Or create a shortcut on the desktop with the command vlc.

---

### Post by philinux on 2008-03-04
Top left click applications. It's probably in the multimedia menu.

---

### Post by mrfr0g on 2008-03-04
It sounds like your trying to right click on a folder, and have VLC play the entire contents of that folder like winamp does. To do that,

Right click on any folder and click "Properties"
Under the "Open With" tab, click on the "+ Add" button.

The Add Application window ill pop up.
Click on, "Use a custom command"

Type in the box,

vlc

Then click "Add"

Close the Properties window.

Now when you right click on a folder, you will have the option to, "Open with VLC Media Player"

---

