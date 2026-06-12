---
title: "nubie please help install downloaded games"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by 200proofhonky on 2008-03-12
just got ubuntu yesterday,please help!!!:(most everything else has been cool but i just downloaded 2 games and they r in a zip file now...is this right???...cant figure out how to run?..is it the app files?..or the exe files?..im lost...thanks for any help!:)

---

### Post by PeterJS on 2008-03-12
Well zip files are the same under ubuntu as they are on windows, they're just compressed archives that contain stuff. You'll probably want to extract the contents of the zip and see what's inside.

As for .exes, those are windows executables, they're designed to run on windows. There is software for ubuntu called wine that can run some windows software, but it's kinda hit or miss, it's getting better everyday the developers are still fumbling forward blindly as fast as they can.

Your best bet for specific help with the stuff you downloaded is post the links here and we'll take a look at what you've got.

---

### Post by duruttye on 2008-03-12
If they are games for windows, they, most probably wont work, anyway search google like: game name ubuntu, see what that returns!

Maybe you could tell us the name of the game you want to try out.

good luck

edit:
PeterJS is more optimistic in using wine, then me :))

---

### Post by red_Marvin on 2008-03-12
If it is .exe files you cannot run them like normal linux programs, since gnu/linux does not have the same program format as windows.

However some games work with [wine]("apt:wine") (<- click to install) and then you would run the program by right clicking on the .exe and choose run with wine.

But before doing that I suggest that you read [this]("https://help.ubuntu.com/community/Wine") since wine is a little tricky.

If you want games that work without problems in linux you can always check out Program menu -> add/remove -> games...

---

### Post by Shazaam on 2008-03-12
Ubuntu (linux) can't run .exe files. Those are Windows only. To get .exe files to work (and not all of them do) you would have to install wine (Wine Is Not an Emulator) from the repositories. There are NO guarantees that ANY of your Windows based programs will work with wine.
As an aside, most programs that you need (with a few exceptions) can be installed using the Synaptic Package Manager (System>Administration>Synaptic). Look in System>Help and Support for info.

---

### Post by PeterJS on 2008-03-12
> **duruttye said:**
> 
edit:
PeterJS is more optimistic in using wine, then me :))


Optimistic? I certainly didn't mean to give that impression. I was going more for sometimes, more so with popular games and programs (steam and photoshop I'm looking at you), but not the sort of thing I'd bet on, and that it's a small miracle that it works at all.

---

### Post by 200proofhonky on 2008-03-12
[http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/)

wow!!! u guys r fast,thanks every1.....they were in linux top 10 games search on google.So since they r linux games i should extract the app. files then?? r app. files to linux what exe. files r to windows?....again thanks evry1 for all info.......not sure what other games to try,just want some easy ones for my young kids (5-6yr olds) and some cool shootem up for me....

---

### Post by PeterJS on 2008-03-12
.app files are generally Mac applications folders and are their own thing separate from every other executable file format known to man, because they aren't actually files, but directories. As for what file extension linux uses to denote executables, it doesn't.  Executables are denoted by having their execute bit set, and generally being located in a bin folder. The .sh extension is used for shell scripts which are executable text files that are a lot like windows batch files.

To install nexuiz, open up the package manager, System > Administration > Synaptic Package Manager, search for nexuiz, right click and mark it for installation, and then apply your changes.

EDIT
And in the future if you're looking for stand alone software for ubuntu, you'll want to try and get it in the .deb package format.

---

### Post by 200proofhonky on 2008-03-12
hey guys,...tryin to install using synaptic package manager but the only way i can locate the file is to click "search"....when i do this it does find it but it pops up in right hand side window and will not let me right click on it or choose "mark for installation" from the "package" tab up top by the file,edit,settings,and help tabs.Any info or alternatives would be great......thanks.

---

### Post by PeterJS on 2008-03-12
Well you could try installing it with apturl [ with this link](apt://nexuiz), or from the terminal with:
```

sudo apt-get install nexuiz

```

---

### Post by 200proofhonky on 2008-03-12
ok guys,im up and runnin!!! thanks for all the help! if anyone should ever have this problem use the synaptic package manager,if you cant find your folder/file/whatever your looking for then click on settings then repositories and check all the boxes in the repositories to allow them and once youve exited settings click reload and then you should be able to right click on it and mark for installation......NOTE;the screenshots i viewed to help me with this were a little different than mine.VISIT THIS LINK FOR THE SCREENSHOTS....[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)     

when you reach this link scroll down to ENABLING EXTRA REPOSITORIES...this will be the part you need to look at.



thanks again to every1 here....GODBLESS!


dont know how things work here yet but if theres a moderator that closes threads when solved then......

CLOSE THREAD........PROBLEM SOLVED!!!!:guitar:

---

