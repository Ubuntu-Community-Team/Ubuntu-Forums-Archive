---
title: "Debian: Sublime Text"
date: 2012-11-03
forum: Any Other OS
---

### Post by skstid2012 on 2012-11-03
Recently, I decided to switch to a Linux distro (Debian 6.0.6) on my laptop. I wanted to get used to using the bash shell since all the websites that are hosted by my employer are on CentOS 5.5, I felt that using a Linux-based OS would be most beneficial (instead of using putty).

Anyway, I have attempted to setup Sublime Text on my Debian installation.  I followed the steps on all the following websites to get the installation working properly:

[http://docs.sublimetext.info/en/latest/getting_started/install.html#linux](http://docs.sublimetext.info/en/latest/getting_started/install.html#linux)

[http://mashingwachine.tumblr.com/post/4414279415/sublime-text-2-on-an-old-ubuntu-and-libgio-2-26#disqus_thread](http://mashingwachine.tumblr.com/post/4414279415/sublime-text-2-on-an-old-ubuntu-and-libgio-2-26#disqus_thread)

I get the following error when I run sublime via the Terminal:

"libgio version is less than 2.26, single instance support disabled"

I followed the instructions on this following website to manually compile libgio:

[http://www.tipiweb.tk/blog/2012/05/31/compile-glib-to-get-sublime-text-2-multi-instances-worked/](http://www.tipiweb.tk/blog/2012/05/31/compile-glib-to-get-sublime-text-2-multi-instances-worked/)

I know that according to the "mashingwachine" website mentioned earlier, I need to configure the following location "~/bin/st" with the LD_LIBRARY_PATH information.  However, when I use vim to edit that location ... I get the following error:

"bin/st" E212: Can't open file for writing

What do I do from here to get Sublime to use a single instance to open files?

All help is much appreciated.

---

### Post by sffvba[e0rt on 2012-11-04
This typically means you don't have permission to edit the file.  Have you tried this as root?


404

---

### Post by skstid2012 on 2012-11-04
> **not found said:**
> This typically means you don't have permission to edit the file.  Have you tried this as root?


404

I did. When I first installed Debian on my laptop, I added my personal user accout to the sudoers. I used both "sudo" and "su" to perform the task.  The problem is that neither "~/bin/st" or "/bin/st" exists in the filesystem.  When I try to edit them, I get the error mentioned above.

---

### Post by kiyop on 2012-11-04
[s]If it is not related to Ubuntu and it is related to debian only, why not posting at Debian forum?[/s]
[http://forums.debian.net/](http://forums.debian.net/)

> **skstid2012 said:**
> The problem is that neither "~/bin/st" or "/bin/st" exists in the filesystem.
```
find / -iname st
```may find out bin/st.
I wonder if it is not absolute path, but relative path.

ADDED AT Sun Nov  4 23:42:15 JST 2012:

I found your post on debian forum:
[http://forums.debian.net/viewtopic.php?f=30&t=87681&p=460045&hilit=sublime#p460045](http://forums.debian.net/viewtopic.php?f=30&t=87681&p=460045&hilit=sublime#p460045)

---

### Post by skstid2012 on 2012-11-05
Based on your response, I'll assume that you didn't read or look into the links I shared initially in my thread.  The "~/bin/st" and "/bin/st" locations don't exist in a fresh brand new Debian installation.  I ran your command multiple times and I browsed to those locations just to be sure my suspicions about the articles I read were correct.  Basically, a shell script needed to be created and placed in the "~/bin/st" location.  The "~" represents the home folder for your user account.  My username is skstid2012 in my Linux environment.  So, I had to manually create the location:

mkdir /home/skstid2012/bin

Then, I had to create the shell script using vim

sudo vim /home/skstid2012/bin/st.sh

Then, I had to write the shell script as described in the articles I provided.  After completing that, I made a symbolic link of the "~/bin/st.sh" to the following locations: "/bin/st" and "/usr/bin/st."  However, after completing all those steps and running my new "st" command I found out that my manual compilation of the glib/libgio failed.  So, tonight I will have to use git to checkout the glib 2.26.1 and recompile it manually to a specified location.  After that is complete, I will go ahead and edit my st.sh file to reflect the proper location to the glib/libgio files.  Technically, this should work (although, because I am still new to this ... I expect some issues to arise).

---

### Post by kiyop on 2012-11-07
I want you to post in debian forum that your problem will be solved.
_[http://forums.debian.net/viewtopic.php?f=30&t=87681&p=460552#p460113](http://forums.debian.net/viewtopic.php?f=30&t=87681&p=460552#p460113)_
Anyway, I hope you succeed.

---

