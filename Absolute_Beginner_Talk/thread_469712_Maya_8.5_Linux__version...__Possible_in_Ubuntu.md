---
title: "Maya 8.5 Linux  version...  Possible in Ubuntu?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-10
Hello!
I'm ubunting some of my friends (4 Already! Ubuntu 100%) , but one of them uses Maya 8.5 (wich has a linux native version in RPM) But has been absolutely IMPOSSIBLE for us to install it on Ubuntu. (Alien doesn't works, and creates broken debs)...   And we have NO IDEA about this ( new users on linux)

My only question is...  Do we have even a single chance to install that strange linux version of Maya 8.5 in Feisty? I spent lot of time looking in internet and I guess is not possible... :(   This is the only reason my friend is still in Windows...

Help!! 	:cry:

---

### Post by Kosimo on 2007-06-10
By the way... I got this how to, in gentoo

[http://gentoo-wiki.com/HOWTO_Install_Autodesk_Maya_8.5](http://gentoo-wiki.com/HOWTO_Install_Autodesk_Maya_8.5)

I know it doesn't help... But...  I though if some program runs on linux should run in all distros right? 

hm...

---

### Post by Golyadkin on 2007-06-10
How about this tutorial?   Installing Maya 8.0 in Kubuntu:
[http://www.wouz.dk/autodesk-maya-misc/maya-8-installation-under-kubuntu-6061-lts/](http://www.wouz.dk/autodesk-maya-misc/maya-8-installation-under-kubuntu-6061-lts/)

That tutorial works great, the only thing 8.5 needs is a second symbolic link after the first one:

sudo ln -s /usr/autodesk /autodesk

Then continue installing the .deb packages.

---

### Post by meborc on 2007-06-10
maybe this will help you? [http://ubuntuforums.org/showthread.php?t=66859](http://ubuntuforums.org/showthread.php?t=66859)

if you read the final 2 pages you will see that they got maya 8.5 working under feisty... i guess you just need to read the whole thread to see if they used the original instructions or something else...

good luck :)

---

### Post by Golyadkin on 2007-06-10
Also on the official Autodesk forums someone says it will work also if you extract and install manually:
[http://discussion.autodesk.com/thread.jspa?threadID=552396](http://discussion.autodesk.com/thread.jspa?threadID=552396)

---

### Post by Kosimo on 2007-06-10
Thank you guys, we'll try to follow that guides tonight!

I'm happy to know that someone has maya 8.5 on feisty! :-)

Now, I'm just wondering if I will be able to do it with my small knowledge! :P

---

### Post by samsf28 on 2007-06-10
I was having trouble installing Maya 8.5 yesterday even after following those tutorials but then I reinstalled Ubuntu and this time chose the ext3 journeled formatting and it worked, I was having the same issue with broken deb's the first time. It seems alien doesnt like fat formatting and behaves wierd. I am relatively new to unix too, so still learning my way around it. 
Offcourse after installing maya I ran into a new problem of the viewport having redraw issues where if you click on the pull down menus when you close them they leave behind a grey rectangle the size of the menu in the viewport. and then i have to refresh the viewport for it to clear out. Any one know what that is all about. I think its got to do with my machine being old and having the older crappy Ati x300 mobility radeon.

---

### Post by fordey42 on 2007-09-05
installed maya 8.5 on my Ubuntu machine, but it does not see the parallel dongle.  It says there is an error in the license file if i point to it manually.  Anyone know how to get Ubuntu to see the parallel port dongle thing

---

