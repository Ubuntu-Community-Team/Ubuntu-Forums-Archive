---
title: "When I move stuff to the trash..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-23
...it just gets auto-deleted. I don't have to empty the trash can at all. It just never appears there after sending it to the trash.

why?

---

### Post by kilroy423 on 2007-05-23
All the trash can is is a link to the /home/your user name/.Trash try looking there

dan

---

### Post by Roasted on 2007-05-23
Right. But my actual icon in the lower right corner never registers that anything is in it. If I open the trash can, I see the stuff there. If I go to file-empty trash, it empties. But I can't right click the icon and hit empty trash. The option is grayed out. Wonder what's up?

---

### Post by kilroy423 on 2007-05-24
Huh...maybe you don't own the files in the trash can?  Try deleteing everything through the .trash folder as root

dan

---

### Post by ryanVickers on 2007-05-24
yes, if there are root files in there, they won't show up.  I found my aplet rendomly stopped working a few days ago, but it's back on now.  As long as the files just go to /home/user/.Trash, it should be OK, you can clear them from there.  Just to let you know, If your new to this, every divice that's not your main HD, like an external drive, mp3 player, etc. has it's own trash folders.  Check on these devices under %mountpoint%/.Trash-username.

root has it's own trash in it's home at /root/.Trash.  Any files deleted as root will go here, not your trash.  same with divices; %mountpoint%/.Trash-root

of course you need to be root to view/modify these files

---

### Post by sambody on 2007-06-02
I had a similar problem with the trash can: all files were deleted without going to the trash can (or so I thought!). What was even worse: just opening the trash can, there was no visible file, and Nautilus was frozen, I could not close the trash can without doing Force quit.

When opening the folder (.Trash) in a console, typing "ls" to list the files, I could see my files. So I removed them as root, including the directories, like this: "sudo rm * -r".
And it worked. Now the trash can is working normally again. 
Thanks ryanVickers for the tip about clearing the files.

---

