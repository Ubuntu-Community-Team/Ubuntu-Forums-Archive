---
title: "When in Wine File how to browse to the real Windows partition?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-29
I have a program that I tried to load in Wine using the installer CD. But it keeps getting jammed in the beginning of the load at the window where it informs you what it is going to call the program and where it is going to put it. I click "ok", and it just freezes there-- won't go any further. So I thought I'd try another way to get it loaded. As I don't think this program uses the Windows registry, I thought I'd try installing it using Wine, via the same program already installed on my Windows partition. I know the pathway to the .exe file, and want to point the Wine File browser to that .exe file on the Windows partition. But when I open Wine File, I can't seem to find the *real *Windows partition. There is the fake c drive which Wine created of course, but I can't find the actual Windows partition. How do you browse to it in Wine File?

---

### Post by bogolisk on 2007-08-29
> **swarup said:**
> I have a program that I tried to load in Wine using the installer CD. But it keeps getting jammed in the beginning of the load at the window where it informs you what it is going to call the program and where it is going to put it. I click "ok", and it just freezes there-- won't go any further. So I thought I'd try another way to get it loaded. As I don't think this program uses the Windows registry, I thought I'd try installing it using Wine, via the same program already installed on my Windows partition. I know the pathway to the .exe file, and want to point the Wine File browser to that .exe file on the Windows partition. But when I open Wine File, I can't seem to find the *real *Windows partition. There is the fake c drive which Wine created of course, but I can't find the actual Windows partition. How do you browse to it in Wine File?

run winecfg and map the path to the windows drive to a faked drive letter. By examples, map /usr/local/old_win_disk to e: would map */usr/local/old_win_disk/Program\ Files* to *e:/Program Files*

---

### Post by swarup on 2007-08-29
> **bogolisk said:**
> run winecfg and map the path to the windows drive to a faked drive letter. By examples, map /usr/local/old_win_disk to e: would map */usr/local/old_win_disk/Program\ Files* to *e:/Program Files*

I opened the Wine configuration utility according to your direction, and selected the Drives tab. There I see the Drive mappings to which you refer. And by clicking on "add", the drive "E" shows up. So I guess there I just need to give the correct map to my real c:\ drive. I suppose that pathway would read like this: /media/disk/Program Files -- does that look correct? (I'm running Win 98 in the Win partition of this particular computer, and Win XP in my other computer). But I see that in the Wine Configuration Drive mappings window, one cannot type there. And the browser window that opens when you click on "browse" only sees the linux partition. So how do you get the pathway typed in or browsed to, for the new drive letter E?

---

### Post by swarup on 2007-08-30
If someone could kindly help with the problem I described in the post just above, I would be grateful.

---

### Post by bogolisk on 2007-08-30
> **swarup said:**
> If someone could kindly help with the problem I described in the post just above, I would be grateful.

The C: drive in wine is, AFAIK, hard-coded to ~/.wine/drive_c. So my guess is you don't really have a choice. You can try to copy your windowns program from the original /path/to/my/windows/c/Program\ Files/ApplicationXXX to ~/.wine/drive_c/Program\ Files/ApplicationXXX
```

$ cp -a /path/to/my/windows/c/Program\ Files/ApplicationXXX ~/.wine/drive_c/Program\ Files/ApplicationXXX

```

---

### Post by swarup on 2007-08-30
> **bogolisk said:**
> The C: drive in wine is, AFAIK, hard-coded to ~/.wine/drive_c. So my guess is you don't really have a choice. You can try to copy your windowns program from the original /path/to/my/windows/c/Program\ Files/ApplicationXXX to ~/.wine/drive_c/Program\ Files/ApplicationXXX
```

$ cp -a /path/to/my/windows/c/Program\ Files/ApplicationXXX ~/.wine/drive_c/Program\ Files/ApplicationXXX

```

Thanks! I'll try it.

Also, what about in a terminal window if I just do,

$ wine [pathway to the application in the Windows partion]\xxx.exe

That is, link wine to the .exe file that **runs** (rather than installs) the program in Windows.

Won't that work?

---

### Post by bogolisk on 2007-08-30
> **swarup said:**
> Thanks! I'll try it.

Also, what about in a terminal window if I just do,

$ wine [pathway to the application in the Windows partion]\xxx.exe

That is, link wine to the .exe file that **runs** (rather than installs) the program in Windows.

Won't that work?

Providing that windows program doesn't remember where it was installed in the original windows environment. If it does then it won't be able to load its companion files (dll, hlp, dat, bin) because wine's "C:\Program Files\ApplicationXXX" is NOT "/path/to/original/windows/disk/c/Program\ Files/ApplicationXXX" where its companion files reside.

That why I try to use the portable editions of windows programs. They have no installation information.

---

### Post by swarup on 2007-08-30
> **bogolisk said:**
> Providing that windows program doesn't remember where it was installed in the original windows environment. If it does then it won't be able to load its companion files (dll, hlp, dat, bin) because wine's "C:\Program Files\ApplicationXXX" is NOT "/path/to/original/windows/disk/c/Program\ Files/ApplicationXXX" where its companion files reside.

That why I try to use the portable editions of windows programs. They have no installation information.

ok. But there is no danger in trying it, right? At worst, it wouldn't run-- right? I mean, it wouldn't damage the original program in Windows or anything?

The fact is, I couldn't really understand what you had written in the post just prior-- the one with the long terminal command line. In order to try that, all I'd have to do is copy and paste the code line you wrote, into my terminal? (As I recall, I'd have to type in the actual pathway which I should be able to manage). What does the "cp -a " mean?

---

### Post by bogolisk on 2007-08-30
> **swarup said:**
> ok. But there is no danger in trying it, right? At worst, it wouldn't run-- right? I mean, it wouldn't damage the original program in Windows or anything?

sure
> 
The fact is, I couldn't really understand what you had written in the post just prior-- the one with the long terminal command line. In order to try that, all I'd have to do is copy and paste the code line you wrote, into my terminal? (As I recall, I'd have to type in the actual pathway which I should be able to manage). What does the "cp -a " mean?

It'd be easier for our discussion if you state "how do you access your windows directory in linux". That would make the examples more concrete. "cp" is copy: "cp -a source destination".

---

### Post by swarup on 2007-08-30
> **bogolisk said:**
> sure


It'd be easier for our discussion if you state "how do you access your windows directory in linux". That would make the examples more concrete. "cp" is copy: "cp -a source destination".

ok, but I know how to access the windows directory in linux. That is no problem-- I do it all the time. My problem is that unlike the Ubuntu browser, which when you open Places -> "disk" allows you to mount and browse the Windows partition, that option isn't apparent in Wine File.

I thought your suggestion to open the Wine Configuration utility and create a new drive representing a pathway to the Windows partition, was excellent. That seems like the easiest way. But I just don't understand how to put the pathway (/media/disk/Program Files) onto the drive screen in the Wine Configuration utility. You can't type it in, you can't browse to it and point the new drive to it, but there must be a way to just stick that in there for the new E drive somehow. I would think that would be quite straightforward. After all, people using Wine may quite commonly need to browse the Windows partition in Wine File. So how could it be difficult to do?

---

### Post by bogolisk on 2007-08-30
> **swarup said:**
> ok, but I know how to access the windows directory in linux. That is no problem-- I do it all the time. My problem is that unlike the Ubuntu browser, which when you open Places -> "disk" allows you to mount and browse the Windows partition, that option isn't apparent in Wine File.

so your "c:\Program Files" in (the real) windows is actually "/media/disk/Program\ Files" in linux.
> 

I thought your suggestion to open the Wine Configuration utility and create a new drive representing a pathway to the Windows partition, was excellent. That seems like the easiest way. But I just don't understand how to put the pathway (/media/disk/Program Files) onto the drive screen in the Wine Configuration utility. You can't type it in, you can't browse to it and point the new drive to it, but there must be a way to just stick that in there for the new E drive somehow.

if you pressed "Add" in winecfg, it should add a new entry using the next available drive letter (or our example let's say it was E). Then press "Browse" to choose what path you want to map (i.e. /media/disk). The press "Ok".

Once that was done:
[list]
[*] original windows directory "C:\Program Files"
[*] linux path "/media/disk/Program\ Files"
[*] wine virtual directory "E:\Program Files"
[/list]
would be all the same thing.


> 

 I would think that would be quite straightforward. After all, people using Wine may quite commonly need to browse the Windows partition in Wine File. So how could it be difficult to do?

I believe most ppl separate their original window hierarchy from the wine virtual hierarchy. I don't think the twos would share files very well. As for me, I don't even have a windows partition on my box.

Good luck.

---

### Post by swarup on 2007-08-31
> **bogolisk said:**
> so your "c:\Program Files" in (the real) windows is actually "/media/disk/Program\ Files" in linux.

if you pressed "Add" in winecfg, it should add a new entry using the next available drive letter (or our example let's say it was E). Then press "Browse" to choose what path you want to map (i.e. /media/disk). The press "Ok".

Once that was done:
[list]
[*] original windows directory "C:\Program Files"
[*] linux path "/media/disk/Program\ Files"
[*] wine virtual directory "E:\Program Files"
[/list]
would be all the same thing.

Thanks. This is extremely helpful. I tried making the new pathway in wincfg to be able to get to the Windows partition, and this time it worked. I'll try loading the program located on Windows using this tool today, and see how it goes.

---

### Post by swarup on 2007-09-05
> **bogolisk said:**
> so your "c:\Program Files" in (the real) windows is actually "/media/disk/Program\ Files" in linux.

if you pressed "Add" in winecfg, it should add a new entry using the next available drive letter (or our example let's say it was E). Then press "Browse" to choose what path you want to map (i.e. /media/disk). The press "Ok".

Once that was done:
[list]
[*] original windows directory "C:\Program Files"
[*] linux path "/media/disk/Program\ Files"
[*] wine virtual directory "E:\Program Files"
[/list]
would be all the same thing.



When I open winecfg and click "Add" in the drive window, then click on "browse", there in the browser window under /media there is only /media/cdrom and /media/cdrom0. Why doesn't "/media/disk" appear there? 

On the other computer in which I initially checked this (see post just above), /media/disk is there in the winecfg drive browser window. But on THIS computer on which I need to do the work, under "/media", "/disk" is not appearing there. Why is that, and how can I get this /media/disk/ pathway added to the drive in winecfg so I can then access the Windows partition using winefile?

---

### Post by amirman on 2008-05-18
hey, i'm trying to do the same thing here, my windows partition shows up in wine's file browser however, you should look into editing your fstab file in linux to automatically mount your windows partition at startup.

---

