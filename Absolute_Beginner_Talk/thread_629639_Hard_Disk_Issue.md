---
title: "Hard Disk Issue"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Tikay777 on 2007-12-02
I installed ubuntu and everything was fine except from some minor issues that i managed to solve. Now though i cant seem to solve this one (at least not alone). 

I tried to copy a file from my home directory to the usr folder. To be more exact i downloaded a skin for aMSN and i tried to put it inside the Amsn/skin folder. The message i got though is that i dont have the rights to write in that folder. And i ask myself if i dont have the rights who has? (stupid joke :P)

So i went to the terminal and tried the normal solutions that popped in my head but all i got was "chmod: changing permissions of `/dev/sda1': Operation not permitted"
so i think i did something wrong during the installation.

Could you help me solving this problem? I would appreciate it.

---

### Post by skyjacker on 2007-12-02
> **Tikay777 said:**
> I installed ubuntu and everything was fine except from some minor issues that i managed to solve. Now though i cant seem to solve this one (at least not alone). 

I tried to copy a file from my home directory to the usr folder. To be more exact i downloaded a skin for aMSN and i tried to put it inside the Amsn/skin folder. The message i got though is that i dont have the rights to write in that folder. And i ask myself if i dont have the rights who has? (stupid joke :P)

So i went to the terminal and tried the normal solutions that popped in my head but all i got was "chmod: changing permissions of `/dev/sda1': Operation not permitted"
so i think i did something wrong during the installation.

Could you help me solving this problem? I would appreciate it. Try opening aMSN file in Root (sudo).

---

### Post by rob1101 on 2007-12-02
try moving the file with the command line

```

sudo cp "[I]path of file you want to copy" "path of where you want to move it"
[/I]
```

or just to move it replace *cp *with *mv*

have you tried pidgin? i believe that supports msn and it uses what ever them your window manager is using.

---

### Post by FuturePilot on 2007-12-02
> **skyjacker said:**
> Try opening aMSN file in Root (sudo).

Probably not a good idea. It could mess up some of your home folder permissions. If you need to run a graphical app as root use gksudo
Read more here
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

As for installing aMSN skins check this out
[http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Installing+Plugins+and+Skins#linusr]("http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Installing+Plugins+and+Skins#linusr")
Put them in .amsn/skins/ which is in your home folder. Notice the dot . in front. That means it's a hidden folder so press Ctrl+H to view hidden files

---

### Post by Tikay777 on 2007-12-02
Thanks a lot guys. I figured it out. Special thanks to Future Pilot his post was the closest one to what i wanted :)

---

### Post by BatsotO on 2007-12-02
you cannot write to usr (and any other directory except home) is because as normal user you don't need to write to those directory, just like in windows you wont need to put your document in win32 folder. this is not a hard drive issue, it just every directory made for specific purpose, and as normal user we only need to have full access to our account in home directory. notice that every time you install something you will be ask for administrator password because you need tho write to directories that normal user can't.

---

