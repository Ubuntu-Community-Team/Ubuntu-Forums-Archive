---
title: "How do I change the screen resolution"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by AlanCam on 2006-08-23
I am a complete Linux beginner but a very experienced MS Windows user.
I have installed Ubuntu and have achieved a dual boot system OK but the screen resolution is 1280x1024 which makes the screen impossible to read. Old age.
How do I go about changing the setup.
Using
System>Preferences>Screen Resolution
gives only one choice for resolution.
In response please bear in mind I know nothing about running Linux and it is difficult when you cannot easily read the screen.

---

### Post by Turgon on 2006-08-23
What you need to do is a little complicated. You need to open a terminal and then type:

sudo dpkg-reconfigure xserver-xorg

Then you will be asked a lot of questions, but you can at most of them just press enter (answer yes on autodetection of videocards, keyboard and display). 

In one page it will ask you which resolutions you want to use. Just press spase over the once you need to add and then press enter. 

After you are done with all the questions, restart or just press Crtl+Alt+Backspace (restarts the graphical enviroment, deletes all data thats not stored).

Then you should be able to change the ressolution to whatever you need.

Good Luck!

---

### Post by AlanCam on 2006-08-23
Thanks a lot for the reply.

I did precisely as you suggested. IT SCRAMBLED EVERYTHING!

I willl get back to you when I have re-installed the whole sorry mess again.

Alan

---

### Post by iampoch on 2006-08-23
It's the xserver bug methinks. Been having the same problem.

---

### Post by AlanCam on 2006-08-25
Thanks for confirmation of that.

This release of Ubuntu is obviously not ready for general release. Can you imagine an office user doing the screen resolution thing described above.
Some of the questions it asks I was hard pressed to understand the question let alone choose the correct answer.

No, I think I may abandon Ubuntu Dapper Drake.
Is the previous version still available?

---

### Post by Druidor on 2006-08-25
I think the screen resolution problem is a reocurring one with many users.

I to have been trying to get a resolution of 1280 on my machine without sucsess.

Have done sudo dpkg-reconfigure xserver-xorg & specifically selected the resolution & have looked at my settings file which clearly shows the resolution there Yet in the control panel the highest resolution is 1152 which as I am used to 1280 looks freaky.

Still working on this one though.

---

