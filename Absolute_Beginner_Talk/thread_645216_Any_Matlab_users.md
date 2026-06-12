---
title: "Any Matlab users?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by madu on 2007-12-19
Hello guys,

I finally installed Matlab on my Gusty according to the Wiki for Ubuntu and it worked fine. Matlab starts up fine and I can do basic stuff like additions and plotting. 
But I have a strange problem in using toolboxes.
I copied the comm (Communications) and signal (signal processing) toolboxes from my  Windows Matlab installtion and copied to the /toolbox  folder in Linux. And then I setup the paths.

Before installing (copying) the toolboxes, I could not autocomplete functions like rayleighchan or awgn. But after the toolboxes are coiped, Matlab successfully autocompletes those functions and even can view the help from the command. But when I try to use that function, it says "Undefined function/command" which is very strange. And when I try to change the working directory to the folder where the .m file of these functions are, Matlab says  "Name is nonexistent or not a directory".

Can somebody please give me some help with this. I was so looking forward to Matlab'ing in Linux.

Thanks a lot.

---

### Post by bone2006 on 2007-12-24
I'm not sure if you are the same person who wrote another question about matlab, but give octave a shot.  It's free open source and does almost everything matlab does at least for what my needs are

---

### Post by dfire07 on 2007-12-28
Matlab's windows toolboxes may not be compatible with the linux version. Also you can't just copy toolboxes and adjust the path. Many hidden binaries also need to be transferred. You can try some matlab forums like [kluid]("http://www.kluid.com") for more.

Thanks,
D. Wolfgang
Design Engineer
[www.celliz.com]("http://www.celliz.com")

---

### Post by madu on 2007-12-28
Thank you very much bone2006 and dfire07.

Octave simply didnt have the function I needed and also since I have been working with Matlab for a while I wanted to stick to it to be able to use the codes I have already written.

But since Octave had a major upgrade, maybe I'd give it a try. But it still doesnt seems to be in the repositories...

Thank you dfire07 for that info. Maybe that is the problem. But that worked in Windows. Anyway I'd try a forum or just call the Mathworks help desk.

Thanks a lot again fellows.

---

