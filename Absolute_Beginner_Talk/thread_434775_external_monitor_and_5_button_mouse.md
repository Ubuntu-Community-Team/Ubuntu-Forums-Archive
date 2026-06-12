---
title: "external monitor and 5 button mouse?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by karbon14 on 2007-05-06
working on a dell d620, installed 7.04 last night and it seems alrighty so far.

as per [this]("http://ubuntuforums.org/showthread.php?p=2602270#post2602270") post i upgraded to the newest intel driver to get the resolution working properly at 1280x800. (granted i was reading what it was doing and i was a bit lost, can you tell i'm new?)

only 2 things that i want to work at the moment are my external monitor (philips 17" tft should run at 1280x1024) wanting to know if i can run it as an extended desktop and how exactly i do that? (baby steps please)

and i have a logitech desktop set,  an mx3200, but only really use the mouse.  only thing is the back and forward buttons on it don't work.  how would i go about fixing this?

oh in fact, out of interest, why does backspace not take me back a page in firefox the same as it would have in windows?

---

### Post by Happy_Man on 2007-05-06
At least the Firefox one I can answer. [http://ubuntuforums.org/showthread.php?t=387698&highlight=backspace+firefox](http://ubuntuforums.org/showthread.php?t=387698&highlight=backspace+firefox)

---

### Post by karbon14 on 2007-05-06
hurrah, that feels better already.

granted i could have searched for that myself but only thought about it while writting the post.

thanks happy_man :)

---

### Post by starcraft.man on 2007-05-06
Ok, [here]("http://ubuntuforums.org/showpost.php?p=2318286&postcount=1") you go for the backspace fix in Ubuntu.

I don't know how to get the back and forward buttons on your mouse to work, not sure if you can. Probably requires a custom xorg.conf file to get it to work, or else its just not possible...

And in relation to your extended screen, what graphics card are you using? I only have experience with Nvidia, you will want to install the drivers for your card regardless with [this,]("http://www.albertomilone.com/nvidia_scripts1.html") its an installer script, follow the instructions on his home page and install automatically the right drivers. Then, I know in Nvidia,  go to the nvidia settings (Applications > System Tools >Nvidia settings) and there will be a section with twinview labelled, you'll have to use that to set it up... I have to find the link to the howto here.,.. but I'm fairly sure you can use the GUI to set it up easily and it will autoconfig your xorg.

---

### Post by karbon14 on 2007-05-06
its just the intel graphics chip on the board, so i don't think that link would work.  only seems to be for ATI or nVidia i think?

---

