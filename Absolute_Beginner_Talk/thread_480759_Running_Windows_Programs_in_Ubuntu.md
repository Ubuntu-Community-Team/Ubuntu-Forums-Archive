---
title: "Running Windows Programs in Ubuntu?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Christ_Guard on 2007-06-21
I have heard rummors that there is a program that may allow for windows programs to be booted from ubuntu, is this true, if so, where can I get more info?

---

### Post by Majorix on 2007-06-21
You can use wine. It is in the repos.

Once set up, you can use it by typing
wine applicationname.exe

---

### Post by Christ_Guard on 2007-06-21
Repos?

---

### Post by Majorix on 2007-06-21
Ok if you have Ubuntu installed go to System>Administration>Synaptic Package Manager. Type in your root pass when prompted. Then once in there, type in "wine" to the search. You will get a list. Select "wine" from that list, not "wine-develop" and stuff like that.

And you have to type in "wine application.exe" in the terminal. You can access the terminal by going to Applications>Accessories>Terminal.

Hope that helps you.

---

### Post by jputman01 on 2007-06-21
> **Christ_Guard said:**
> Repos?

repos=software repository

you may need to do some research on how software and linux work first, like the different methods to get and install software and so on

but the program you are referring to is called Wine as stated above

a good starting place to learn some ubuntu basics is here in the forums and [psychocats]("http://www.psychocats.net/ubuntu/index.php")

welcome!

---

### Post by Adam_GUI on 2007-06-21
> **Christ_Guard said:**
> Repos?
Yup.
They're in synaptic, the program that does your addition/subtraction and updating of programs.

"Kdesu synaptic" or "Gksu synaptic"
Input your password and search for "wine."

Mind, wine won't run everything.
For games there's cedega.
For office/misc there's Crossover Office.

---

### Post by FleetAdmiral74 on 2007-06-21
LOL, rumors...where the heck did you read rumors of this?

---

### Post by Sable683 on 2007-06-21
Just my $0.02.... I've tried both wine and cross over office and both didn't want to run the programs that I use that are native to Windows. My solution was to use Virtual Box, I allocated a 5 GB hard drive and now I just have an icon for booting Windows. I used the system recovery CDs for my laptop to install winxp and have not had any major issues with it. 
For a noob like me, it was easier than doing all the work arounds for wine and COO.

~John

---

### Post by vexorian on 2007-06-21
Almost all software can run in WINE, the issue is that some require some special DLLs, and some rely (for no practical purposes) on CD copy protections thus it is hard to make the program figure out it could work, but then there are the few WINE apps and most of the games which won't work correctly after you get to launch them.

IMHO if your intend with an OS is to run windows apps your best pick is windows XP.

vmware can pretty much run windows very fast as long as you got enough memory and disk space, but the issue is that 3d acceleration either is not available or I didn't know how to enable it, so I couldn't run  most of the actually essential apps on it.

Thus I just keep dual boot, most of the times lately I stick to Ubuntu, but reboot to windows whenever I have to do something I can't on Linux (and viceversa actually)

---

