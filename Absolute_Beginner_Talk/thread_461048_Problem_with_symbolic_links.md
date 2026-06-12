---
title: "Problem with symbolic links"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by teamanx on 2007-06-01
Hello. I am trying ubuntu, in order to replace Windows in my network. I have noticed that, when you  want to delete a symbolic link, Nautilus deletes the destination, not the link itself. Actually, I have found no way of deleting a link without deleting first the destination (I mean, using Nautilus; i know i can use "rm" or "unlink" on the command line).

Is there any way to change this behavior? It is very dangerous, especially for people used to Windows.

Thanks in advance!

---

### Post by Sparkster185 on 2007-06-01
Are you creating soft or hard links?  I believe if you don't create "soft" links, rm will follow the link and delete the target, too.

Try it from the command line.  the "-s" option to "ln" tells it to make a soft link.  Try creating a test with a soft link, then using "rm" and a hard link, then use "rm" on it.

---

### Post by teamanx on 2007-06-02
I have noticed the problem is only when I create symbolic links between different filesytems (i.e., I create a link on my desktop to a windows shared folder mounted with smbmount), and try to send it to the trash with Nautilus. Then I got an error message. The solution I have found is enabling the command to fully erase the files in the Nautilus preferences, and now I can delete those links.

Ooops, it was easier than I thought! :oops: Well, this proves that i am an Absolute Beginner.

Thanks to all.

---

