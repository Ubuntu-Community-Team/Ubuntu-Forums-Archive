---
title: "Navigation question"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-12-26
Ok, this should be really simple to answer but here it is.
How do I navigate into a directory that has a space in it?  eg My Documents
cd /home/user/My Documents/ does not work, and I've tried some other ways.  How can I navigate into it short of changing the name of the folder?

---

### Post by candtalan on 2007-12-26
> **OlyPerson said:**
> Ok, this should be really simple to answer but here it is.
How do I navigate into a directory that has a space in it?  eg My Documents
cd /home/user/My Documents/ does not work, and I've tried some other ways.  How can I navigate into it short of changing the name of the folder?

probably by using quotes to surround the string - not sure if they would be single or double quotes, but that is what I would try
cd /home/user/"My Documents"/

---

### Post by LaRoza on 2007-12-26
> **candtalan said:**
> probably by using quotes to surround the string - not sure if they would be single or double quotes, but that is what I would try
cd /home/user/"My Documents"/

Quote the whole path.

```

cd "/home/user/look spaces what a bad idea"

```

You can also escape the space with a backslash:

```

cd /home/user/look\ spaces\ what\ a\ bad\ idea

```

Or you can use the auto completion to fill it in (type a little then press tab)

---

### Post by Dakine858 on 2007-12-26
Re-check the path of the folder you are trying to navigate. As a quick reminder, when using the terminal, you have to type and spell everything perfectly while following the terminals' "case sensative" requirement which means that if you are trying to find a folder called "new folder" located in the root folder, you have to type "/root/new folder/"  NOT "/root/New Folder/"  As far as a space in the name of the folder, you still put the space into the terminal line exactly as the name of the folder is written. Also, I noticed the line you typed in had /user/ as one of the directories as part of the path, unless you changed any of the default names after installing Ubuntu then the correct directory is /usr/  so like I said, everything going into the terminal needs to be EXACT!!! If you are still having issues, tell me the name of the folder, where you think its located (if not on the desktop, assuming you downloaded or extracted it) and ill tell you what the path should read.

---

