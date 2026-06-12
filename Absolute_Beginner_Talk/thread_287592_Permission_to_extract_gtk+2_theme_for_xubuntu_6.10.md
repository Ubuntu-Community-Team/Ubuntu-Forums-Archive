---
title: "Permission to extract gtk+2 theme for xubuntu 6.10"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-29
Hello, I'm trying to add a theme to my themes folder. How do I make it that I always have permission, I am the only user on my laptop.

this is what the error message in Archiver says: You don't have the right permissions to extract the files to the folder "/usr/share/themes".

Is there a setting that I don't know about to be able to use the Archiver and click the folder directly to extract the file the fastest to the location I want it?

Thanks,
-c.

---

### Post by taurus on 2006-10-29
Use the sudo command if you want to extract it to /usr/share/themes...

---

### Post by crimesaucer on 2006-10-29
So I can't just click "extract to" and choose a file? I have to open up terminal and extract it from there and copy it to the /user/share/themes folder?

---

### Post by taurus on 2006-10-29
Probably best to do it from a terminal...  I don't know why some people are so afraid of a terminal!  Usually that is the first thing I open when I sit in front of a Linux box because I can do a lot from a terminal.  ;)

---

### Post by crimesaucer on 2006-10-29
I'm not "afraid" of terminal, I just did about 20 different install/upgrades in the last two weeks, fixed errors of the xserver and daemon in ctrl/alt/f1 when my gui was failing and gone, and have avoided EasyUbuntu and Automatix2 for all installs of packages(except RealPlayer on edgy) because I prefer installing in terminal. 

It's just I'm really new to the xubuntu/ubuntu and the file system so I'm basically asking a simple question about extracting files and file permissions since this is one of the first times that I needed to actually do it. 

In windows I used WinRAR or the windows file extract ( choose a folder where it belongs) and "BLAMO" your file is in the correct place. So why not the same on the Archive Manager? I'm sure there is a way to make it the same.

My point is that I click a link and download a file, and it opens up a file extractor. So if I can't use the Archiver user interface and file system to put it directly into /user/share/themes, then how do I extract it properly to where the file needs to go, or should I extract it to my home folder and then use terminal to move it or copy it to a new file location? That seems like a lot of extra steps rather than just moving it from the Archive to the end destination. Same goes for not being able to drag and drop the file to the /usr/share/themes.

And yeh, sudo then a command, right, but WHAT command and WHY. 

If you're gonna answer a post (it says this in the forum rules), then please answer the post in a complete step by step explanation for beginners with the reasons why so new people in this "Absolute Beginners Forum" can learn, or don't answer it at all and let someone else do it. Also, explaining it completely will help a lot of people besides me when they use the search engine.

I don't mean to be rude, but sudo and "why are people afraid of terminal" aren't really good answers, especially when the reason I'm even on a linux is because I want to perform all of my actions eventually with terminal, but it helps to learn it before messing something up, believe me, I tried to install beryl and configure my gdm and ruined my system 2 days ago and then it took three different installs to get past the xserver upgrade errors...and I was in terminal and no GUI for like 3 to 4 days. I actually enjoyed it.

---

### Post by crimesaucer on 2006-10-29
I might of over-reacted a bit, I'm sorry, but without the actual step by step process with proper terminal code, it just doesn't say anything other than what I was thinking (....Now how would I do this the fastest using the terminal), and I still don't learn a thing about using the xubuntu Archiver correctly.

---

### Post by kerry_s on 2006-10-29
I usally just extract it than move it to .themes in my home directory, no permissions needed.

---

### Post by crimesaucer on 2006-10-29
How? I extracted it, then clicked on the folder icon to the right to choose where to extract it to, which was... /usr/share/themes... to place a .tar.gz theme I downloaded from the Xfce-looks themes page, and then I got the "no permissions error".

Do I need to click one of the option buttons, and if so, which one?

Am I using Archiver wrong.

Thanks for any replies,
-c.

---

### Post by crimesaucer on 2006-10-29
All right, I know I already scared away the help by being a tad bit short with Taurus, but I have tried to say sorry with a reason, but this is what happened when I tried to use terminal without knowing the way to ask terminal to Extract the file:

In terminal I wrote this: peep@show:~$ sudo cp -r /tmp/46153-Neutronium-Theme-Pack.tar.gz /usr/share/themes/

then it moved the theme to /usr/share/themes/, but now it was still not opened and when I tried to click on it (and I knew permissions would be denied because of the red x on the package box) I got this error message:

Can't open archive "/usr/share/themes/46153-Neutronium-Theme-Pack.tar.gz"

permission denied.

**EDIT 30 minutes later** All right, this is what I have meant during all of my bitching: the [option] "-r"  after the basic command cp that I wrote above for copying the files completely, is wrong, is there an [OPTION] for "extracting completely" while copying and moving from the tmp file?..So, basically an option to move files and extract while in terminal?..**end edit**

like this:  peep@show:~$ sudo cp [add correct option for complete extraction] /tmp/46153-Neutronium-Theme-Pack.tar.gz /usr/share/themes/

That code (if it is correct) and the correct command and [option] with a quick explaination why, would of been a complete answer. Sorry to keep bitching.

I also still feel there must be an easier way to use the archiver to avoid all of the typing. I'm sorry, I'm still a beginner.

---

### Post by kerry_s on 2006-10-29
No, man you just extract it where you downloaded it to, then copy it to the .themes folder. The themes folder is a hidden folder in your user folder, if it's not there you make it.

---

### Post by crimesaucer on 2006-10-29
Thanks, I'll try that.

And to all of the ubuntu forum help, I apologize, you read about linux forums on digg and hear about all of the RTFM stuff, and I haven't ever ran into that on ubuntu forums, not even in this post, I just felt like the 1st and 2nd replies were kinda "Nick Burns- the computer guy", and it didn't really say anything other then use sudo, instead of...this is how to use sudo and the terminal.

---

