---
title: "[SOLVED] No such file or directory"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-11-08
Alright, this has been getting me annoyed for the past little while. Why is it that every time I have to extract or install something (at least, that is how far I have ever gotten when running in terminal) I always get the error that says: no such file or directory. For instance, when trying to unpack the tarball from my desktop for my Wacom Intuos3 4x6 from the Linux Wacom Project, I got that error. After getting agitated, I decided to just right click the tarball and extract it onto my desktop. I have been trying ever since to try and install the file/folder, but I keep on getting the same error. This is a problem that I have had since the beginning - the beginning being after install Ubuntu from the CD ISO that I downloaded, even after the upgrade to Gutsy from Feisty. If you can help me with this I will be pestering this forum a lot less! Thank you!

---

### Post by Chilongola on 2007-11-08
Do not have much to go by in terms of specifics but...  Are you for instance typing file name exactly as the name is spelled?  By this I refer to say "-"  "_"  "."  caps and so on?

---

### Post by ShadowMKII on 2007-11-08
Unfortunately, yes. I have checked over and over again. I have even copied and pasted the name of the folder into my terminal and ran the command, only to come up with nothing.

---

### Post by Maestro23 on 2007-11-08
> **ShadowMKII said:**
> Unfortunately, yes. I have checked over and over again. I have even copied and pasted the name of the folder into my terminal and ran the command, only to come up with nothing.

So the tarball is on your desktop:

> cd ~/Desktop

Need to extract it:

> tar xvf filename.tar.gz

Change directory to extracted folder

> cd /extracted folder

List contents of folder

> ls

Are you doing something like that?

---

### Post by ShadowMKII on 2007-11-08
Alright! So far, I am getting very excited. Everything worked, until I hit cd /folder name. That did not seem to work. Maybe I am doing something wrong. 

[[img=http://img474.imageshack.us/img474/3632/screenshotzv6.th.png]](http://img474.imageshack.us/my.php?image=screenshotzv6.png)

Do you think that I am listing the wrong file name?

---

### Post by Maestro23 on 2007-11-08
> **ShadowMKII said:**
> Alright! So far, I am getting very excited. Everything worked, until I hit cd /folder name. That did not seem to work. Maybe I am doing something wrong. 

[[img=http://img474.imageshack.us/img474/3632/screenshotzv6.th.png]](http://img474.imageshack.us/my.php?image=screenshotzv6.png)

Do you think that I am listing the wrong file name?

Ah... I see your problem.  You are **already in **your Desktop directory, you don't need cd /linuxwacom-0.7.8-3

Just cd linuxwacom-0.7.8-3

The command you are using is telling Ubuntu to look for the** linuxwacom** folder in the **/ root** directory.l

---

### Post by ShadowMKII on 2007-11-08
I am slightly confused now. I am glad to know that ~/Desktop will send me to my desktop, but after that, I do not know what commands to enter to get things working. Here is what I have been told to do on the Linux Wacom Project's website.

[[img=http://img214.imageshack.us/img214/1466/screenshotfn6.th.png]](http://img214.imageshack.us/my.php?image=screenshotfn6.png)

I am trying to get all of this accomplished for my little Ubuntu, and things do not seem to be working; perhaps that screenshot will get you an idea of what I have been trying to do.

---

### Post by strabes on 2007-11-08
I will try to clarify what maestro said. The reason you're getting "no such file or directory" when you type "cd /linuxwacom-0.7.8-3" is because of the slash. By the way, it's much easier to just type "cd" then hit TAB twice and you'll get a list of all the possible folders you can cd (change directory) into. If you start typing the first few characters of a filename and hit tab it will complete it for you. This helps to prevent against typos, etc.

---

### Post by ShadowMKII on 2007-11-09
I think I might be understanding this now. However, I still have a couple of problems! I'll show you what I have done.

[[img=http://img141.imageshack.us/img141/2207/screenshothv7.th.png]](http://img141.imageshack.us/my.php?image=screenshothv7.png)
[[img=http://img222.imageshack.us/img222/5266/screenshot1ry3.th.png]](http://img222.imageshack.us/my.php?image=screenshot1ry3.png)

I do not know if I am getting better or worse at this, but it feels a bit better. The only problem now is that after I get to where I was on the second screenshot I gave you, I encounter the problem of ./uninstall or ./install being called not a valid directory.

---

### Post by Maestro23 on 2007-11-09
> **ShadowMKII said:**
> I think I might be understanding this now. However, I still have a couple of problems! I'll show you what I have done.

[[img=http://img141.imageshack.us/img141/2207/screenshothv7.th.png]](http://img141.imageshack.us/my.php?image=screenshothv7.png)
[[img=http://img222.imageshack.us/img222/5266/screenshot1ry3.th.png]](http://img222.imageshack.us/my.php?image=screenshot1ry3.png)

I do not know if I am getting better or worse at this, but it feels a bit better. The only problem now is that after I get to where I was on the second screenshot I gave you, I encounter the problem of ./uninstall or ./install being called not a valid directory.

According to the directions on that screenshot, there should be a **prebuilt **directory inside the linuxwacom directory.  While you are inside the linuxwacom directory, do a **ls** (list contents of directory).  

If so, you need to change directory (**cd**) to it before you run those commands.

---

### Post by ShadowMKII on 2007-11-09
Haha, that would be me being dense. Being tired is no excuse! Well, thank you for all of that - you have successfullly taught me how to use the cd command properly, minus my idiocracy. Thanks again everyone!

---

### Post by Maestro23 on 2007-11-09
> **ShadowMKII said:**
> Haha, that would be me being dense. Being tired is no excuse! Well, thank you for all of that - you have successfullly taught me how to use the cd command properly, minus my idiocracy. Thanks again everyone!

Good deal man.  Here's a link that might come in handy for ya down the road:

Intro to Terminal: [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)

Glad you got things sorted out man.:guitar:

---

