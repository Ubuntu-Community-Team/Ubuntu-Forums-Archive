---
title: "show cpu usage"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Snoopy381 on 2006-10-29
is there a command in ubuntu to just show the cup usage by it self. eg:

#unknowncommand

cpu usage is 55%

ps -aux shows all the processes and their cpu usage but i dont want to have to add up all the precesses cpu uaseg to get a total. is there a command that will just give me a simple % answer for all process running on the system combined?

---

### Post by podunk on 2006-10-29
I don't know a command, but there is a little graphical thingies. System>Administration>System Monitor

It shows CPU load, memory, bandwidth, swap - stuff like that.

---

### Post by Snoopy381 on 2006-10-29
yeh i know iv seen it. thats what made me think there was most likley a command line way of doing it.

---

### Post by Coelocanth on 2006-10-29
If memory serves (I've been reading a bit about Linux commands lately), xload will bring up a graph, but I don't know if there's a command to get just a % value output.

---

### Post by Snoopy381 on 2006-10-29
i tried it and xload does bring up a graph like you said. but im dure there is a way of getting a % value, .....i remember doing it an old red hat bax years ago while reading the command out of a book.

---

### Post by d3v1ant_0n3 on 2006-10-29
'top' will show you CPU usage, along with memory, and  processes using the most CPU and memory.

Hope that helps:D

---

### Post by Snoopy381 on 2006-10-30
> **d3v1ant_0n3 said:**
> 'top' will show you CPU usage, along with memory, and  processes using the most CPU and memory.

Hope that helps:D

thanks, thats exactally what i wanted.


come to think of it, that was the command i used ages ago on red hat, thanks. :D

---

