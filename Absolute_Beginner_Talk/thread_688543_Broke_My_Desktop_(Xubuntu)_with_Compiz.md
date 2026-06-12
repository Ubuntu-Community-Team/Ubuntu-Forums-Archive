---
title: "Broke My Desktop (Xubuntu) with Compiz"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jeffk14 on 2008-02-05
Tried installing compiz on my old emachines T1100 running Xubuntu per [this link]("http://xubuntublog.wordpress.com/?s=compiz"). When I tested it, everything was "glitchy" with flickering pointer, small (about 1 inch) windows lingering after closing them, etc. I never did the steps that cause compiz to start on startup, so when I didn't like the way it looked, I restarted the computer. On restart, the 4 workspaces on my bottom panel went away & I got about a 3" X 5" black window (almost like a terminal, but no prompt) in the upper left of my desktop. I reopened synaptic, completely removed all the packages that I installed for compiz, then restarted. No help. Still no workspaces shown & still have the black window. When I go Applications>Settings>Window Manager, I get an error message saying that my window manager is unknown. I think this may be related. I tried search, but couldn't find this exact same problem anywhere.  Please help.

---

### Post by kernel tom on 2008-02-05
try this

start ur computer, but go into a non-desktop session... hit ctrl+alt+f2 to do that after logging in

this next part assumes you are connected to the internet

sudo apt-get install xubuntu-desktop
then reboot

worth a shot.

if not try

sudo apt-get install xubuntu-default-settings

-kt

---

### Post by jeffk14 on 2008-02-05
Thanks, I'll try that tomorrow morning when I'm home & report my results.

---

### Post by jeffk14 on 2008-02-06
I solved it by following the tip from Vincent over on his xubuntu blog. Apps->Accessories->Thunar File Manager, opened the location window, typed "~/.cache/."
This showed the contents of cache. I deleted the sessions folder, restarted and all is good. Thanks for the help.

---

