---
title: "Repository Error Message installing Automatrix2"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-03-16
I am brand newbie as I just installed Ubuntu yesterday and in the the process of installing new software programs I really screwed up.  I attempted to install Automatrix2, but was unsuccessful, so I gave up.  Later, I discovered that when I put my pointer on the orange icon with the star burst located on the top line about 4/5 to the right corner, I got this error message popup:

A error occurred, please run Package Manager from the right click menu or apt-get on a terminal to see what is wrong.  The error message: Opening the cache (E:Type 'bat328blue' is not known on line 34 in source.list /etc/apt/sources.list, E:The list of sources could not be read)'

This is way above my head and your help will be appreciated.  Please consider my skill and experience level (very very low) in your reply.

Thank you

---

### Post by Stone123 on 2007-03-16
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

in terminal type : gksudo gedit /etc/apt/sources.list

press emter
truncate (delete all text) and paste new from site

---

### Post by explorer716 on 2007-03-16
Here is some additional Information about my problem:  

E: Type 'bat328blue' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


As suggested I went to Systems>Accessories>Terminal  and after: robert@robert-desktop:~$ I typed gksudo gedit/etc/apt/sources.list and hit enter.

When I did that all remained was: robert@robert-desktop:~$ 

I checked and the problem is still there.

---

### Post by explorer716 on 2007-03-17
Please disregard my previous post as I did not describe things correctly.  Please allow me to try to get it right.

  1)  Following the message from Stone123 I went Applications>Accessories>Terminal and keyed Enter.

  2)  I get a blank screen except:  robert@robert-desktop~$
 
  3)  I key in the information from Stone123"s reply. Now the screen looks like:
          robert@robert-desktop~$ gksudo gedit /etc/apt/sources.list  and press enter.

  4)  I get a screen asking for my password.  After entering my password I get a screen with on it:
           robert@robert-desktop~$ gksudo gedit /etc/apt/sources.list 
           robert@robert-desktop~$
 
   5)  This where get lost: What text do I delete and what do I paste  and from which site? And then what do I do?

Thanks for your assistant.  As you can tell,  I am a lost ball in high grass.

---

