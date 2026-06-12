---
title: "Konqueror could not and still cannot find files. =/"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-12
My issue: Kfind is unable to find any files at all. This issue occurs when searching for pictures, documents, mp3s, etc.,

I first encountered this problem when I was using Ubuntu Dapper which is v6.06LTS. Kfind was never able to find any files, not even if I created a file in Desktop.

However, due to certain nasty issues on Dapper, I did a clean installation of Feisty which has now been patched from beta to final. Again, I encountered this issue within Kfind. 

uname --a : Linux lucifiel 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux


What I did:

1) I searched using "All files and folders". No results. 

2) When the above failed to produce any results, I switched to using a more specific search term. That is, when searching for images like .jpg, etc.,  I'd use a term like "All images" and when searching for mp3s, "All sounds". Again, I received no results, not even when trying to search for different files like 250.png, me1.jpg , meow1.png, she_rocks.mp3, etc.

3) I tried again and again with files in different directories(with or without spacing, hidden or not hidden, in different partitions, etc.) but still, I received no search results.

4) Then, I decided to try searching for files using Nautilus File Manager and it was able to find the files. The same goes for "Search for files"(another Search function in Ubuntu).

5) I actually reinstalled Konqueror, Kfind, kde-base and many other kde related packages but this issue still remained.

6) Further investigating on this issue yields:

i) Using "All files" as a search term doesn't work either.

ii) Kfind can actually find a file if I input the exact filename like "mew.jpg"  Thus, this gives me "mew.jpg" in the search results.

ii) Kfind can find a folder only if I input the exact folder name. Like "Food" gives me the folder "Food" .


Below are 3 screenshots. One shows the search results in Kfind, another shows the search results in Nautilus and the last shows the search results from "Search for files".

Kfind search results
[http://img258.imageshack.us/my.php?image=lucifielkonvresults1bk7.png](http://img258.imageshack.us/my.php?image=lucifielkonvresults1bk7.png)

Nautilus search results
[http://img253.imageshack.us/my.php?image=lucifielnautilussearchjp6.png](http://img253.imageshack.us/my.php?image=lucifielnautilussearchjp6.png)

"Search for files" results
[http://img102.imageshack.us/my.php?image=lucifielsearchforfilesij5.png](http://img102.imageshack.us/my.php?image=lucifielsearchforfilesij5.png)

---

### Post by Lucifiel on 2007-05-12
Bump! :)

---

### Post by ubromtoo on 2007-05-12
am having a sort of similar problem with Dapper : when I tried to save a text file,

 a box popped up saying that the file by that particular name already exists.

 However, when I searched for that file, it was not found !?  this has happened a

couple of times.  Of course it is easy enough to simply change the name of the 

file I wish to save, and then save it, but that does not solve the deeper problem

of being unable to find a specific file which I am told does indeed exist.

                               sign me,  Noob in need o' help:-k

---

