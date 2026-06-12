---
title: "gdesklets grey screen bug!"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by aata on 2007-07-03
HELP!
my gdesklets refuses to start! 
what do i do? i believe its that same grey screen bug thats been reported in launchpad, but none of those solutions, along with several others i located, work! when i start gdesklets in the terminal, it takes its time saying ´connecting to daemon´, after which it gives me this error message:

```
Starting gdesklets-daemon...
Connecting to daemon [        ###  ]
==========================================================[07/03/07-11:09:11]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/local/bin/gdesklets: line 399 <module>
in /usr/local/bin/gdesklets: line 273 parse_command
in /usr/local/bin/gdesklets: line 177 __open_profile
in /usr/local/bin/gdesklets: line 158 __client_daemon
in /usr/local/lib/gdesklets/main/client.py: line 288 get_daemon
[EXC]/usr/local/lib/gdesklets/main/client.py

[---]  283                 daemon = connection
[---]  284                 if (daemon):
[---]  285                     break
[---]  286             except socket.error:
[---]  287                 pass
[ERR]> 288             time.sleep(0.1)
[---]  289 
[---]  290         print "\r" + " " * 40 + "\r",
[---]  291 
[---]  292         if (not daemon):
[---]  293             sys.exit(_("Cannot establish connection to daemon: timeout!\n"
[---]  294                         "The log file might help you solving the problem."))

```

i have tried replacing the /usr/lib/gdesklets file with the corresponding one from the synaptic deb package, but that doesnt work either. and compiling from the source code give pretty much the same error. i need help!

f=im running fiesty fawn 7.04.
if you need any more details, just reply to the post.
thanks in advance.
aata

---

