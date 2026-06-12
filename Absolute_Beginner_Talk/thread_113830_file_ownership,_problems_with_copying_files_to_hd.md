---
title: "file ownership, problems with copying files to hd"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Moucxs on 2006-01-07
Hello , ime quite new to linux. 

i was trying to copy a set of files to the baseq folder on my file system.
while trying i walked into a difficulty, i was not able to do so because of file ownership.

when i took a look in the config i saw that root was owner of the file.

i tried logging in as root but that didnt worked,

i would like to modify the rights of ownership but i dont know how to do that in the console ( root console,) 

if someone knows the sollution , it will be a good addition in my learing proces of linux :) 

greetz

---

### Post by lha on 2006-01-07
You can do
```
sudo chown moucxs:moucxs /my_folder
```
to make you the owner of my_folder. (If your username is moucxs.)

Or you can give everyone full access to /my_folder with
```
sudo chmod a+rwx /my_folder
```.

---

### Post by Moucxs on 2006-01-07
intresting , i didnt knew that.
 
works :)

---

