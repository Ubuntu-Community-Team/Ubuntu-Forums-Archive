---
title: "Automatix Install Question....maybe Problem"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-20
In my looking around today I found Automatix, which seems like it is perfect for a person like me who is trying to get a handful of those programs in the easiest fashion.   I can't tell, however, if I'm doing this correctly.  Here's what I did.  

I got all my info from this thread: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

I entered this command in terminal: 
wget [http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb)

I got this: 
--18:21:24--  [http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb)
           => `automatix-ubuntu_4.0-1_i386.deb.2'
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,180 (32K) [text/plain]

100%[====================================>] 33,180        98.68K/s

18:21:24 (98.49 KB/s) - `automatix-ubuntu_4.0-1_i386.deb.2' saved [33180/33180]


I then entered this command: 
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb

and got this:  
Selecting previously deselected package automatix.
(Reading database ... 77906 files and directories currently installed.)
Unpacking automatix (from automatix-ubuntu_4.0-1_i386.deb) ...
Setting up automatix (4.0-1) ...

But that's it.  I just took me back to my name prompt where I would enter another command.  Is that how this works?  I doesn't appear that anything changed or was installed.  

I from the thread it doesn't appear that I would need to do anything else, but maybe I'm missing something.

---

### Post by endersshadow on 2005-12-20
Amazingly, yes, it did work.

The great thing about Linux is that it just assumes you're right, and if you're not, it'll tell you.  And trust me, you'll know.

To load up Automatix, go to Applications>System Tools>Automatix and it'll be there in a nice, handy, GUI.

Welcome to Linux :-D

---

### Post by Nameless on 2005-12-20
Oh yes!  I see that it did work now, endershadow.  

I'm going to really enjoy Linux/Ubuntu.  This is great.  What a great package.

Thanks

---

### Post by Rackerz on 2005-12-20
That's exactly what i love about Linux, it tells when your doing something wrong and shows you what it's doing when your right! Not like in Windows were a program just fails to load without notice.

---

