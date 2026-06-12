---
title: "Linux Newbie needs help configuring Wine."
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by bakumatsu on 2006-05-19
Alright. Here goes. First post, a cry for help. So, I just started out on Linux, yes I know. It's not meant to be like windows. But I want to run some windows apps (specifically some emulators ) and figured I'd try using Wine. So I did what thier user guide said all good, I was going good. Then they said to run it just type in winecfg in the console. Alright. So I did that. And here's what came up. I gather it's some sort of error, but I have no idea what I did wrong. Someone please help me. I'm at a total loss. 


bakumatsu@linksys:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/bakumatsu', starting in the Windows directory.

sizeof(RADEONDRIRec) == 100, devPrivSize 100
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

sizeof(RADEONDRIRec) == 100, devPrivSize 100

Someone Help!

---

### Post by S{yndrom}e on 2006-05-19
how exactly did u install wine? Because if you use a automated script like automatix or whatnot it installs it automatically for you, and the winecfg works fine. 
Try chmod +x /media/windows/system32 if it is a permissions problem

---

### Post by slimdog360 on 2006-05-19
Im not 100% sure but, Id say the first part is because your windows partion is NTFS and it cant modify it very well. The second part with the RADEON text, I cant say for sure as I have nvidia in my system, could be some graphical conflict with the ati card, Ive heard linux has that problem sometimes. 
If you want to run a windows app just type

wine nameofexefile.exe

---

### Post by halitech on 2006-05-19
the best explanation I've found for installing WINE and getting it set up is here

[]("http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine")

I've used it twice to install (first time when I installed and second time when Ubuntu barfed upgrading to Dapper) and both times worked like a charm.

---

### Post by bakumatsu on 2006-05-20
Um. I think there was supposed to be a link that didn't show up. So can you please repost that?

---

### Post by bakumatsu on 2006-05-20
[QUOTE=S{yndrom}e]how exactly did u install wine? Because if you use a automated script like automatix or whatnot it installs it automatically for you, and the winecfg works fine. 
Try chmod +x /media/windows/system32 if it is a permissions problem[/QUOTE]

bakumatsu@linksys:~$ chmod +x /media/windows/system32
chmod: cannot access `/media/windows/system32': No such file or directory

Well since this doesn't seem to be working someone want to guide me through the entire install process? I'll uninstall it, and try agian, oh and the first time I did it was using synaptic package manager. I downloaded the package that auto installs it. Using the repositories given by the wine website. It apparently didn't work.

---

### Post by S{yndrom}e on 2006-05-20
check out automatix, it is an automated script written by arnie boy that automatically downloads, and installs programs. On this list is Wine. All i did was selct wine to be installed and afterwards typed winecfg and everything worked fine. Check it out somewhere in the HOWTO section in the stickies.

Or try sudo apt-get install wine

---

### Post by Ecthelion on 2006-05-20
[QUOTE=S{yndrom}e]how exactly did u install wine? Because if you use a automated script like automatix or whatnot it installs it automatically for you, and the winecfg works fine. 
Try chmod +x /media/windows/system32 if it is a permissions problem[/QUOTE]

I can be wrong but i though that wine files are in
/home/**username**/.wine/

So if you try chmodding it should be to
/home/**username**/.wine/drive_c/windows/system32

At least that's where mine are. Of course it could be that you mounted your wine-c drive as windows, and then i'm sorry to bother.

---

### Post by S{yndrom}e on 2006-05-20
Etechilion is right, when i say the C: in the error output i automatically assumed it ment the windows partition which is loacted under media. But he is right, wine files are located in a hidden folder in your home. So yea chmodding them would fix it.

---

### Post by stalefries on 2006-05-20
This is a HOWTO posted on these forums. Enjoy!

[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

---

