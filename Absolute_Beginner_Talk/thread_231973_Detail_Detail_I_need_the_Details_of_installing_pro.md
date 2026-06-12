---
title: "Detail Detail I need the Details of installing programs."
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Ludwig7666 on 2006-08-08
Hi all and I hope that someone or some may do this for me. If I like enough it will be placed on my site as a reminder plus another way to help newbs like myself. First off I can say that I'm dyslexic (hands-on and visiual learner) so I learn differnt from most of yous. I also need to know what's going on when I do this or that. The background jobs kinda deal. It seems to be easier in windows(4 years) then linux(1 week) so far.

Ok where I've read from many linux sites, guides and forums I don't seem to see where they help with installing programs onto linux well enough for me. I do have Ubuntu Dapper Drake 6.06. I tried to run and setup my programs and that to how I like it orginised. But I can't seem to properly install any programs, even programs to run those programs. Could I ask for a detailed list and what's going on for each section? 

Simple Example: 
Push "On" button to turn on computer: It loads the OS/kernel to user login.

Place user name and password: Computer checks and sees it's ok to load up any startup programs and settings, then does it.

Click on firefox browser icon to start program: Computer sees you want to turn on firefox so it does. Firefox is now loaded.

Blah blah blah and so on and so on. This is how I think of most stuff, Very Simple. Just dunno how to program quit yet.

I go and find myself a game to install for linux. I would download the tar.gz file. Then after downloading them I would right click then "extrack" I would see a .sh file name and turn on the game from that (Well for Nexuiz). I can't send to desktop or somehow make a shortcut so I can have it in easy reach. I tried to play around in Run Application but nothing seems to work or stay there. I even tried messing around in Add/Remove Appication. It don't find anything new and the only programs I can find is from ubuntu's appication list, for ubuntu. I have wine installed?? I guess. I even tried some of my normal windows programs, like Ventrilo, winrar, winamp, alleycode. They seem to install like the normal windows way but can't get them again. I found out about show hidden file in the Run appication's "Run with file" so then I can see them in the wine folder but can't open any of them. It claims that it can't find the file or can't be opened. I tried the README files and stuff but it don't say much to me in great detail of what's going on. I like the quote "Keep it simple stupid!", so if you can could you help me along, please.

---

### Post by krazykirk on 2006-08-08
Hi there,

Installing programs in linux is quite different from windows. Well in some cases it can be very similar lol. When you download a program to use with linux, try to find a ubuntu or debian version of the program you're looking for. It should end with a .deb . If you're using dapper, then installing it should only double clicking on it and it should install! If not you can use dpkg from the command line to install it.

When you download a tar.gz or whatever file, and just extract the files somewhere, and run the .sh file or something like that, it will only run from there. It won't come up in the applications menu, and it won't come up from the run thing unless you enter a absolute path, such as /opt/game/whatever.
If you want to just type in the name in the run box and want it work, it only runs programs from the /usr/bin folder. I think you might be able to get it work with something called symbolic linking, but i'm not sure. For your application menu problem, if you right click on applications and click  edit menus, it should open a program called the Alacarte Menu editor. Then just go file > new entry and you should be able to figure out the rest! If you need any more help just post again and i'll try to help! :)

---

### Post by Sef on 2006-08-08
To install anything, [read this.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Ludwig7666 on 2006-08-08
thanks guys.

I like that link Sef. But Sef what does your signature mean? Su stands for switch user. The plural of virus is viruses. you saying that there is many viruses for su, or did I read that wrong?

---

