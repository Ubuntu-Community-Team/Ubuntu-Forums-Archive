---
title: "vidoes won't delete"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-12-19
I have these two movie clips I downloaded ages ages ago. I had deleted them and emptied trash, but every now and then they pop up on my desktop after I start or retart the computer.
Each time I drag them into the trash bin and then empty the trash. But they show up again after a while. I'm not sure how to permanently delete them. I'm using Gutsy.
Also, my video folder says I have six or seven items, but doesn't display any names. so I can't delete whatever is in in the folder.
Pls. help. Thanks.

---

### Post by fs3rp4 on 2007-12-19
Delete this files as root. Like this:


sudo rm -rfv file.avi

---

### Post by kernel tom on 2007-12-19
from the teminal

rm ~/Desktop/filename.extension

if you want to delete an entire folder

rm -rf ~/folderpath/foldername   (-rf stands for recursive/forced)

if you want to view what's in a folder

cd ~/folderpath/foldername
ls -a

AND only use 'sudo' before hand if you do not have the rights to the file.

---

### Post by Tadock on 2007-12-19
Have you tried to rm -rf the files from the terminal?

---

### Post by rickycodie on 2007-12-19
maybe you could remove them as root. 

rm ~/Desktop/filename.extension

or

sudo rm -rfv file.avi

or try pressing shift+delete

that might work too.

---

### Post by urvaksh on 2007-12-19
Thanks guys. I'll give it a shot.

---

