---
title: "Applications won't start"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Sigma1 on 2006-08-28
Hello,
I'm runnning Ubuntu 6.06 and am pleased with it, but on occasion applications simply refuse to run. I get the startup logo, when there is one, then return to the previous screen. The phenomenon is difficult to replicate and does not affect one particular application (I've noticed it with Firefox, Open Office, Gnome Terminal and even System > Quit.) It may be an overheating problem, I imagine, but I really don't know how I should begin configure Fan management.
For information, I'm running a dual boot with two hard drives on a Compaq Presario.
Any help would be much appreciated.

---

### Post by crane on 2006-08-28
One thing you could do is run a test on your memory. Just select memory test on boot menu (grub) and let it run. Basicly leave the computer to run the test for awhile. Bad memory can cause apps to 'just' quit sometimes.
 As far as heat, I have no knowledge of controlling fans. I put 2 really big fanes in mine and have not had a heta problem to worry with.

 If the proble happens frequent enough you can start the programs from terminal to see the error.
 You could also change the start command to make a log file to view. Example:
Create a launcher on you desktop for firefox
In the command line use something like,
firefox > firefoxlog.txt
Then everytime you start it from that launcher it will right a text file in your home directory. Then when it does crash, you can look at the text file and see why.

 I was having the same issues with Q3 and other apps for a while. Found signal 11 error cause the app. to quit. Turned out to be bad memory.
Maybe someone else have a better way of trouble shooting, that is just the way I did it.

 Good Luck!

---

### Post by Sigma1 on 2006-08-28
Many thanks for your answer, Crane. I've run the memtest... it didn't appear to throw up any errors, but there again I'm not sure I'd have been able to recognise it if it had.
Could I ask you to be more precise for me regards the launcher? I create a desktop launcher for Firefox, but where should I place the firefoxlog.txt link, please?
Thanks again. S.

---

### Post by crane on 2006-08-30
> **Sigma1 said:**
> Many thanks for your answer, Crane. I've run the memtest... it didn't appear to throw up any errors, but there again I'm not sure I'd have been able to recognise it if it had.
Could I ask you to be more precise for me regards the launcher? I create a desktop launcher for Firefox, but where should I place the firefoxlog.txt link, please?
Thanks again. S.

I'm not on my Linux Box right now (work = windows:( )
I believe it is the second tab over in the proporties box tha has a place for tha command. Generally it is something like 
*firefox*
Just change it to 
*firefox >firefoxlog.text*
 I will look at this tonight when I get home as well and confirm it.

---

### Post by Sigma1 on 2006-08-31
Thanks, Crane. I look forward to your answer. I'm working on Dapper which may explain why I can't seem to find the same features in the Properties box. All that happens when I insert firefox >firefoxlog.txt, is that firefox opens and tries to find a page "firefoxlog.txt". The problem has occurred only once since running the memtest, which is encouraging.
S.

---

### Post by crane on 2006-09-02
> **Sigma1 said:**
> Thanks, Crane. I look forward to your answer. I'm working on Dapper which may explain why I can't seem to find the same features in the Properties box. All that happens when I insert firefox >firefoxlog.txt, is that firefox opens and tries to find a page "firefoxlog.txt". The problem has occurred only once since running the memtest, which is encouraging.
S.

Yea I have messed with this as well and get the same outcome. I guess the best way would be just to run some of your programs from terminal and that way when they crash you will be able to look at the terminal and see what happened. It is a bit of a pain but it will help out when it crashes.
 Also , when you run memtest, how long did you run it?I ran one the other day and an error did not show until pass 92.
Good Luck, if I come across anything else that could help I will post it here.

---

### Post by Sigma1 on 2006-09-03
Thanks again, Crane, for your answer. I ran memtest for 1h30 or so, maybe that wasn't enough. I'm beginning to think the problem is connected with the ubuntu-desktop package, or possibly with gnome, since I seem to be able to start other apps fine. I wonder also if it's not connected with resume after suspend. I don't think the problem's ever happened before suspend-and-resume.
I'll trying running apps from the terminal next time and may be back with a new post if I get any interesting messages!
Best. S.

---

### Post by dirk_k on 2006-09-05
This is some bug in x-session-manager or something. See: [http://launchpad.net/distros/ubuntu/+bug/52200](http://launchpad.net/distros/ubuntu/+bug/52200)

I also have this problem with both my desktop and my laptop.

---

### Post by Sigma1 on 2006-09-06
Thanks dirk_k, nice to know I'm not alone. I noticed that according to one of the threads you gave, typing DISPLAY=:0 in a terminal worked for somebody (but not everybody). Will try that.
Curiously I've started suspending using the suspend button on my keyboard (it hadn't occurred to me that it would also work under Linux) rather than System>Suspend, and have not had the problem again since. Might just be coincidence, though!

---

