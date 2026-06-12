---
title: "Help reinstalling"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by TheBuntu on 2007-03-30
Hey guys, 

I have a problem with Ubuntu. I've managed to screw it up enough that I can't really install anything because everything is corrupt (I kind of knew what I was doing, so its alright). Anyway, when I go to reinstall, I format the partition with all the system files, and leave the partition with my personal stuff (movies, pictures, documents) untouched. 

Then when I go to boot up for the first time, all the setting are reset, but all the same programs are installed and the same files corrupt (almost like I hadn't reinstalled).


Does anyone know what could be the problem? :confused: :confused:  How do I do a true reinstall but leave my personal partition untouched?


Thanks!!

---

### Post by etank on 2007-03-30
In your /home directory there are hidden files and folders. Do a ```
ls -a
```or hit Ctrl+h while in your home directory in nautilus so see what I mean. Many applications will store config files in these directories and when you reinstall those settings are still there. If you know which application is giving you problems then you can try deleting the folder that goes with it. Then next time you run the app it will recreate the folder for you with a clean config.

---

