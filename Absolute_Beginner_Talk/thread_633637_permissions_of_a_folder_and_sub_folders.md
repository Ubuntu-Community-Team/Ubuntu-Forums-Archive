---
title: "permissions of a folder and sub folders"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by tlivingd on 2007-12-06
alright,  under vista in a ext2 drive I copied a whole bunch of music files,  however i accidentally created the music folder in a system file under vista accidently obviously it's able to do this.   under vista i copied the file into my /home/tlivingd/Music folder.  however now all the files are unavailable to view unless I'm root because it brought over the permissions of the system folder. i have about 40gb in this music folder and it's too big to copy into another directory then delete not to mention i can't see them unless i'm root.

i'm trying to use the command```
sudo chmod -r 777 /home/tlivingd/Music
```

but i keep getting a "chmod: cannot access `777': No such file or directory"


can anyone help me on what i maybe doing wrong?

thanks
-nate

---

### Post by bodhi.zazen on 2007-12-06
sudo chmod -R 777 /home/tlivingd/Music

---

### Post by Vadi on 2007-12-06
I know you can do this easily in Konqueror - launch it as root, select properties of a folder, change the owner to yourself, and check off the "recursive" option so it does the changes to everything inside those folders too.

I'm not sure how to do this in Nautilus though.

Try doing "sudo su", and then the chmod -r ?

---

