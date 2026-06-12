---
title: "So I have Wine installed, what can I run with it?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-17
Ia there a comprehensive list of .exe files that will run with Wine installed? or is it jsut a "Try it and see what happens" type thing?  I want to load Google Chat, etc.

---

### Post by halfvolle melk on 2006-03-17
You can always try and see what happens. However here you can find stuff that's supposed to work:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by ubhobbes on 2006-03-17
I have wine installed. Is it possible for me to run an exe directly off of the windows XP partition on my HDD? From what it looks like to me, wine/cedega installations copy the files to a virtual "c:\program files" folder under ubuntu. So, couldn't it be run strait from the directory it's already put on? or perhaps if need be, create a map to that partition/directory in the wine/cedega 'virtual folder'?

There are a few programs that I use all the time under winXP that are preventing me from making any kind of primary switch to ubuntu. Yes, I've seen the "equivalents" list, but these are programs I cannot substitute.

Any help or points in the correct direction would be greatly appreciated. I spend hours searching on these forums all the time, trying to find what I'm looking for.

---

### Post by halfvolle melk on 2006-03-17
As far as I know you can not. You will need to install the programs you want to use through Wine, and maybe simulate a reboot (LOL).

edit:
> 
There are a few programs that I use all the time under winXP that are preventing me from making any kind of primary switch to ubuntu. Yes, I've seen the "equivalents" list, but these are programs I cannot substitute.
Which programs?

---

### Post by Roland Arnold on 2006-03-17
*Some* programs will in fact run if you simply browse to where the program is installed on your windows drive and you run it with wine (typically from the command line). WinRar or Textpad are good example of this, but of course they act as unregistered programs with this setup. It *should* be harmless to browse around and try to run all the main programs in C:/Program Files/ to see what runs, but don't expect too much. Programs with any sort of copy-protection tend to break - they need the registry information sitting in your windows drive's registry.

---

### Post by jam'ez on 2006-03-17
wine is good, but doesnt run everything. so i tend to use Crossover. this runs everything i need and i was lucky enough to have a copy! :)

---

### Post by ubhobbes on 2006-03-18
As part of my job, I am required to be able to run different FPS games. I edit, test and administrate some online game servers. Call of Duty 2 is one. I also use a VOIP program called Ventrilo to communicate with other modders, admins, etc.

I also only alotted 4.5 GB to Ubuntu's partition when installing it. Cod2 is 3.5 GB and my ubuntu partition is already partly full. Was hoping to be able to run it without having to clear room on the disk, then re partitioning it.

Maybe I just have to stick with Windows. Thanks for your replies.:)

---

### Post by GreyFox503 on 2006-03-18
If you need to enlarge your root partition, or create a new one, Gparted can do it without losing any data.  Give it a try, it's in the repositories.  Just be careful with it.

---

