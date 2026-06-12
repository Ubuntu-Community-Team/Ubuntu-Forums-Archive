---
title: "Horrible uninstall problem"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-08
Hi there. I'm very sorry to cross post like this, but I'm having something of a problem with Sunbird.

I followed instructions in this [[COLOR="Blue"]THREAD[/COLOR]]("http://ubuntuforums.org/showthread.php?t=278206"), and everything went fine, until I tried to start the program. It has never run, and seems to have prevented the Synaptic version of the program from installing and running correctly.

I have made a post in that thread, right at the [[COLOR="Blue"]END[/COLOR]]("http://ubuntuforums.org/showthread.php?t=278206&page=10") of course, but it doesn't seem to be getting much attention, and I'm starting to get a little jittery since I have no idea how to uninstall a program at the moment, and I very much need my calendar, which means of course that I have to keep swapping back and forth to Windows.

Any help would be very gratefully received, and once again, I apologize for cross posting like this.

Max

---

### Post by PmDematagoda on 2008-01-08
If you compiled the application, try running this in the folder containing the source:-
```
sudo make uninstall
```

---

### Post by MaxVK on 2008-01-08
No, I didn't compile the program, and Iv already tried that, failing miserably! :(

The instructions I followed are shown in that link, and there was no compiling of programs, just unpacking from an archive.

---

### Post by kellemes on 2008-01-08
Just reverse the howto in the thread you followed..
Delete the /opt/sunbird directory..
Delete /usr/bin/sunbird.sh
Delete /usr/share/applications/sunbird.desktop
Maybe you got "sunbird-0.7rc3.en-US.linux-i686.tar.gz" somewhere, you don't need this anymore, so you can delete it also.
And you should be done..

Simply instal sunbird using synaptic..

Edit: By the way, when sunbird keeps on giving trouble, try to run it from the commandline by typing "sunbird" (probably), you'll get some output that may give some info.

---

### Post by MaxVK on 2008-01-08
Thanks kellemes. I didn't know that you could just delete the folder like that.

However, now that the folder and the archive have gone, and I have installed Sunbird from Synaptic, no icon appears in the menu system, and when I run it from the command line I get the following message:

> *** Calendar schema version is: 7
Starting calendar alarm service
observer added
observer added
*** glibc detected *** /usr/lib/sunbird/sunbird-bin: munmap_chunk(): invalid pointer: 0x08a67290 ***

This is followed by quite a few pages of blurb, and is finally ended with this:
> 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


I do hope that Iv not trashed Sunbird for good because I was counting on it to help my shift from Windows.

---

### Post by MaxVK on 2008-01-08
Well Iv been back and forth with this all day today and I'm getting nowhere fast. Iv hunted these forums and Googled as well, and nothing Iv read fixes the problems.

Iv just been looking through Synaptic and found that when I check the properties of Sunbird (installed or otherwise), there is a conflict with libnss3, which is installed.

I have no idea what (If anything) I can do with this snippet of information, or if this is indeed the cause of the problems. I'm certainly not going to start messing with libnss3, since although I can read the description, I have no idea what it actually does!

I refuse to believe that Sunbird can be the downfall of my change to Ubuntu, but Iv spent more time in Windows today so that I could use my calendar, and what time I have spent in Ubuntu has been wasted trying to sort this seemingly insane problem out.

---

### Post by d_fiant_1 on 2008-01-08
If you install Sunbird through synaptic, doesn't it automatically add dependencies and remove conflicts?

I am only a newbie too, but I prefer to install programs through synaptic rather than through a terminal because of this.

---

### Post by MaxVK on 2008-01-08
I thought it was supposed to do that, but apparently it doesn't, or at least not in this case.

---

### Post by kellemes on 2008-01-08
Is there a specific reason for wanting to use Sunbird?
I mean, there are a lot of other calendar-programs for GNU/Linux, and there a lot that are much better. Sunbird is rather early in it's development as I understand it.
Couple of options..
[Evolution]("http://www.gnome.org/projects/evolution/")
[Kontact]("http://www.kontact.org/")

---

### Post by d_fiant_1 on 2008-01-08
If it is any help, I am using Thunderbird with the Lightning extension, I don't know what Lightning is like compared to Sunbird, but they sound similar.

I prefer to use Thunderbird over evolution because I am more familiar with thunder, but its just a thought

---

### Post by MaxVK on 2008-01-08
I really don't get on with Evolution at all, which is why I don't want to use it, and Iv tried the Lightning plug in for Thunderbird (Which is my mail client) and found that it is a bit.. um.. odd! It IS Sunbird, but then again, its not!

I use Sunbird on my Windows install, and figured that it would be sensible to use it in Ubuntu because I can point it at the correct .ics calendar file and have the two OS's share the calendar. This is the main objective, since I still have to use Windows here and there for work, and sharing the calendar (As I'm currently sharing Firefox bookmarks and Thunderbird mail) is pretty much a requirement.

Thanks for the link to Kontact - Ill check it out and see if it can be pointed at the calendar file.

---

### Post by MaxVK on 2008-01-08
Unfortunately Kontact doesn't look like something Im likely to use. Its a bit heavyweight for what I want to do and I'm certainly not going to start using it as a mail client, since I'm happy with Thunderbird.

I just had *another* look through Evolution, but there seems no way to have it load my shared ics calendar file, so thats out as well.

I'm starting to feel a bit panicky all of a sudden! I was banking on being able to make this move away from Windows, but its looking as if I might as well have stayed with it.

Does anyone have any other suggestions for a suitable calendar app?

---

