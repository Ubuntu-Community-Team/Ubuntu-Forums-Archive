---
title: "Can't open any folders on my desktop"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-01-15
I thought it was just an SSH problem.  Now, if I click any folder on my desktop, I get 

[B]Opening "foldername"

You can stop this operation by clicking cancel.[/B]

Any idea what the problem might be?

All I can do is click cancel, which puts me back to square one.

In fact, I can't open any folders anywhere - to use files I have to use Terminal to move them out of a folder onto the desktop.

My GUI seems to be breaking down.

Thanks.

---

### Post by cmittle on 2008-01-16
I'd guess that you do not have permission to view these folders you are trying to open.  Did you create these folders as a different user?  Can you open them as superuser?

---

### Post by pedbsktbll on 2008-01-16
No, that's not it all. I'm running feisty and I've just noticed the exact same problem. I'll use the 'connect to server' to connect via ssh to a remote server... Occasionally, while I'm browsing through the server, it will take a while to load the contents if a particular folder.. so I'll just close it. I notice that later I can no longer open any folders using the GUI (be it home folder, the filesystem, etc.). 

The only solution I have found is to just completely restart the x11 session (control+alt+backspace). Then the problem is solved until it occurs again...

The entire desktop also becomes unresponsive. I've used the shell to save files to the desktop, but they will not appear until the desktop is restarted.

Any ideas on this?

---

