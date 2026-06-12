---
title: "extract autopackage.tar.bz2?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by raker t on 2007-05-20
Hi all, I'm as green as can be, and newer than noob. I installed Ubuntu 5.04  Friday night. I put a second hard drive in this machine, and put linux there. The other drive is MSwindows, I have it connected to the internet. I downloaded Inkscape there, put it on a flash drive, and moved it over to the other drive. Also a couple extra files from the Inkscape site, one of which is autopackage.tar.bz2. From what I gather, I need to have the files all in the same directory, and, have the two extra files there before I try to run the main Inkscape file. 
 Nothing happens. I thought maybeI need to extract the bz2 file. I clicked "extract here", and another icon showed up in the same folder, but the folder is empty. When I double clicked the bz2 file the next time, a box opens to the left of the screen, "Archive Manager". Inside of that is an error box, which says:

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Read 8305 bytes from /var/tmp/autopackage.tar.tar
tar: Error exit delayed from previous errors

Obviously, I need to get the ubuntu side connected to the internet, and download the software directly. But I'd like to learn how to do it with a CD, so that I can also insatll it on my laptop, and some other machines (art students next fall). 

Obviuosly, I could be doing all kinds of things wrong here, like "No, that_is_not_how you extract a tar file, and that is not where you park your new software (System files/var/tmp), and do you even know where to get to the command line dialog?" No I don't. :o 
 So like I said, newer than noob, please_explain_things_really_slowly. Thanks alot.
 PS: this "same directory" is having them both in the same folder what is refered to here?

---

### Post by taurus on 2007-05-20
5.04 is real old so you should consider installing the latest one if you can, Feisty Fawn--7.04.  And if you want to extract something, you can do it from a terminal.

Applications -> Accessories -Terminal
```
tar xvjf autopackage.tar.bz2
(assuming you are in the same directory that autopackage.tar.bz2 is located)
```

---

### Post by raker t on 2007-05-20
Thanks taurus for the info, but it looks like there is no "terminal" in accessories. Maybe this isn't part of the basic install?

---

### Post by taurus on 2007-05-20
Try <Alt>F2 and then type **gnome-terminal** to bring up a terminal.

---

### Post by aysiu on 2007-05-20
5.04 is really old. Terminal in 5.04 is under Applications > System Tools, I think.

---

### Post by raker t on 2007-05-21
Yes it was under system tools, and thanks for the help. The problem now is that it's saying

 " can not open, no such file or directory"

I've tried it a number of different ways, always while I had the file open that the autopackage.tar.tar is in. I tried it while the file was selected, and while it wasn't. I tried it with (what I thought) was the whole "address". Instaed of saying "C" I wrote Filesystem/var/tmp/autopackage.tar.tar>enter.
 
Always the same message. I must not understand "directory". Thanks for your patience. This forum is like an emergency ward on steriods. Wow.

---

### Post by wormser on 2007-05-21
> **raker t said:**
> Yes it was under system tools, and thanks for the help. The problem now is that it's saying

 " can not open, no such file or directory"

I've tried it a number of different ways, always while I had the file open that the autopackage.tar.tar is in. I tried it while the file was selected, and while it wasn't. I tried it with (what I thought) was the whole "address". Instaed of saying "C" I wrote Filesystem/var/tmp/autopackage.tar.tar>enter.
 
Always the same message. I must not understand "directory". Thanks for your patience. This forum is like an emergency ward on steriods. Wow.

Where did you save the file to?  You need to be in that directory (folder) to run the command.  The terminal cannot find that file in that directory and gives that error.  You need to use the command **cd** to change directory.  The **ls** command will list what is in your current directory.  Here is an example if you are trying to get to the Desktop.

```
cd Desktop
```

When you open the terminal it starts you in the /home/your_user_name.  The Desktop is in your home directory.  

Hopefully that helps.

---

### Post by raker t on 2007-05-21
That reply from Wormser is good. I feel like I'm closer. There are acouple of things I'm not sure of though. 

 In order to get to a directory when I first open terminal, do I type in the whole address? In order to see the file in GUI, I go to filesystem/var/tmp/autopackage.tar.tar. The closest I can relate to that (MSwindows thinking) is: C/var/tmp/autopackage.tar.tar
 Would the code look like this:  cd Desktop/filesystem/var/tmp  ?
 Or do I skip all that and simply write: cd tmp  ?

Thanks again for the help.

---

