---
title: "Hellanzb / file permissions absoloute beginner"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-08-18
Firstly, hello to one and all.

Let me quickly say who i am and where i'm at...

I'm a long term windows user, 95-98 and xp. I've done a little programming, but way, way back eg.cobol,pascal;  and am, i suppose, not too unaquianted with a console, at least not afraid to use one;).

With all that M-soft has been doing the last months i've decided to try something else, LINUX seems to be exactly what i'm looking for.  My first step has been to set up a dual boot with win xp pro and LINUX together on my laptop.  A quick look at Suse 10.1 freaked me, way too many options and no working wireless sent me scurrying for an alternative...Ubuntu! 

I've been using Ubuntu for approximately one month, Gnome desktop, everything installed a treat (no issues with wireless or graphics). 
Got my ATI card installed correctly and have xgl up and running etc.
I've managed with the aid of these forums and "google" to resolve all my problems to date and i'm having fun!

Now, to the crux of the matter.
I''m a usernet junky, Films (dvd,divx,xvid) and music.
So i've been trying to find a LINUX equivelent for "newsleecher-Win' xp".
I found Hellanzb, which seems to fit the bill.
After installing yesterday, i finally got it to work today.  The config file took a little bit of "head scratching" but it works.
I found i could only install the prog as Root, this has left me with a file structure that has only Root privileges...
eg.all the working files can only be changed by root.
I can't add a "NZB" file to the "NZB" folder without being logged in as Root - "sudo nautilus" and then copying the nzb.file
I've tried changing the folder privelages using...
"sudo chmod -r 0777 /home/steve/hellanzb work file" (which has worked on other folders, but get the following error....
"chmod: cannot access `/home/steve/hellanzb work file': No such file or directory"

Is it the command format that i've got wrong (chmod -r 0777 - to change privelages for the whole folder) or is it a problem with the folder name?
eg hellanzb(space)work(space)file.

At the moment i can use hellanzb, it works fine, but only as root.  How do i change this please?

Again, i'm loving it here (in LINUX/Ubuntu land) but have the feeling i've got loads to learn...;) 

Thanx in advance for any help that you can offer.
Steve (Stoer).

---

### Post by Ambimom on 2006-08-18
Have you tried Grabit under wine? It works.  The only thing it won't do is NZB files.  As far as I know NZB files don't work under Gnome....yet for any news reader.

---

### Post by huygens on 2006-08-18
Hi,

If your directory contains spaces, there is two ways (I think) to use it under the command line. You need to "backslash" it or to put it inside double quotes, so your command line should be something like:
```
sudo chmod -R 0777 /home/steve/hellanzb\ work\ file
```or```
sudo chmod -R 0777 "/home/steve/hellanzb work file"
```
(I do not know if -r is the same thing as -R, but for what you want, I am usually using the second)

Huygens

---

### Post by bluefrog on 2006-08-18
Spaces are not liked very much.

best thing thing would be to rename the folder without using space (and try to kee this habit in the future) otherwise adding quotes before and after the name should do the trick. You also have the possibility to add / (or \)before the spaces (sry not on linux right now) to make the path understood. otherwise the command you were issuing is correct.

You can also change the ownership of the folder so that you don't have to sudo everytime.

sudo chown steve /home/steve/hellanzb

James

---

### Post by Zimmer on 2006-08-18
I think it is the spaces in the filename that cause the problem.

I saw a thread last night 

[http://ubuntuforums.org/showthread.php?t=202605&page=2&highlight=space](http://ubuntuforums.org/showthread.php?t=202605&page=2&highlight=space)

which relates to accessing filenames with spaces using Samba.

Perhaps if you enclose the complete file location in quotes 
with the chmod  command

chmod -r 0777 "/home/steve/hellanzb work file"  or try the other method mentioned in the post...


Good luck

Zimmer

---

### Post by stoer on 2006-08-18
Thanks everybody for replying and for the help.

"Have you tried Grabit under wine? It works. The only thing it won't do is NZB files. As far as I know NZB files don't work under Gnome....yet for any news reader."

I'm using Hellanzb in gnome right now, using NZB files, it works.  As for Grabit, you said it all - no NZB and no SuperSearch or its pay for it.


1) "sudo chmod -R 0777 /home/steve/hellanzb\ work\ file"

Tried but kept getting, "file doen't exist"

2) " sudo chmod -R 0777 "/home/steve/hellanzb work file"  "

Worked, or at least changed the folder permissions but not the folder content permissions.


"sudo chown steve /home/steve/hellanzb/******"

Also works. Again only changed the ownership of the folder, the contents remained the property of Root.


I've renamed my folders, No more spaces! Too many years working with "long file names" i'm afraid.  Ialso used ....
"sudo chown steve /home/steve/hellanzb/******"
on each of the content files and successfully changed each from Root to User.  So thanks again for the ideas and tips, very much appreciated.

Can anybody explain what the difference between 

sudo chmod -R 0777
and
sudo chown <user>
is? and why one might be more "correct" than the other?

I'm guessing it's chmod -R 0777 opens access to "everybody" whilest chown <user> makes it only accessable to the  named user, making chown more correct???

---

### Post by huygens on 2006-08-19
> **stoer said:**
> Can anybody explain what the difference between 
sudo chmod -R 0777
and
sudo chown <user>
is? and why one might be more "correct" than the other?

I'm guessing it's chmod -R 0777 opens access to "everybody" whilest chown <user> makes it only accessable to the  named user, making chown more correct???

Good guess. :)
'chmod -R' means you are going to change recursively (so the directory and all of its content) the access rights. And 0777 means you give read, write and executable access to everyone.
'chown <user>' change the owner of the file(s) to the <user>. If you do a 'chmod -R 0700' and 'chown <myself>' on the same file, then only you can read and modify the files. :) The rest of the *world* cannot access the files.

Huygens

---

### Post by stoer on 2006-08-19
> **huygens said:**
> Good guess. :)
'chmod -R' means you are going to change recursively (so the directory and all of its content) the access rights. And 0777 means you give read, write and executable access to everyone.
'chown <user>' change the owner of the file(s) to the <user>. If you do a 'chmod -R 0700' and 'chown <myself>' on the same file, then only you can read and modify the files. :) The rest of the *world* cannot access the files.

Huygens

Thanks for the explanation.  Now that at least makes sense.  Time to hit the books - or at least "man" :) 
Cheers.

---

