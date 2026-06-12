---
title: "download, file creation, command line"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by boddo on 2007-02-06
Hi, I've been dual-booting with Ubuntu Edgy for about a week.  

There is a primitive word processor program called darkroom that I really enjoy using in Windows (similar to writeroom on the Mac).  
There is a version that works in Ubuntu using Java!

However, the website ([http://www.codealchemists.com/jdarkroom](http://www.codealchemists.com/jdarkroom)) says the following:

# Ubuntu Linux users: JDarkRoom will work on Ubuntu with Java 1.6. You will need to add the following line to your conf/jdarkroom.properties file (create one if it doesn't exist):

suppress.native.look.and.feel=true

Like I said, I am new, and this will be the first program I work with not available from the software repositories.

How do I create a conf...properties file, and how do I add the above line to it?

(there may also be an issue with Java, as I now have 1.5, but I may try an earlier version of jdarkroom if it doesn't work). 

Thanks.

---

### Post by firefly2442 on 2007-02-06
I would navigate to the directory where you installed Darkroom and see if there is a "conf" directory.  Then just open up the needed file with the text editor (note, you might need to open it as a user that has WRITE permissions if you want to save changes).

I looked at the screenshots for Darkroom and it looks similar to Nano.  If you open up the terminal, just type "nano" and see if you like it.  :)

If you don't have Nano, run this to install it:

"sudo apt-get install nano"

---

