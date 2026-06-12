---
title: "Anyway to See Commands Run by Applications?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Miikee on 2008-04-10
I really like using the terminal... and am beginning to really enjoy Linux, it has got me into an entirely new way of doing things on computers.  
I try to read the man pages before running most commands and try to automate most of the tasks I do (which are really basic lame tasks... tar, mv, nautilus, cp, etc).  Doing this always takes me about 4 times as long than if I had just gone ahead and manually done the work... but I guess that's learning.

So before this time disposal learning method gets old and too frustrating, I'm trying to figure out some ways to expedite the process of learning some basic/common/useful/interesting  commands/tasks/options.

I was wondering if there is an application around that I can open  that displays  the command lines that an application I have running in gnome gives the computer when I am using the program.
Examples of this would be: 
 See what command is given to the computer when I'm running firefox and click refresh or back or enter a url.
-or-
If I'm in gimp and am just drawing something.

Something similar to what I'm thinking of is "xev"... that is an awesome little program!  I want something like that for everything I do on the computer!

I'm thinking that this probably can't be done with most programs... due to different orders of programming language (I think that's why).  But anything like described above would be helpful.  

Also any tips that someone could share with me about things to do in the terminal (or anywhere on Ubuntu) to help me learn would also be helpful. 
 I also understand that learning will take time.  And I know reading is probably one of the best ways to learn, and I do.  I read ALOT about it.  Maybe not the best things though... mostly forums, tutorials, articles.

Is asking in forums a good way of getting info fast, or should I always search a topic for about 2 hours and then ask my questions?  I didn't do this for this question, because I'm a little busy.. but this question kept taking my interest away from my homework.

Thank you very much for your suggestions and help.

---

### Post by Hospadar on 2008-04-10
well a lot of times, there is no terminal command, like for example, when you start firefox, the command "firefox" gets executed, but there is no way from the command line to cause actions within firefox to happen after it's started running.  Some applications (for example mplayer) do have some interactive terminal qualities, but very few graphical applications support this.

If you are looking to automate things, there are almost always good command line tools to do whatever you need to do, like let's say you wanted to scale down a ton of pictures from the command line, you could use imagemagik (sp?).

If you just want to see what command starts an application, you can search for it in one of the "bin" folders, like /usr/bin, /usr/share/bin, or /bin, or if there is a shortcut to it (like in the gnome menu) you can look at it's properties and see what command it calls.

Also, if you find yourself entering the same command over and over again (like for example, "tar -xzvf" to unpack gzipped tar files, you could write an alias for that in your .bashrc file.

Try opening it up in gedit "gedit .bashrc" scroll down to the bottom and you'll see some aliases already in place, the basic format is "alias <command you want to type>='<actual command to execute>'

Also, I would suggest, if you are having trouble with any specific command line apps, that you try and google around for how to use them.  Most applications websites have really good guides that go in depth about all their command line switches in a way that is more helpful and accessible than a man page.  Oftentimes too, you can find ready-made recipes for a lot of command line actions

---

### Post by Trail on 2008-04-10
The gnome task manager gives you the command that was used to run an application.

> 
but there is no way from the command line to cause actions within firefox to happen after it's started running

No, but it's possible on KDE applications through dcop etc. Look it up.

---

### Post by kpkeerthi on 2008-04-10
There is also **pstree**

---

