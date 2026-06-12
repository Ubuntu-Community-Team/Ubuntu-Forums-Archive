---
title: "How to delete all subdirs with a given name?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by pompiuses on 2007-03-01
I want to delete all subdirectories called .svn (with content). How can I do that?

I've been reading the rm manual, but can't see subdirectories mentioned anywhere there.

Thanks!

---

### Post by Stemp on 2007-03-01
rm -r .svn

---

### Post by bruenig on 2007-03-01
Are you saying something like
rm -rf /directory/*.svn

---

### Post by pompiuses on 2007-03-01
Perhaps I didn't express myself clear enough:

I want to delete the folder .svn in **all** subdirectories in a given directory.

---

### Post by dannyboy79 on 2007-03-01
sudo find / -name "*.svn" > folders_to_delete        (note: change the /   to whatever directory it is you want to search. ie sudo find /home/fred/blah/)

this will create a file and it will put all files and folders that were found which contained the string **anything**.svn. then what you do is open that file and review it to make sure that it only contains the directories that you want to delete. anything you find in the file that you don't want deleted, get rid of it. then save the file.

now you do this

sudo rm -rf < folders_to_delete

or maybe you could do 

sudo cat folders_to_delete>/dev/null/ 

I am not sure on this last one though! the whole point of my way, is that you won't end up deleting something that you don't want, you gte to review what you'll be deleting first.

I am pretty sure this would work. here is the link for input/ouput redirection in linux. good luck

you might even be able to use the ls -la command using your directory where you said all these .svn direcrtories are. then redirect that to a file, then when you look at that file, you'll see at the begining of each line, which ones are directories "d" and which ones are file, "-".

examples:

drwxr-xr-x 13 xxxx xxxxxx4096 2007-02-09 19:32 500gb-ext3
-rw-r--r--  1 xxxx  xxxxxx     654 2006-09-29 22:05 automatix.log

i tried this:
ls -la | grep ".gn" > test 

and when I used cat for the file test, sure enough it showed me this:

drwxr-xr-x  4 xxxxxxxx4096 2007-02-09 19:11 .gnome
drwx------ 13 xxxxxxx4096 2007-02-21 06:07 .gnome2
drwx------  2 xxxxxxxx4096 2006-09-11 18:20 .gnome2_private
drwx------  2 xxxxxx4096 2007-02-28 11:22 .gnupg
-rw-r--r--  1 xxxxxx88 2006-09-11 18:20 .gtkrc-1.2-gnome2    **it's weird that it found this line as it doesn't match .gn?**

so then I believe you could remove all the garbage in the begining of each line like this:

.gnome
.gnome2
.gnome2_private
.gnupg

then save the file caslled test, and then use the input redirection to delete all directories.

sudo rm -rf < test


**_*SORRY, I thought this would work but it's not*_**, at least not right now while I tried testing it. The input redirection isn't working with the rm -rf or rmdir? not sure why?





**note: I have x'd out my username and group name.**

---

### Post by pompiuses on 2007-03-01
Creating the folders_to_delete file went fine, but this line doesn't work:
sudo rm -rf < folders_to_delete

Nothing gets deleted even though there are many dirs in folders_to_delete.

---

### Post by obelisk on 2007-03-01
rm -rf /directory/folders_to_delete should work shouldn't need the <

---

### Post by kolach on 2007-03-01
You can do it with **find** command

For example you have a **Habba-Habba** directory with all that .svn subdirectories
inside.

The command will be:

find Habba-Habba/ -name .svn -exec rm -r '{}' \;

See **man find** for details

---

### Post by dannyboy79 on 2007-03-01
***_THIS IS IT. EVEN TESTED IT, IT WORKS._***

ok, i got it figured out. you can use the output redirection, using the find way, NOT the ls -la way. you can use the ls -la to find out if something is a file or a directory if need be but after you have created a file which contains all the locations you want deleted. Example:

/home/daniel/.gnome-delete
/home/daniel/.gnome2-delete
/home/daniel/.gnome2_private-delete
/home/daniel/.gnupg-delete

then you simply run this command:

cat test | xargs sudo /bin/rm -r

assuming your filename is test. so to delete we use the pipe command with the xargs option. pretty sweet!!!!

---

### Post by dannyboy79 on 2007-03-01
> **kolach said:**
> You can do it with **find** command

For example you have a **Habba-Habba** directory with all that .svn subdirectories
inside.

The command will be:

find Habba-Habba/ -name .svn -exec rm -r '{}' \;

See **man find** for details


sure but then what if it grabs a directory or file he didn't want it to???? thats the whole reason I am redirecting the output to a file first, for review. thanks though.

---

### Post by dannyboy79 on 2007-03-01
> **obelisk said:**
> rm -rf /directory/folders_to_delete should work shouldn't need the <

wrong, that would simply delete the file he just created.

---

