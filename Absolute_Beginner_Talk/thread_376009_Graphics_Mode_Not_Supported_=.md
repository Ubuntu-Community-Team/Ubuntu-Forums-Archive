---
title: "Graphics Mode Not Supported =/"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by tiC_t0k on 2007-03-04
Hi All,
i am trying to run ubuntu on my computer so i downloaded the .iso from ubuntu.com(i got the 6.10 version) and wrote it onto a cd as it describes with the software "InfraRecorder" and its all done with that. i changed my bios so it will boot from a cd before a harddrive. so i put in my cd and restart my computer and it takes me to the ubuntu main menu. i checked for disk error and there was none. so i restarted and did "Start or Install Ubuntu" and it loads for a while and after its all done loading it goes and makes the sound like its going to start but then my screen flashes and goes completly black and my monitor gives me the message "Graphics mode not supported" and it floats around my monitor. its in the same box like if your monitor isnt plugged in.

so, any ideas?

tiC_t0k

p.s. i dont know if this will help but these are my computer specs.

Proccesor= AMD Athlon 64 X2 Dual Core Processor 3800+
GFX card= NVIDIA GeForce 6800 GS 256mb

---

### Post by annda on 2007-03-04
when you boot from the cd, can you choose safe graphics mode? what happens then?

---

### Post by tiC_t0k on 2007-03-04
it does the same thing when i do the graphics safe mode

---

### Post by igknighted on 2007-03-04
First I would try "graphics safe mode".  If that doesn't work, hitting F6 will let you add extra boot options manually.  Try adding vga=791 or resolution=1024x768 to the end of that line.  If it really doesn't want to work, I would download the alternate install CD and use that to install.  Once installed it should boot OK, and even if it doesn't want to, you can install the nvidia driver easily without logging into the graphical mode, and it will work then.

---

### Post by tiC_t0k on 2007-03-04
so i kinda realized that i didnt do what u said...but i hit F4(i think) the VGA one and changed the resolution to1024x768x32 and i was able to get it to boot! so i got to the main screen desktop thing of ubuntu and i dont have a mouse =/ its there but i cant see it. im assuming that this isnt normal....

is there anybody who has msn, aim, xfire that can help me?

---

### Post by tiC_t0k on 2007-03-04
let me rephrase, i have a mouse just not a pointer. so if i move over an icon i can see it light up or change letting me know my mouse is on it, i just cant see the pointer, its invisible

---

