---
title: "[SOLVED] Newbie to Ubuntu having all sorts of trouble trying to install ah2-0.22tar.g"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Justin72 on 2008-04-18
Hi there, I am a total newbie to Ubuntu and Linux.  I am trying to get Autohouse II 0.22 up and running without any luck.  Here is the link to the program [http://linux.softpedia.com/get/Office/Finance/Autohouse-II-12341.shtml](http://linux.softpedia.com/get/Office/Finance/Autohouse-II-12341.shtml)

I have read the installation guide in the downloaded package but being totally new to linux I am not sure if I am completing things correctly.  I have looked in the add programs section and also the Synaptic Package Manager without any luck in finding the program.  So therefore I am assuming I need to install it from source code.  Below is what I get from the terminal when I try to uncompress the source.

justin@laptop:~$ tar -zxvf ah0.22.tar.gz
tar: ah0.22.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

The file is stored on my desktop. I have tried cd Desktop and I get this response
justin@laptop:~/Desktop$ tar -zxvf ah0.22.tar.gz
tar: ah0.22.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can anyone help and if so can you please explain as if you were trying to explain it to someone who is very new to this operating system.

Thank you in anticipation.

---

### Post by SunnyRabbiera on 2008-04-18
well we do have a unzip application, but if you really want to you can try to convert the suse RPM package to a debian installer using alien...
but let me test it out for you as alien can be a bit messy sometimes.


edit: bugger, the RPM link dont work and its built on suse 9.1... how silly.

---

### Post by spiderbatdad on 2008-04-18
In the screenshot...you have extracted the package...hence the folder of the same name. The reason you were getting package not found is, the package in the screenshot is called:  ah2-0.22**(2)**tar.gz
It must be a second download. Anyway the next step is generally to cd into the folder to complete the installation.
You can avoid simple typos by using the tab key to auto-complete filenames. For example tar -xvzf ah (hit the tab key to complete the package name.) If it fails...it usually because you are in the wrong directory, or requesting invalid options.

---

### Post by Xzenome on 2008-04-18
You might want to have a look around for something different, this requires an external database which is going to make it even harder to set up.

---

### Post by bumanie on 2008-04-18
There is usually a text file in the extracted directory that gives installation instructions.

---

### Post by Justin72 on 2008-04-18
Thanks spiderbatdad your help is appreciated.  Ok well I have got as far as installing the software but I am having no luck getting this configured now.  I know that Xzenome suggested that I look around for another product but I cannot find one that has this sort of detail.  I have tried to follow the instructions in the text file but being so new to linux I am not sure how to even identify when something goes wrong or even if the instructions are incorrect.  Is there anyone that might volunteer to try and get this working and if so can they help me step by step.  I know that I am asking for a lot, but if I don't ask I will never know.  Or should I be in another forum to be asking this sort of question?

Thanks again for everyones help.

---

### Post by Justin72 on 2008-04-20
I love the concept of linux, but it is all too hard to learn how to install software and if things don't go right you can take days to try to work it out and still not know what you are doing.  This is what I have done all week and still I don't understand how to even get source coded software to work.  Unfortunately I don't have the time to try to nut this one out any more.  Thank you to those that tried to help an absolute novice.  I wish there were courses on linux.

---

### Post by Justin72 on 2008-04-20
Sorry this is not solved, but I couldn't find how to remove the thread.

---

