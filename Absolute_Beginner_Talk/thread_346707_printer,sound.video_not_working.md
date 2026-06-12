---
title: "printer,sound.video not working"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by yellowtuxido on 2007-01-26
hi
Just installed edgy installed HP950c from list its visibale in the printer boxsays ready to print when sent a print it says print in Q but nothing happens. please help also I have no sound at all help

---

### Post by citizenofnowhere on 2007-01-26
Your problems are most likely unrelated, try to provide more info on your problem when you post. Especially what have you already tried to fix it?

_Printer_

Have you tried restarting the program you are printing from and/or the computer? Sometimes it takes a while. 

Assuming you are using Ubuntu (and not Xubuntu or Kubuntu) Go to your System-> Administration->Services

Look for anything related to printing and make sure it's checked. This will ensure it starts up together with your PC.

Double check all the connections between your PC and your printer. If you have another PC - plug it in instead, and see if the Printer works at all. Or if you have a Windows installation parallel to your Ubuntu, try to print from there.

Alternatively, take your installation cd and boot up (live-cd). Try installing your printer and printing a test document. (Remember none of your changes will be saved, this is to make sure your printer is still working fine)

_Sound_

What version of Ubuntu are you using?
What is your soundcard?
What are you using to play back videos/audio? Are you trying to play mp3s/dvds? Does it work with VLC player? 

You need a special package to be able to play mp3s/dvds using anything other than VLC. Google for and download "automatix" - running this program will install all the codecs necessary for you. 

Are you using ALSA/OSS? Have you tried switching between them?

---

