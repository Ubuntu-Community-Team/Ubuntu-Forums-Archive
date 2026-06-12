---
title: "can't read folders in os x partition"
date: 2009-06-21
forum: Apple Hardware Users
---

### Post by hananias on 2009-06-21
I`m dual booting Ubuntu Jaunty with osx. I can mount the osx drive, and open the user folders, but when I get to the user (home) folder in os x ...all the folders (music, movies, pictures, etc.) are locked!! Says "You do not have the permissions necessary to view the contents of "Music"."
I went to my osx partition, and I went to the folder info settings, and change the permission for "everyone" to "read and write" I also tried "read" permission...but nothing works!!! I even have those folders as shared in my network. I can only read them if I use nautilus as **root**, but I still **can`t** copy the files!  
This is crazy!! 

So then, I took an external drive, formatted to fat32 (later on, I tried to format to nfts, ext 2,3,4...nothing works)...Ubuntu read it fine, I could copy and back up some files in it. But I went to osx partition, copy some files from there to the ext drive. Now in Ubuntu I can`t access the back up files in the ext drive. (No permissions) I can`t read my back up files!!! Isn`t that ironic, I back up my files...but they end up getting locked up!!

Any help on this 2 issues would really be appreciated. I really just want os x and ubuntu to play nice! After all they are both against windows, on the same unix side. (I know they are not the same...still, it`s not windows).

Please help!

---

### Post by Richardcavell on 2009-06-21
I think the problem is ownership and group.  Go into OS X and change the ownership of the files with chown.

This happens to me too.  I would have thought that it was the proper behaviour for any UNIX flavour to not let you into another UNIX's user folders.

Richard

---

