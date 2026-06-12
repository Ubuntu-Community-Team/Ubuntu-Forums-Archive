---
title: "How to Install .run/game in Ubuntu."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-07-10
Hey ALl
I donwloaded Savage from Official Site.. Now Plz tell me how to install it using the .run file :confused:

Peas :guitar:

---

### Post by k33bz on 2007-07-10
i know there is 2 ways to do it. The first one, the best way to do it, is in the terminal, forgive me since i do not remember the commad, but i think you can get it here.  [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

the secodn way, the easiset, is to right click on the .run file, select properites, then check to run as program.

---

### Post by jordanmthomas on 2007-07-10
first, cd to the directory you downloaded it to:
```
cd ~/Desktop
``` most likely
Then, make it executable:
```
chmod +x NAMEOFFILE.run
```
then, run it.
```
./NAMEOFFILE.run
```
if you get permissions errors, prepend sudo to that:
```
sudo ./NAMEOFFILE.run
```

Hope this helps.

---

### Post by hammad1337 on 2007-07-21
right-click and select "open with other application" >click on "use custom command" and type "sh" > then press enter.
done.

---

