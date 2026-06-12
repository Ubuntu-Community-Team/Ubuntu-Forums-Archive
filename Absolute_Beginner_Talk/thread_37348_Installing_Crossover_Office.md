---
title: "Installing Crossover Office"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by spednik on 2005-05-26
First things first, I'm a am a complete green noob. 

I managed to get a copy of crossover office pro, but am completely clueless on how to install that, let alone the windows apps. 

In the packadge, i have 2 files 
install-crossover-pro-4.1.sh
install-crossover-pro-4.1.sh.md5sum 

What now? 

I Take it i have to enter something into the terminal, so if someone could tell me exactly what,word by word,  that would be a great help.  

I doubt this will be of any help to anyone, but the file path to the packadge is 
tar:/home/spednik/Shared/CodeWeavers.CrossOver.Office.Professional.v4.1.Linux.tar/


Thanks in advance for any help

---

### Post by andlinux21 on 2005-05-26
[FONT=Comic Sans MS]I wish i could help you with this but I too wanted to get and install Crossover I will google and see what I can come up with.[/FONT]

---

### Post by codejunkie on 2005-05-26
open a terminal go to the directory where the file is located example: cd /home/yourusername/crossoveroffice and the type 
sh install-crossover-pro-4.1.sh this will open a graphical installer that will walk you through the rest of the process hope this helps.

---

### Post by spednik on 2005-05-27
Hmmmm, not working. 

The part with the cd works fine, but when i type the part with the sh it says 
sh: install-crossover-pro-4.1.sh: No such file or directory

I tried everyhing, but still no good. And the file does exist! i even dragged it right into the terminal , but still  the same thing. 
Any Ideas?

---

### Post by spednik on 2005-05-27
No scratch that, even the cd part dosnt work, it just says it isnt a directory.

---

### Post by clb137 on 2005-05-28
[QUOTE=spednik]No scratch that, even the cd part dosnt work, it just says it isnt a directory.[/QUOTE]

Can you mount your cd???? and read it in linux

---

### Post by poofyhairguy on 2005-05-28
[QUOTE=spednik]
I tried everyhing, but still no good. And the file does exist! i even dragged it right into the terminal , but still  the same thing. 
Any Ideas?[/QUOTE]


is that the folder that .sh file is in?

---

### Post by jrobcet on 2005-05-28
Hmmm, looking at this makes me wonder:[QUOTE=spednik]I doubt this will be of any help to anyone, but the file path to the packadge is 
tar:/home/spednik/Shared/**CodeWeavers.CrossOver.Office.Professional.v4.1.Linux.tar**/
[/QUOTE] Have you actually extracted the archive? If so, is "CrossOver.Office.Professional.v4.1.Linux.tar" the directory that contains the installation file?

---

### Post by spednik on 2005-05-28
Nope, i Havent tried extracting it , i wouldnt even know how to (this is my first time installing something without apt-get or synaptic) and with the dragging, i tried the install crossover pro file. still no luck.

---

### Post by spednik on 2005-05-28
install-crossover-pro-4.1.sh that file i mean. 

So pretty much what i have right now is a packadge sitting in my shared folder, in my home , with nothing extracted or anything. 

Like when  i click on the packadge (file:///home/spednik/Shared/CodeWeavers.CrossOver.Office.Professional.v4.1.Linux.tar)
In my Konqueror, it gives me this
tar:/home/spednik/Shared/CodeWeavers.CrossOver.Office.Professional.v4.1.Linux.tar/


Thats probobly of no help to anybody, but im cluess on this stuff.

---

### Post by tread on 2005-05-28
I'm using this as the file you downloaded:
> file:///home/spednik/Shared/CodeWeavers.CrossOver.Office.Professional.v4.1.Lin ux.tar 

1. Start a terminal
In the terminal type:
2. cd /home/spednik/Shared
3. tar xvf CodeWeavers.CrossOver.Office.Professional.v4.1.Linux.tar
4. sh install-crossover-pro-4.1.sh

Now follow the instructions from the installer.

---

### Post by spednik on 2005-05-28
I extracted it to /home/spednik//CodeWeavers.CrossOver.Office.Professional.v4.1.Linux/

But i doubt that will help me

---

### Post by spednik on 2005-05-28
Darn i didnt see that response, i extracted it, so now the file path will be different. Ill just get the file move the file back and follow those instructions, 


Thanks for your help all!

---

### Post by spednik on 2005-05-28
Yep, its all installed fine now. 


Thanks Again for everyone's  help.  :)

---

### Post by tread on 2005-05-28
You're welcome :)

---

### Post by elgx on 2005-09-20
mmmmh...
i installed the demo version, not managing in findind NOW another one. but i'll do soon.

ok, the fact is: i can't run "install(...).sh" as root, coz simply Ubu doesn't allow root user to access the KdisplayManager (or the G one). and so i installed in my hom dir.

so, went on to installing MS Office 2000... the cd reader can't read the "hidden" windows files, so the installation stops. if i hit the "fix" button, Crossover changes my fstab, but even if rebooted the cd still can't read hidden files. i'm currently copying files into the harddrive of a pc with windows, in order to unhide them and then rewrite a cd...

but isn't there a way to fix directly from Ubuntu?
thanks to all! and very sorry for my baaaaad english... :roll:

---

### Post by Perfect Storm on 2005-09-20
Codeweavers got .deb file, why not getting them instead?

When downloaded:

sudo dpkg -i /where/you/downloaded/it/to/crossofficeXXXX.deb
killall gnome-panel

Applications --->Crossover ---> Office Setup

---

### Post by elgx on 2005-09-21
well, managed to install it anyway (where have you found the .deb?!)...
thanks!
do you know of any tool (installable by Crossover or compatible via kubuntu) to type greek unicode characters and italians (/englishs) at the same time? i mean, just by clicking somewhere it should change keyboard layout/configuration...

---

### Post by TechSonic on 2005-09-21
I had a similar problem.

I purchased Crossover office and they sent me the one for Redhat and I told them it was the wrong one and they said I was a liar and wouldn't refund my money.  I wouldn't do business with those jerks.  Can't even send the proper version.  I asked for a Debian type and they sent me Redhat type.  Idiots.

---

### Post by ounas on 2005-09-24
[QUOTE=Artificial Intelligence]Codeweavers got .deb file, why not getting them instead?

When downloaded:

sudo dpkg -i /where/you/downloaded/it/to/crossofficeXXXX.deb
killall gnome-panel

Applications --->Crossover ---> Office Setup[/QUOTE]

Thanks it now works for me. :-)  :-) 

-
Ounas :razz:

---

### Post by Perfect Storm on 2005-09-24
[QUOTE=TechSonic]I had a similar problem.

I purchased Crossover office and they sent me the one for Redhat and I told them it was the wrong one and they said I was a liar and wouldn't refund my money.  I wouldn't do business with those jerks.  Can't even send the proper version.  I asked for a Debian type and they sent me Redhat type.  Idiots.[/QUOTE]

When you bought Xover office, then you made a username and password, just login at their homepage and grab the prefered package.

---

### Post by Donnut on 2005-11-18
k, I got the package, and when I tried running the command: sh install-crossover-pro-4.1.sh it said "file not found".  How do I install the rpm package?  I thought using apt-get would work, but it couldn't find it...

---

### Post by Perfect Storm on 2005-11-29
When installing indenpendent packages which aren't from the repo, you don't use apt-get but dpkg

```

sudo dpkg -i /where/the/package/is/XXXXXX.deb

```

---

### Post by johnniecarcinogen on 2006-05-31
[QUOTE=Donnut]k, I got the package, and when I tried running the command: sh install-crossover-pro-4.1.sh it said "file not found".  How do I install the rpm package?  I thought using apt-get would work, but it couldn't find it...[/QUOTE]

  ```
sudo -i
sh ./install-crossover-pro-4.1.sh
``` or whatever your file version is.

---

### Post by zvacet on 2006-06-01
Go to your share folder (cd /share).Then sh install -crossover-pro-4.1.sh

---

### Post by from_beyond on 2006-07-15
I just bought codeweavers Crossover Office and paid a good deal of money to just have notepad working. I hope I can get a refund, this is a really bad investment and I'm just posting as a warning to others contemplating on buying it. Be smart and try out before you buy any third party software for linux.

---

### Post by firezip on 2006-07-20
I downloaded CO 3 but it doesn't make the Gnome shortcuts. Anyway I can fix this?

---

### Post by GavinZac on 2007-11-11
This thread is the first result from Google, so just to clarify, the easiest way to install the CO trial is at this link: [http://media.codeweavers.com/pub/crossover/cxlinux/demo/crossover-standard-demo_6.2.0-1_i386.deb](http://media.codeweavers.com/pub/crossover/cxlinux/demo/crossover-standard-demo_6.2.0-1_i386.deb)

---

### Post by nzstef on 2007-11-18
Or to install via Automatix2: [http://www.getautomatix.com/]("http://www.getautomatix.com/");)

---

