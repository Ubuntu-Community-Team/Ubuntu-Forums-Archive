---
title: "when I'm logged in directly or via ssh, I can't log out"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-06
When I try to log out, the process just "hangs".

Note:  This ONLY happens on SSH when I run forward some X windows, so I'm guessing this is related to the GUI.

What should I do?  Where should I start?

---

### Post by The Cog on 2008-02-06
Close the X window and your ssh login will then also close. Or close the tereminal window that you are running ssh in, and that will also brutally kill the X application.

ssh is remaining open in order to keep the X tunnel open. The fact that your interactive login has finished doesn't mean a lot, because ssh knows it's carrying other connections (X) too. It won't close until they're all gone.

P.S. 
If the X session is the only reason for opening an SSH connection at all, then you can do something like this: Press Alt-F2 to get a "run application" prompt, and then enter the command:
ssh user@server xeyes
and then you don't get the annoying console window.

---

