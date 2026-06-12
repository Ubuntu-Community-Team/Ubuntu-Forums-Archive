---
title: "error messege install clamAV"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by jamadan on 2006-09-15
i've problem while install clamAV to my pc. at first step in terminal (./configure....) as a guildline to install. the error messege is " no acceptable C compiller in $PATH".
what is it means. how to proceed to next step?
tq.

---

### Post by oedipuss on 2006-09-15
Are you building it from source?
Why not use the one from the repositories (through synaptic) which will reduce the installation procedure to a few clicks? 
Go to System/Administration/Software Properties, and enable 'universe' and 'multiverse', and then run Synaptic and check the package 'clamav'. It will also install all other software it might be needing to work.

On the other hand, if you still want to install it from source (./configure , make , and make install) then I suppose you'd be missing a C compiler or other tools.
Try going again in synaptic and installing the package 'build-essentials'.

PS : if you favor the console, you can run :
 sudo apt-get install clamav

or 

sudo apt-get install build-essentials

Its the same as synaptic, minus the nice searchable gui.


PS2: If you're new to linux, I'd strongly reccomend using synaptic and getting things from the repositories over building them yourself. =D

---

### Post by Najand on 2006-09-15
If you are using Ubuntu as a Desktop, you don't need any virus scanner. Virus Scanners are for servers with some Windows Computer inside.

---

