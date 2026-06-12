---
title: "Synaptic Package Manager Not Uninstalling Programs Completely"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-10
I've just noticed this afternoon that when using Synaptic, and if I choose a program and select to "Mark for complete removal" , according to Synaptic, it completely removes the program.  OK, sounds good to me...

But then I was strolling thru my Home directory, and happen to notice a lot of directories that start with a period, and they have names of programs that I supposedly completely removed...   For example, I installed Enlightenment and messed with it for a bit, and decided it wasn't for me.  So, I "Mark for complete removal", Synaptic does it's thing, and I think all is well.  But, now I notice a directory named .enlightenment, with a total size of 397KB.   

My question is this:  what's going on here?  Is there something wrong with my Synaptic program, or is this normal behavior?   If it is normal, why does it do this?  If I want something completely removed, I want it completely gone from the hard drive, not wasting space that could be used for something else, right??

Thanks.

FwF

---

### Post by lloyd_b on 2008-03-10
> **FreewareFan said:**
> I've just noticed this afternoon that when using Synaptic, and if I choose a program and select to "Mark for complete removal" , according to Synaptic, it completely removes the program.  OK, sounds good to me...

But then I was strolling thru my Home directory, and happen to notice a lot of directories that start with a period, and they have names of programs that I supposedly completely removed...   For example, I installed Enlightenment and messed with it for a bit, and decided it wasn't for me.  So, I "Mark for complete removal", Synaptic does it's thing, and I think all is well.  But, now I notice a directory named .enlightenment, with a total size of 397KB.   

My question is this:  what's going on here?  Is there something wrong with my Synaptic program, or is this normal behavior?   If it is normal, why does it do this?  If I want something completely removed, I want it completely gone from the hard drive, not wasting space that could be used for something else, right??

Thanks.

FwF

This is perfectly normal.  When you tell Synaptic to remove a program, it removes everything that was created when you installed the program initially.

What it *doesn't* do is remove any files that were created by the program.  Those ".something" directories weren't created by Synaptic, but were created by the *program* (usually to store user-specific configuration info, but the usage of such files/directories varies depending on the program).

Lloyd B.

---

### Post by handydan918 on 2008-03-10
That's normal behavior. If you look at what is in the .enlightenment folder, it is not any of the things that are handled by a package manager. IIRC, it contains your personal prefs and settings for enlightenment. 
"Completely remove" just means uninstall and clear out the configuration files while you're at it. This option is useful if you bork the config on an app and reinstalling doesn't fix it.
If you want to be miserly about disk space,, learn some cli stuff like ```
locate
``` 

Oh, yeah. And "Completely Remove Windows"



:rofl:

---

### Post by FreewareFan on 2008-03-10
Well, thanks to you both for clearing that up for me...  I was under the impression that when I told Synaptic to completely remove something, it removed EVERYTHING related to that program, whether Synaptic installed it or not...  Live and learn.  

Now, as far as this comment:

> **handydan918 said:**
> 
If you want to be miserly about disk space,, learn some cli stuff...

You might call it being miserly, but I call it being prudent to use all available space.  

Again, thanks to both of you for the explaination.

FwF

---

### Post by handydan918 on 2008-03-10
> **FreewareFan said:**
> 
You might call it being miserly, but I call it being prudent to use all available space.  
FwF

No offense intended...just my rather dry sense of humor.

---

### Post by FreewareFan on 2008-03-10
I wasn't offended.   I did thank you, after all...   No problems here!

FwF

---

### Post by SunnyRabbiera on 2008-03-10
yeh think of the .something files as the application data folder in windows, even windows leaves folders and stuff behind but its not as upfront (you have to dig around to see the extra profile stuff that programs have placed about in the drive)

---

### Post by CSMatt on 2008-03-10
Yep.  In Windows XP it's in C:\Documents and Settings\[User]\Application Data\[Program Name[ or C:\Documents and Settings\All Users\Application Data\[Program Name].

---

