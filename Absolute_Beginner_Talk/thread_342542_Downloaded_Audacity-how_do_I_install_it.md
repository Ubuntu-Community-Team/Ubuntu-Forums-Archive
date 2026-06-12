---
title: "Downloaded Audacity-how do I install it?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-01-20
I downloaded Audacity for the Audacity site. Their forum is very quite so I thought I would ask here how to install it. I previously tried to set things up in Synaptic but I just am too new to Linux Ubuntu. I put a url in the repository but when I go to get it there is an error saying that "Error-the following problems were found on your system-E: Type 'http://http.us.debian.org/debian/' is not known on line 28 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."
I also opened the root terminal and tried to do an install but struck problems and got a similar error as above.
The file is on my desktop so if it is supposed to be elsewhere can you tell me how to move it as I know I can't unless I am the root user.

---

### Post by shareMenaPeace on 2007-01-20
Hi, 
well i guess you have the source files now and need to install them.
This is 1 way of doing it. To know howto search google or this forum for audacity install ubuntu or debian.

[http://www.google.de/search?hl=de&q=audacity+install+ubuntu&btnG=Suche&meta=](http://www.google.de/search?hl=de&q=audacity+install+ubuntu&btnG=Suche&meta=)

I used getautomatix.com an automatic installation application.
Which offers the most importent tools and codecs and auda.
 All you need todo is downlaod the installer and run it once it downlaoded.

And is the line you put in the surces.list similar to the other sources lines and is it adjusted to your ubuntu version?

---

### Post by ComplexNumber on 2007-01-20
**rapattack1**
you don't need to download it from the audacity site. just fire up the synaptic package manager and you'll find it in there. you need to enable the universe and multiverse reositories in synaptic by going to 'settings' then 'repositories' in the menu, then clicking on al the tickboxes.

---

### Post by steve.horsley on 2007-01-20
You should definitely be using synaptic for installing software whenever possible. Did you try to edit sources.list by hand? Did you make a backup of the original sources.list first? 

if you can restore the original osurces.list, please do so and then do the following:
Start Synaptic: System->Administration->Synaptic
Choose Settings->Repositories
Enable the Multiverse, Universe and Restricted sources.

Now you can choose and installl Audacity from the repositories.

If you can't restore the original sources.list, please post your current version here, and we'll be able to tell you how to fix it. At a quick guess, you need to put the keyword "deb" in front of the new URL, but I can't be sure without seeing it.

Downloading and compiling from source code is not something a newbie really wants to get stuck into unless really necessary, and for Audacity which is in the repos, you're just making a lot of grief for yourself fo no reason. And you **must** get synaptic fixed anyway.

---

### Post by shareMenaPeace on 2007-01-20
Thanks for the tip wasnt aware synaptic offers audacity.

---

### Post by rapattack1 on 2007-01-20
OK first things first how do I enable  the Multiverse, Universe and Restricted sources?
Btw I downloaded Audacity because time was going on and I have dialup. I thought I could point whatever program to install from the hard drive but I am sure I have to move the file to the opt folder first?

---

### Post by ComplexNumber on 2007-01-20
> **rapattack1 said:**
> OK first things first how do I enable  the Multiverse, Universe and Restricted sources?
Btw I downloaded Audacity because time was going on and I have dialup. I thought I could point whatever program to install from the hard drive but I am sure I have to move the file to the opt folder first?
find synaptic in the menu, then follow the instructions above by selcting 'settings' then 'repositories' from the menu. its very straightforward. oh, when you've clicked all the repositories and clicked on the close button, it wil ask you to 'reload'. go ahead and reload - this will add the extra packages from universe and multiverse into the list of packages.

---

### Post by rapattack1 on 2007-01-20
I know how to find Synaptic and the repositories but how do I enable universe, multiverse whatever? I have done the reload thing but nothing is listed there.

---

### Post by ComplexNumber on 2007-01-20
> **rapattack1 said:**
> I know how to find Synaptic and the repositories but how do I enable universe, multiverse whatever? I have done the reload thing but nothing is listed there.
what exactly do you mean by "nothing is installed there"? 
also, have you done a search for "audacity"?

here is a screen shot showing what you get after going into the menu and selecting settigns then repositories. all the tickboxes need to be selected, then press the reload button.

---

### Post by rapattack1 on 2007-01-20
There is an error that I have posted somewhere above!

---

### Post by ComplexNumber on 2007-01-20
> **rapattack1 said:**
> There is an error that I have posted somewhere above!
if its a malformed URL, the chances are that it will show up in the dialogue that i posted a screnshot for. go back then and click on the 'Third Party' tab. do you see the same URL in there that is giving the error? if so, delete it, then reload.

realistically, you shouldn't really be mixing debian repositories with ubuntu ones.

---

### Post by steve.horsley on 2007-01-20
> **steve.horsley said:**
> 
If you can't restore the original sources.list, please post your current version here, and we'll be able to tell you how to fix it. At a quick guess, you need to put the keyword "deb" in front of the new URL, but I can't be sure without seeing it.

Post the file and we'll post a fix.

---

### Post by rapattack1 on 2007-01-20
I have deleted that debian line.....can't think of the exact thing but anyway it is done. Reload has shown that audacity is listed but I still am getting nowhere.

---

### Post by rapattack1 on 2007-01-20
Sorry I deleted it. A friend who is a Linux enthusiast was over at my place earlier and said ok later when you go online this is what you do but it didn't work. I didn't go online and try it at the time as I have dialup and only one phone line. Not good to go online in the daytime.

---

### Post by ComplexNumber on 2007-01-20
> **rapattack1 said:**
> I have deleted that debian line.....can't think of the exact thing but anyway it is done. Reload has shown that audacity is listed but I still am getting nowhere.
i suspect that certain packages need to be upgraded first. deselect 'audacity' and any others you may have selected, then click 'reload'. press the 'mark all changes' button, then press 'apply'. i think it must be due to some inconsistancy in the database.

---

### Post by rapattack1 on 2007-01-20
I have nothing marked for installation and synaptic is not allowing me to do it for audacity. As far as I know of have the latest of everything.

---

### Post by williamts99 on 2007-01-26
What version of Ubuntu are you using?

---

### Post by rapattack1 on 2007-01-26
5.04

---

