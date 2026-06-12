---
title: "[SOLVED] Installing Xubuntu"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by wasing on 2007-06-07
i downloaded the Xubuntu.ISO file for the Desktop i386 because i wanted to put it on my first self built computer and i was wondering how to install it. i tested it in my good computer but all i get is the file i wrote to the CD.. this may seem very obvious to many of you to what i am doing wrong but for my first time even using a Linux OS or a .ISO extension i have no Idea how to properly install a .ISO file or what i have to do to set it up so that i can install it...

please help me

---

### Post by logos34 on 2007-06-07
**[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)**

Welcome to Ubuntu!

---

### Post by Skidpad on 2007-06-07
Sounds like you wrote the .iso file to disc (cd) as a data file, and not as an iso *image* as it needs to be.  It won't work as a data file.

What program did you use to burn it with?  Look through your Options and see if there is something like "Write/Burn as image".

---

### Post by wasing on 2007-06-07
Thank you Guys Very Much for the Help

Also Thank you for Welcoming me into Ubuntu

---

### Post by Skidpad on 2007-06-07
No problem.  Enjoy yourself, and let us know how you get on with it.

---

### Post by bodycoach2 on 2007-06-07
Let us know if you had a successful installation.

---

### Post by wasing on 2007-06-08
Well i have been researching more and more about Ubuntu and Xubuntu and the message that im getting is that before i can install xubuntu i need ubuntu is this true or am i just misunderstanding.... i was reading somewhere that before i install xubuntu i need to install a "Minimal System".... i can't test ubuntu at all for atleast 12 days because i have to get my RAM in the mail...  :( 

anyway... 

can you guys tell me any prerequisite information i need before i even start up my computer that i will need to install before xubuntu or atleast point me in the right direction of where to find it...

thx you guys so much in advance 

12-14 [SIZE="7"]Business[/SIZE]days in counting till RAM arrives.

---

### Post by dptxp on 2007-06-08
Download Infrarecorder. It runs on Windows.

Use "Burn Image" command in "actions" Menu.

Select the iso file.

Once CD id ready, boot with the CD. (set bios to boot with CD).

Check CD integrety first when the page shows up.

Click on Live/Install to run it live. 

If you like it, Click on the Insttall icon on desktop when running live.

Plan your partitions first. Shall be needed in step 4 (or 5).Use manual mode, resize to 8-12 GB for / in ext3 fornat, rest for /home (ext3 format)excluding the last 2 GB for SWAP.

You can have more partitions in between, format all in ext3. Keep last 2 GB for SWAP.

You do not need anything else.

---

### Post by dstew on 2007-06-08
You do not need to install Ubuntu before installing Xubuntu. The reality is that all the Ubuntu distributions have the same "back end", meaning the kernel and directory setup, but they have different "front ends", in particular the graphical user interface (GUI). Xubuntu uses a light-weight GUI called Xfce that uses less system resources than Gnome, which is the regular Ubuntu GUI. But you will notice, if you look on the forums, that the same command line codes work for Xubuntu and Ubuntu, at least for the text-based programs that undergird the Ubuntu systems. For example, if you want to look at files with a graphical interface in Xubuntu, you use the Thunar file manager. In Ubuntu, it is a different program, I think Nautilus. But both Xubuntu and Ubuntu will give you the same output on the command line to the command **ls**, which gives a text output of directories.

---

