---
title: "Update Problem: Size Mismatch"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Dougga on 2007-04-13
I've tried to update a new installation of Ubuntu and get hundreds of errors stating a size mismatch on the installation files.  I have two problems:

1) I get the error only after the download and an installation attempt.  Why can't this check be made much earlier so I don't waste so much time attempting to install files that will not work.

2) No amount of "apt-get update" or "check" commands will correct this issue.  

The number of updates required is staggering so there seems to be a big problem somewhere.

Thanks for any help

---

### Post by xopher on 2007-04-13
So the files are downloaded over and over again?

Have you tried using a different update manager? Which should matter really..

You might just have problems with your connection. Another thing to try, is to switch to another mirror, the one closest to you is often the best choice.

---

### Post by Dougga on 2007-04-15
>>So the files are downloaded over and over again?

Yes, the files are downloaded each time.  Only after this does it inform me that the files are inappropriate due to 'size mismatch'.

>>Have you tried using a different update manager? Which should matter really..
What options do you suggest?  

>>You might just have problems with your connection. Another thing to try, is to switch to another mirror, the one closest to you is often the best choice.

I've tried with many different mirrors... close and far.  The one at Oregon State University is close and fast, the default US one is adequately fast... all have the same problem.  I currently have 232 updates required on my machine which is ridiculous in anything but a temporary situation.  I fear my relationship with Ubuntu will be thus.

---

### Post by Dougga on 2007-04-15
Running things from the command line I see that things were humming along smoothly when it got hung on a single line.  While it appeared to wait, it indicated that it was waiting for headers.  AFter a couple of minutes hundreds of errors ensued.  I generally got two types of errors:

1)  The "Bad Request" seen below
2)  Most of the errors were the Size Mismatch errors I've written about.


Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main mscompress 0.3-2ubuntu1                                                    
  400 Bad Request [IP: 91.189.88.31 80]
Get:132 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main foomatic-db 20070327-0ubuntu1 [577kB]                                  

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lsb/lsb-base_3.1-22ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lsb/lsb-base_3.1-22ubuntu3_all.deb)  Size mismatch



173 Updates needed after 1 run with apt-get

---

### Post by Dougga on 2007-04-15
Here's what it looks like when it hangs:
Get:124 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gcalctool 5.9.14-0ubuntu1 [710kB]                                      
Get:125 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gdm 2.18.1-0ubuntu1 [1863kB]                                           
Get:126 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gnome-session 2.18.0-0ubuntu3 [290kB]                                  
3% [Waiting for headers]       


It's interesting that this is 2^7 - 2.  I wonder if this is a pattern.


it seems the command line limps along but the Synaptic package manager just makes a mess of it.

---

### Post by Dougga on 2007-04-16
After over a dozen runs of the command line apt-get function, my system is finally up to date.

Unless I'm missing something important, it seems that this functionality is critically flawed.

What a mess...

---

### Post by Dougga on 2007-04-16
Oh yes, the above test was done using the default US repository.

---

