---
title: "how to copy/move a bunch of files using find command?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by joechiang on 2008-02-27
due to invalid arguments and cp/mv limitations

i think there is a way to use find commands to copy a large amount of files into another folder

something like

$ find /home/john/ *.* -exec cp /media/disk/john

but i can't find a good example on the internet

---

### Post by ryanhaigh on 2008-02-27
[http://ubuntuforums.org/showthread.php?p=4400446#post4400446](http://ubuntuforums.org/showthread.php?p=4400446#post4400446)

---

### Post by joechiang on 2008-02-27
thank you very much that's exactly what i need

but i got a problem, because when i cp 
it will copy all the files to another folder without directories

is there any way to keep the file structure & directory? using find command?

---

### Post by hyper_ch on 2008-02-27
```

cp -R

```

---

### Post by ryanhaigh on 2008-02-27
This will do the trick, it will copy all jpgs into the same directory structure at the destination ignoring non jpgs. Directories will only be recreated if they contain a jpg or their subdirectories contain a jpg.

```
find ./ -iname '*.jpg' -exec cp -b --parents {} ~/Desktop/ \;
```

---

### Post by joechiang on 2008-02-27
thank you guys very much!
it works perfect

but i got a single database file that's over 6GB so when i copying it over!

it only copied 4GB of that files over

is there a way around that?

thank you all for your time thank you thank you~

---

### Post by ryanhaigh on 2008-02-27
Im guessing you are copying it to a FAT32 filesystem. If this in fact the case then I'm afraid it isn't possible as the 4GB limit is assoicated with the filesystem.

If windows compatibility is the issue you will need to use ntfs or ext3 with the driver from fs-driver.org (read the faq if it is a usb/removable drive).

---

### Post by joechiang on 2008-02-27
oh my god you are so right about that..
now i think im dumb.. coz i knew it!! i knew u can't have files more than 4GB on fat32

god thank you very much again

---

