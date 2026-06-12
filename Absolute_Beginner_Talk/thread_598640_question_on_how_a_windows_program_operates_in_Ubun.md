---
title: "question on how a windows program operates in Ubuntu"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Kymus on 2007-10-31
I am interested in technical details here.

I use a program called ConvertXtoDVD to convert avi files to a DVD format and burn it all to disk. However, this is a windows program, so I run it with WINE.

Thankfully, it runs beautifully in Ubuntu (though I'd like to hear some suggestions on linux-native programs that do the same thing that allow me to edit context menus, etc.). This program supports the option of speeding up the conversion process by using more system resources. When maxed out, windows goes into slowmo and it's impossible to use windows functionally until the conversion is over due to the drain on system resources. I found out the other day, however, that when I do this same thing in Ubuntu, the speed is just as fast but I don't experience any visible system slow-downs.

Why is this?

---

### Post by Jaco Du Toit on 2007-10-31
I guess that Linux handles threads better than windows. Simplistically each program you run does so in a thread, and your cpu schedules time for each running thread. Usually when programming threads it is customary to insert so-called thread-sleeps into the program, basically telling the program to give control back to the operating system for a fraction of time. The operating system then uses this fraction of time to process other threads from other programs or events (such as mouse clicks or windows being moved etc)

Now it sounds like the application you are running to encode the DVD's is basically consuming as much resources as it is able to take from the operating system, which in Windows means that by default it takes all of the cpu time and gives the operating system as little as possible back - hence the apparent slow down of the interface. (It is possible in Windows to tell it not to give any single process more than a certain percentage of the cpu, but this is not set by default)

Now I think (and this is pure speculation on my part) that Linux just handles situations like this better. Perhaps it is somehow able to force the running process in wine not to consume absolutely every last bit of CPU time.. or perhaps it allocates a certain amount of resources for wine which in turn then passes this onto the application, and the application can then never exceed the initial pool of resources allocated? 

(Incidentally to convert media files in Linux take a look at a package called transcode)

---

### Post by Kymus on 2007-10-31
interesting, thanks :)

---

