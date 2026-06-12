---
title: "Help!!! I find Gnome extremely frustrating."
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by USarge on 2008-02-15
I have no "real" knowledge of Linux or Ubuntu and have been nothing but frustrated with it.  

- I have no idea where files go when new software gets loaded or downloaded, etc.

- The top menu bar is now on the right hand side of the screen and I'm not able to move it or find ANY step-by-step instructions on how to change it.

- I'm just about ready to give up and stick with Windows.  It can be a pain, but at least it's easy to get around in and you know where to find stuff.

---

### Post by taurus on 2008-02-15
1.  Your download stuff is usually in ~/Desktop.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
ls -la
```

2.  You can just drag it back to the top.

3.  If you think windows works better for you, then stick with it!

---

### Post by Het Irv on 2008-02-15
First I have to say that I love your Avatar. Beaker FTW.

Okay, down to buisiness,  what are you downloading from?  Different programs do differnent things with their files.

Menu bar, just click and drag back to the top.

Stick with it, Linux takes a while to get used to. Good Luck.

---

### Post by LRT on 2008-02-15
gnome and kde are one of the most user friendly window managers available for linux.. kde is more windows-like, so u may want to try it... if you are really struggling with figuring out basic things, i would read the following to websites:

[URL="https://wiki.ubuntu.com/"]
https://wiki.ubuntu.com/[/URL]
[URL="http://ubuntuguide.org/wiki/Ubuntu:Gutsy"]
http://ubuntuguide.org/wiki/Ubuntu:Gutsy[/URL]

hope this helps

---

### Post by Yoke &amp; Chung on 2008-02-15
If you are used to Windows environment, maybe you should install KDE based Distros such as Kubuntu and PCLinuxOS. These distros look very Windows.

I have used Windows for 16 years(?) (since Windows 3.11) and I do not find GNOME difficult to use at all when I switch to Ubuntu, just need to explore all the options and menus,  sometimes programs installed do not appear on menu cos they do not have GUI interface. 

You will get used to it after awhile. However easy to use is  McOS X, if you are using it for the first time and used to the way you do things in Windows, you will be stumped too.

---

### Post by uberlube on 2008-02-15
If you have been giving Linux a try it means that you have been looking for a release from the proprietary prison that Microsoft has had you trapped in for probably a very long time, and all I can say to you is dont give up yet! Linux is the best thing since Kraft Dinner and it is definitely worth sticking with and spending the time to get to know. At one point you didnt know how to use windows and it took you time to learn that so if you just give Ubuntu the same chance it will pay off. I guarantee it :). I have been using linux for only 3 months now and when I started I felt the same way but it didn't take long to adjust. Here are some things that I think will help:

1) Dont use gnome, use the KDE desktop environment. Much better and feels alot like windows, the KDE version of Ubuntu is called KUBUNTU. Which leads me to number 2

2) Use LinuxMint. It is based on Debian and Ubuntu which are the best 2 ditros out there for Linux noobs.

3) Start learning how to use the command line, just google it and start from there. It will be your best friend after a while.

Cheers

---

### Post by jingo811 on 2008-02-15
Just sit back and watch.
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

[LIST]
[*]Files and Folders
[*]Installing Applications
[*]Tour of the Ubuntu Applications
[*]Tour of the Ubuntu Desktop
[*]Customising Ubuntu Desktop
[/LIST]
[LIST]
[*]Why Ubuntu
[*]Introduction to Linux
[/LIST]

---

### Post by LRT on 2008-02-15
wow! 4 replies in the same minute... can u get better support than this???

---

### Post by FoolsRun on 2008-02-15
> **USarge said:**
> I have no "real" knowledge of Linux or Ubuntu and have been nothing but frustrated with it.

- I have no idea where files go when new software gets loaded or downloaded, etc.

This isn't something you need to worry about. The package manager (either the "Add Programs" menu item on the "Applications" menu, or "Synaptic Package Manager" in the "System" menu) handles all of that for you. Applications will add themselves to your "Applications" menu and organize themselves into appropriate sub-menus.

Uninstalling software is as easy as unchecking a box in the package manager and hitting "apply".

If you're compiling software manually, which I don't recommend if you're new to the Linux world, then it's a little trickier.

Package management takes the guess-work out of installing software and prevents you from installing things where they shouldn't go. I understand it can feel a little restrictive when you're coming from the Windows world of "if you really want to you can Office inside the c:\Windows folder", but package management really makes things easier.

> - The top menu bar is now on the right hand side of the screen and I'm not able to move it or find ANY step-by-step instructions on how to change it.
1. Right-click on an empty area on the top-bar.
2. Select "Properties"
3. On the "General" tab of the properties dialog, change "Orientation" to "Top".
4. Click "Close".

Should be fixed!

---

### Post by uberlube on 2008-02-15
Were a strong community, and oh ya "Welcome" :)

---

### Post by USarge on 2008-02-15
Thanks for the replys.  

Weird thing is, I couldn't drag it back.  I think it has to do with my screen size and resizing a problem.  I guess I wasn't able to "grab" it because I only have a 13" viewable laptop.  But when I opened Firefox, the menu bar seemed to get "released" and then the hand appeared so that I was able to get it back to the top.  Very weird; but by pure accident I was able to get it back.

I guess to be a little more specific is what if you load a program, through Synaptic Package Manager and a 'shortcut' doesn't appear in one of the menus up top; where is the program if I want to add it to one of the menus?

---

### Post by jan quark on 2008-02-15
you can have a look in

system > preferences > main menu

perhaps it is listed there but not checked to be displayed

what application do not show up in the menu?

---

### Post by jaytek13 on 2008-02-15
Aside from the placement of the "start" buttons, KDE is more like a mac and Gnome is more like Windows. And, as the OP has already figured out, you can place the "start" button on the bottom in Gnome, too. But, his questions are not Gnome specific so switching to KDE will not resolve them.

And, for the OP, as far as moving the bar, you have to right click on it and select "unlock" before you'll be able to move it, assuming it is locked atm.

---

### Post by USarge on 2008-02-15
> **uberlube said:**
> If you have been giving Linux a try it means that you have been looking for a release from the proprietary prison that Microsoft has had you trapped in for probably a very long time

quite right.

> **uberlube said:**
>  Linux is the best thing since Kraft Dinner 

That's hilarious, Uberlube.  Thanks.

---

### Post by Yoke &amp; Chung on 2008-02-15
Did you set your screen resolution correctly? The menus could go off the screen if the settings is incorrect, happened to me whenever I switch the graphics card.

Usually Synaptics will put the program icon according to its nature, administrative software such as GParted (Partition Editor as it appear) and Firestarter will be found under "Systems--> Administrator". Whereas internet related such as Kompozer and Azureus will be found under "Applications--> Internet". 

I do remember I have a hard time searching for the software I installed when I use Ubuntu for the first time.

---

### Post by FoolsRun on 2008-02-15
...whereas services like Apache won't get an icon at all unless you also install a gui configurator for them.

What software did you install that didn't show up in the menus, USarge?

---

### Post by jingo811 on 2008-02-15
> **USarge said:**
> 
I guess to be a little more specific is what if you load a program, through Synaptic Package Manager and a 'shortcut' doesn't appear in one of the menus up top; where is the program if I want to add it to one of the menus?

Right-click on Desktop > Create launcher > File system
Browse to 
```
usr/bin/[COLOR="Red"]And_Find_Your_Program[/COLOR]
```
That should help you figure out how to squeeze it into the menu.

---

### Post by USarge on 2008-02-15
What software did you install that didn't show up in the menus, USarge?[/QUOTE]

It was mtools.  As it turns out, I could do what I thought mtools would do, through Nautilus.

---

### Post by Het Irv on 2008-02-15
Ahh...yes the two things that everyone does when they first get Linux, Command Line and Downloading unessicary programs.  My first Ubuntu Computer had to be wiped because I downloaded about 50 programs that I never used.  I also had to run NDISWrapper, tons o' Fun.

---

