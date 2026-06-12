---
title: "Freeze ups every time."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Warpspasm on 2007-02-19
I decided to give Linux a try and thought Ubuntu sounded like the best place to start. I downloaded the CD for 6.10 and installed it on my second drive. There was already NTFS on that drive and I chose the selection to make a new Linux partition. In the process of creating the partition the system froze. I rebooted, it froze again. I rebooted and the partition was created and Ubuntu was installed. Then, I did the update thing that there were 135 files needing updating. I told Ubuntu to download and install the updates. At file 71 the system froze. I rebooted. At file 89 the system froze. I rebooted. At some point all of the files were downloaded and it began the unpacking and updating. Guess what. . . .the system froze. I rebooted and now, when I try to continue with the updating process I'm told I have manually run "dpkg --configure -a". I really didn't know how to do this, but I kept noodling around and when I entered this command I was told I needed superuser (or something like that) status to do it! What the heck is superuser status and how do I get it?

I was excited about trying Linux after having used PC and Apple OS's over the last 20 years. I thought I'd waited until the OS was mature, but honestly I'm not so sure at this point. I hope it's just something I did wrong, but the constant freeze ups are kind of weird.

I'm running a home made PC with a 2.8 Pentium 4 on an ASUS PCP800 Deluxe mobo. 2gb RAM, Hercules Fortisimo III sound card and ATI 9500pro video card.

I still really want to give this a try if somebody can help me get through these problems.

Thanks.

---

### Post by StanRedfish on 2007-02-19
Hi;
I am in your situation almost identically except I was using 6.06 and 6.10 cured my lockups.  I believe they were caused by the video card.  That seems to the where Ubuntu is the most fragile.  as for your command hightlight and copy it, go to applciations, accessories, Terminal and enter su at the $prompt.  It will ask you for the root password.  If you don't know it go back into your gui and goto system,  administration, users and groups.  It will ask for your password which is the one you are currently using, enter it and the user settings dialog box will come up.  Click on the root user and click properties.  Then enter the password under the boxes next to the radio button for set password by hand.  Click ok and go back to your terminal window and press <ctrl><shft>v to paste your command into the command line and press <enter>.  This is one of the first problems I came across.  Most of the answers from Linux users assume you know something and coming from windows I know nothing.  So you are not alone.

Hope this helps,
Stan

---

### Post by jvc26 on 2007-02-19
I'm afraid I'm not sure about your freeze up problems, to run the dpkg --configure -a command you need to use 'sudo' like so:
```

sudo dpkg --configure -a

```
It will then ask you for a password, put in your user password and the command will run. For more info on the sudo command have a look [here]("https://help.ubuntu.com/community/RootSudo")
Il

---

### Post by jvc26 on 2007-02-19
> **StanRedfish said:**
> Terminal and enter su at the $prompt.  It will ask you for the root password.
The root account is disabled by default to keep your OS safe, using the root user is extremely inadvisable, and so you use the 'sudo' command to do commands as the superuser - 'sudo x' where x is the command, you then enter your user password and that allows you to execute the command.
Il

---

### Post by Warpspasm on 2007-02-19
The command worked great and the update finished. 

The system still keeps freezing though. I tried installing a game and when I tried to run it, it froze the system after about 10 seconds.

I really didn't expect these kinds of problems with Linux. Is it just Ubuntu, Linux or me?

---

### Post by budgie9 on 2007-02-19
You may be looking for the wrong cause to your problem.
If I was you I would take a look at memory first. Use the Memtest86 program on your CD, run the test for some time to see if there is any errors, 
At least you will rule out one major cause of freezes  then look for other perhaps graphics problems.

---

### Post by Warpspasm on 2007-02-19
If it were a memory issue, wouldn't I have the problem when I run XP as well?  XP runs without a hitch.

---

