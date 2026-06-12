---
title: "Lost file...Please Help"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by squidward_tentacels on 2007-02-12
Hello,
I just installed mIRC via wine on my 6.06 ubuntu. I downloaded a large file via dcc, However, I failed to change the "save to" directory, so the file went to; C:\Program Files\MIRC\Download, in the fake windows file system, however when I attempt to access this area through mIRC, by clicking on the recived files button, I just get a beep, and search does not turn up the file either, I dont think search can look in the "fake windows" filesystem created by wine...Um, if anyone could tell me how to access the the wine directory? and retrieve my file, It will be greatly appreciated. Thanks:)

---

### Post by highneko on 2007-02-12
It should download into the hidden wine directory

cd ~/.wine
# or:
cd /home/username/.wine
# and if you know the name of the file:
find ~/wine -name '*filename*'

have fun
-highneko

---

### Post by squidward_tentacels on 2007-02-12
Thanks for the quick reply:) Ive tried what you suggested, but i seem to be having issues, this is where I keep getting stuck;

pl4nkt0n@localhost:~$ cd /home/pl4nkt0n/.wine
[email]pl4nkt0n@localhost:~/.wine[/email]$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
[email]pl4nkt0n@localhost:~/.wine[/email]$ cd drive_c/
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$ ls
Program Files  windows
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$ cd Program_Files
bash: cd: Program_Files: No such file or directory
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$

Any other suggestions:(  (I tried find ~/wine -name '*filename*') substituting the name of my file, of course, no luck. Is there a way I can graphically browse? Like a way to view contents from "sudo nautilus" ? Im trying to recover from a windows addiction, lol

---

### Post by aktiwers on 2007-02-12
You can go there with nautilus as well..  just open your home folder and press CTRL+H..  Then scroll down to the .wine folder. then you can look for your self.

Any reason you run a Windows IRC client? There are lots of good ones for Linux.

---

### Post by aktiwers on 2007-02-12
Oh yes..  and when there is a space in the name.. its 
cd "/folder with space/somethingmore"

Remember the ""

---

### Post by highneko on 2007-02-12
> **squidward_tentacels said:**
> Thanks for the quick reply:) Ive tried what you suggested, but i seem to be having issues, this is where I keep getting stuck;

pl4nkt0n@localhost:~$ cd /home/pl4nkt0n/.wine
[email]pl4nkt0n@localhost:~/.wine[/email]$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
[email]pl4nkt0n@localhost:~/.wine[/email]$ cd drive_c/
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$ ls
Program Files  windows
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$ cd Program_Files
bash: cd: Program_Files: No such file or directory
[email]pl4nkt0n@localhost:~/.wine[/email]/drive_c$

Any other suggestions:(  (I tried find ~/wine -name '*filename*') substituting the name of my file, of course, no luck. Is there a way I can graphically browse? Like a way to view contents from "sudo nautilus" ? Im trying to recover from a windows addiction, lol
Yea, sorry. I should have suggested nautilus or something. Use this:
nautilus ~/.wine
# If you use kde:
konqueror ~/.wine
# And btw, the reason you couldn't cd into the Program Files directory was because you weren't using quotes:
cd "/home/pl4nkt0n/.wine/drive_c/Program Files"

---

### Post by squidward_tentacels on 2007-02-12
Thanks!:) :) :) :)  That did it!

---

