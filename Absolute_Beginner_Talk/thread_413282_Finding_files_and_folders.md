---
title: "Finding files and folders"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-19
How would I find the location of a program, file or folder? I've used the search feature in File Browser but it only seems to work if you already know the location like /usr/bin. Some command or program that'll tell me the exact file address from scratch. Thanks.

---

### Post by wormser on 2007-04-19
There are a couple of ways.  I got the following commands from [here]("http://www.computerhope.com/unix/ufind.htm")

    find -name 'mypage.htm'

    In the above command the system would search for any file named mypage.htm in the current directory and any subdirectory.

    find / -name 'mypage.htm'

    In the above example the system would search for any file named mypage.htm on the root and all subdirectories from the root.

    find -name 'file*'

    In the above example the system would search for any file beginning with file in the current directory and any subdirectory.

    find -name '*' -size +1000k

    In the above example the system would search for any file that is larger then 1000k. 

Another method is locate.  to update the database before a search:

   sudo updatedb&
   
then
  
   locate filename

The & symbol behind a command lets it run in the background so you do other commands.

---

### Post by Wim Sturkenboom on 2007-04-19
And another one is the* whereis* command

---

