---
title: "Multiple (same) processes"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Sitix on 2007-06-06
I've been using Ubuntu for over a year already... but I think ever since I moved to Feisty it started doing weird things with the processes. Like, right now I have about 10 apache2 processes, 5 getty processes, 2 dbus-daemon processes, 2 gdm processes, etcetera. If you ask me, it pretty much looks like a waste of RAM and CPU. The longer my computer is running, the more of the same processes open. Note that it's mostly with the processes I named.

By the way, if I close all the processes except one, it doesn't give an error or something... it keeps working properly. So I think it's okay to conclude the processes aren't necessary for the computer to run properly. I've been playing around with it, but can't really find out why it's opening several processes for one task.


Thanks in advance for the answer!

---

### Post by pmg on 2007-06-06
First, how are you seeing them?  In some cases, they may be threads and not processes.  But regardless, you don't need to worry about them.  Let the system manage itself.

Many parts of the system (or applications) will start new processes/threads as they are needed.  They may start a "child" process or thread to do work which may go away when the work is done, or may stay around for a while in case more work arrives.  The apache web server, for example, will start  some preset number of "workers" to handle requests, and may start up more as needed (up to a configured limit) to handle web requests.  dbus-daemon is the [D-Bus message bus daemon]("http://www.freedesktop.org/software/dbus/").  The **getty** processes are to allow you to login to the alternate consoles (Atl-Ctrl-F1 thru Alt-Ctrl-F6.)  **gdm** is the Gnome Display Manager which is sort of the window manager for the Xserver.  You are right, in some cases killing them will have little to no affect (they will just be restarted) in other cases you're going to eventually cause yourself problems.

One thing that might help you feel better is knowing a second instance of a process is not using as much resource as the first one.  For example, all the text (i.e. executable code) is only in memory once and is shared between the two copies.  If a process "forks" a child, even their common data in memory can be shared (until one of the processes modifies it and the kernel has to make an independent copy.)  If they really are threads in the same process, all (well, most) of the memory is shared.  If something, really isn't doing anything and your system runs short on memory, the thing not doing anything is what will be paged out to swap space, not the processes that are activly running.

If your apache server doesn't do much you may want to check your config and reduce the number of connections it's ready to accept, but other then that just leave it alone and let the system manage itself.

---

### Post by Sitix on 2007-06-07
Okay, at certain moments I feel like having a flash back to my Windows experience: not enough memory. In fact, I only have 256 MB shared memory, so about 16 to 32 of that goes to my video memory. Sadly, I don't have the money to buy a new computer soon. So that's why I'm mainly trying to keep the RAM use down.

But thanks for your answer, it's good to know that the amount of processes isn't a time bomb effect that sooner or later makes my computer crash :P

---

