---
title: "The KILL command"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Harry_Callahan on 2006-11-30
Hello to all,

I would like to know if the "kill" command should only be used for closing blocked programs? Is it a "drastic" way to close processes? I'll try to explain myself better:

Let's say when I close a program(with GUI) pressing the "x" button it saves any changes to the options of that program(example aMule). If I then use a program WITHOUT GUI(ex. amuled): if I kill amuled from terminal(kill pid), do any changes to the options get saved? 

So if the KILL command is a drastic way to close proccesses, is there any other command that let's me close(like the x button on grapichal server does) a program without GUI?


Thanks!

---

### Post by Circus-Killer on 2006-11-30
when you use the kill command, it is a drastic step. it will not save changes. i honestly dont think there is a graceful way to close a gui app from the command-line, not that i would see why you would want to.

when closing a gui app, the best way to close it is with the normal gui methods. the kill command is there for when a process stops responding.

---

### Post by Harry_Callahan on 2006-11-30
Thanks Circus-Killer,

I always use the normal method for closing GUI programs, but if a program like amuled that I run in background(no gui) and I access it from a remote computer, how do you I close it? the "x" button on the webserver only closes the webserver gui

---

### Post by Circus-Killer on 2006-11-30
well, for most programs that work in the background, they will have a command to close the program cleanly. this command will vary from program to program. 

i dont know about amule specifically though. sorry.

---

### Post by Peepsalot on 2006-11-30
Depends what signal you send with kill.

[quote=http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_01.html]
When killing a process or series of processes, it is common sense to start trying with the least dangerous signal, SIGTERM. That way, programs that care about an orderly shutdown get the chance to follow the procedures that they have been designed to execute when getting the SIGTERM signal, such as cleaning up and closing open files. If you send a SIGKILL to a process, you remove any chance for the process to do a tidy cleanup and shutdown, which might have unfortunate consequences.[/quote]

Apparently "kill -15" might be a "nice" way to quit a process from the command line.  (15 is the code for SIGTERM)

---

### Post by Rinzwind on 2006-11-30
Try
amulecmd --help

(Don't know if this works cuz I haven't got my machine with me :( sorry )

I think there's a close command in there too. So if you use amulecmd (commandline amule) you might be able to get this to work.

---

### Post by Arndt on 2006-11-30
> **Peepsalot said:**
> Depends what signal you send with kill.



Apparently "kill -15" might be a "nice" way to quit a process from the command line.  (15 is the code for SIGTERM)

That is also the default. It's the nicest way, meaning that it is an order to the program to shut itself down, but as orderly as possible. The program has to be programmed for it, though. "kill -9" on the other hand, can't even be detected by the process - the process is just stopped and removed.

Some programs can take a "kill -1" to mean "read your configuration file again".

---

### Post by Harry_Callahan on 2006-11-30
Thanks to all! amulecmd has the command to shutdown aMule without problems

@Arndt    If -15 is default, then the KILL command isn't so "drastic" afterall. Is that correct?

Regards to all

---

### Post by Arndt on 2006-12-01
> **Harry_Callahan said:**
> Thanks to all! amulecmd has the command to shutdown aMule without problems

@Arndt    If -15 is default, then the KILL command isn't so "drastic" afterall. Is that correct?

Regards to all

"As orderly as possible" doesn't usually mean "do the exit command", but that the process stops using any external resources it has acquired, shuts down subprocesses, etc. Any cleanup that can be done fast. And for programs which are not programmed to handle it, signal 15 has the same effect as "kill -9".

---

