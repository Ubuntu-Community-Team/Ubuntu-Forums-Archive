---
title: "checkgmail problems"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-07-01
Hello, I was wondering how to make the checkgmail icon stay in the tray icon area.  Everytime I run the program from terminal ```
checkgmail
``` it works fine,  but when I close the terminal it goes away.  Any help would be greatly appreciated.

---

### Post by p_quarles on 2007-07-01
Create a new launcher and have it run the code "checkgmail."

To create a launcher, just right-click on the area you want to place it in, and select the appropriate option.

---

### Post by orb9220 on 2007-07-01
Or you could just add it as a startup program in sessions manager like I do.

You can also give it audio feedback for new mail I have the notify.wav in my home folder and have gmail do **aplay notify.wav**

---

### Post by fontenot_1031 on 2007-07-01
I did both, thank you very much

---

### Post by espmartin on 2007-08-01
> **orb9220 said:**
> Or you could just add it as a startup program in sessions manager like I do.

You can also give it audio feedback for new mail I have the notify.wav in my home folder and have gmail do **aplay notify.wav**

Can you give example of how you did this for me, a complete Ubuntu newbie?

God bless,

Martin

---

### Post by linuxwizard on 2007-08-02
espmartin
Is this what you wanted

Enter a command in the "Command to execute on new mail" section in the preferences. For example, to play a WAV sound, you could use

aplay /path/to/mysound.wav

---

### Post by espmartin on 2007-08-02
Cool, thanks!!!

---

### Post by mcduck on 2007-08-02
to run a program from the termial so that the program stays open even if you close the terminal you can use 'nohup'. Also add a '&' to the end of the command to keep the terminal usable for other tasks.

For example, 'nohup checkgmail &'

Of course you can just run the command from the Run dialog (Alt-F2) instead of using the terminal. Or in this case add it to your session.

---

### Post by espmartin on 2007-08-02
cool, thanks again!

---

