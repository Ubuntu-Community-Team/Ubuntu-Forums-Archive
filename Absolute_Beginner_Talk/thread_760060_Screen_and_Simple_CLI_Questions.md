---
title: "Screen and Simple CLI Questions"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by BurkDP on 2008-04-19
Hi, I've just made a simple file server, and I don't really need a gui. A friend showed me the magic that is screen but I've got a question: Is it possible to have screen display a bar of all the current windows it has open?

Something like this across the top of the window:
________________________________
  \ 1. Terminal \ 2. HandBrakeCLI \ 3. etc.         | 
-*-----------------*------------------------*---------|


I know screen can have names for each window you open, and I think in the man page also says something of a status line(?). I was wondering if someone could help me set up a situation like above, maybe by editing the config file or creating a script or something. Where I could name windows and just uncomment them to have them show up in the status line. I don't expect to click on the tabs or anything, I just want a way to see what I have running at the moment.

Something Like this maybe? 
## Status line
 1. Terminal
 2. HandBrakeCLI
 3. etc.
# 4.
# 5.
# 6.
# 7.

I'm a complete noob when it comes to linux, so if it's not possible or more of a pain in the butt than it's worth is there another option, like ratpoison or such? I'm capable of following explicit directions so if you can help me, you cannot be too verbose. Thank you for your time and for reading my post, and if this is addressed in another post forgive my double posting.

P.S. - I did the basic CLI install, so it asks me to login as my user every time I have to restart (ex Server Login:  password: ) and I know with a GUI you can just select the option for an automatic login for a user but is there a way to achieve this on the command line?

P.P.S. - How do you set a program to run at startup, like say screen? I've heard (in passing reference) of the power of scripting. Is there a way to set it so screen not only starts running at start-up but reattaches?

---

