---
title: "How to install WBAR"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by bhougland on 2008-03-02
Hello-

I am a total newbie when it comes to Linux and Ubuntu and was wondering if I could get some help installing and setting up WBar.  I realize that this is a big request and I have seen many instructions on the net, but most of them assume the user has a bit more knowledge than a total linux newbie.  For example, I am having trouble after I download the Deb file, where do I extract the file?  (Yea, that how much of a newbie I am)

Can Anyone help with this?

---

### Post by Zeroangel on 2008-03-02
Well for ubuntu, a *.deb file is equivalent to a setup.exe file from Windows. In most cases you should just have to double click on it, and it will launch the installer.

I havent personally seen WBAR, so I dont know if it depends on any other packages  which are not in the Ubuntu repositories. 

If it doesnt work, then post the error here.

(FYI: programs and program components are sometimes called 'packages'. And they usually come in  *.deb format. Repositories are things that you can set up, so that linux can download and install things for you automatically if you run a text-command like "sudo apt-get programname".)

---

### Post by eriqjaffe on 2008-03-12
If you got the .deb from [here](http://code.google.com/p/wbar/downloads/list) and double-clicking it doesn't install it, you can install it from the terminal (navigate to the directory the .deb is in first, or just preface the deb name with th /path/to/it):

```
sudo dpkg -i wbar_1.3.3_i386.deb
```

I've installed that very .deb on Feisty and Gutsy without any dependency issues at all.

---

### Post by likemindead on 2008-03-21
After you install the .deb package, then what? Where does the launcher end up (or is there one)? Thanks....

---

### Post by larryfroot on 2008-03-21
A good point....how do you launch it?

i am curious about wbar, but it will have to be good to beat my personal experience of cairo-dock. As far as wbar goes, I typed wbar into a terminal and got the message 'Using a Super Bar'. Well it might be using a super bar, but I'm b*****y well not. Ah well, lets hunt around the hidden folders in my home directory, might show up there, stuff sometimes does....

Whoops! just found it hiding under the bottom panel as well as a couple of open apps on my laptop desktop - cairo-dock is on my box...looks like wbar in a terminal starts it. But if I had a wider bottom panel I would have missed it!

---

### Post by Huss on 2008-03-30
Launching, humm.

I've found the same thing. I've 'launched' it in terminal and haven't been able to find the super bar. I have run several different options from the wbar -help list but no luck. Wbar, where are you hiding?!

---

### Post by Huss on 2008-03-30
Great. I just had to click where the bar would be and then it started working. Now will work on having the bar above apps - the 'above-desk option doesn't work ... yet

---

### Post by eriqjaffe on 2008-03-30
> **Huss said:**
> Great. I just had to click where the bar would be and then it started working. Now will work on having the bar above apps - the 'above-desk option doesn't work ... yetAFAIK, "above-desk" won't float wbar above applications, it's just supposed to float it above your desktop.  I ran into issues with that trying to use it with PCManFM - I'd launch "wbar --above-desk" and it'd pop up, but as soon as I clicked anywhere but on the wbar dock, it'd disappear behind the PCManFM desktop.

---

### Post by Huss on 2008-03-31
Thanks for the quick reply.

I've got it working nicely now. The only bug left to tweak is that part of my desktop image also hovers above all the applications. Will post when I figure it out.

---

### Post by Huss on 2008-04-01
Wbar was nice, but the only way I managed to get the transparency working was by changing to avant window navigator (AWN).

---

### Post by FreewareFan on 2008-04-01
Might I suggest Kooldock?  It installs from Synaptic just fine, has great eyecandy, and is a breeze to configure.  Try it, you might like it.....

---

### Post by eriqjaffe on 2008-04-01
Yeah, wbar uses a pseudo transparency - change the wallpaper and it becomes obvious unless you kill and restart wbar.

---

### Post by zmjjmz on 2008-04-01
Will kooldock work _without_ KDE?
EDIT: Apparently not, I tried...

---

### Post by FreewareFan on 2008-04-01
Works just fine for me on Ubuntu 7.10.    Did you install it from Synaptic?

---

### Post by Huss on 2008-04-18
Well, I've settled on Cairo-dock. It's much more configurable than advant and is just as stable. Having said that, it's not perfectly stable - it does close down/crash when mounting different drives.

---

