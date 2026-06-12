---
title: "[SOLVED] How Can I Launch HellaGUI From The Gnome Panel?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-02-26
UPDATE:  This thread started as a search for a great front-end for the binary download program called Hellanzb.  See my final post in this thread for the solution.  04/06/08

I've just installed HellaGUI, and I like it very much.  I'd like to get things set up so that I can put an icon up in the top Gnome Panel and just click on the icon to start HellaGUI.

I've tried all the things I've learned how to do within the last week, but none of them work.  I just can't understand why I can double-click it from the desktop, and it will run, but when I try to make a launcher for it, no joy!

It's already set as an executable text file, so I don't think that's the issue.

Anyone have any idea how I can get this to run from the panel?

Thanks!

FwF

---

### Post by jordanmthomas on 2008-02-26
RIght click on your panel and go to "Add to Panel"
Then, add a custom application launcher.
In its command field, type the full path to the script you use to run HellaGUI.

---

### Post by FreewareFan on 2008-02-26
Thanks for the reply.   I already tried that, both on the desktop and in the panel.  Neither one works.   The only thing that works is to double click on the script file itself.

Weird, huh??

---

### Post by darkworld on 2008-02-27
I want to do this too but im using hellagui at the moment and dont want to upset it. Some thoughts though. Is it because it installs as hidden or maybe its path needs to be added????

---

### Post by darkworld on 2008-02-29
Ok I give up too! how is this done?

> /darkworld/home/hellagui/hellgui1.1.1/hellgui1.1.0  click this script and it fires up fine.

Put that path in custom launcher application location and no go.

> Failed to execute child process "hellagui1.1.0" (No such file or directory)

so I thought >  export $PATH /darkworld/home/hellagui/hellgui1.1.1  to try and help things along. Still no good. What is going on here?

---

### Post by FreewareFan on 2008-02-29
Good question... I'd also like to know...

---

### Post by darkworld on 2008-03-01
ok the reason seems to be its a python script and although I have specified in $PATH the route to the script I think maybe there needs to be something else included in $PATH to python. Sorry I know very little of python. Any takers????

---

### Post by FreewareFan on 2008-04-06
UPDATE:  To anyone who runs hellanzb as their binary downloader, I have found what I consider to be the perfect GUI front-end for it.  Very easy to install, works perfect, and has all the features necessary.  It's called LottaNZB.  If you run hellanzb, and have been looking for a good front-end, I suggest that you give this a try.   [http://www.lottanzb.org/](http://www.lottanzb.org/)

You can launch it from the menu, or from a task bar or dock of your choice.  It then fires up hellanzb, and you can choose the nzb file or files you want to download, and it does the rest.  You can even change the destination directory if you wish.  Really cool.

---

