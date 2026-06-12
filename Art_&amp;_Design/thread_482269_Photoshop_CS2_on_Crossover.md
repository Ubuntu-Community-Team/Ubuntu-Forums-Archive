---
title: "Photoshop CS2 on Crossover"
date: 2007-06-23
forum: Art &amp; Design
---

### Post by Paradux on 2007-06-23
Hi all,
I'm brand new to Ubuntu as I just converted from Windoze XP. I think I've got the jist of most of it but I absolutely have to get Photoshop running! I have Crossover pro 6.0 and I can't install from the .exe file. I get past the virus scanning but can't get any further 'this operating system is not supported by this installation'
If CS2 isn't supported then which versions are?

I guess you guys have experience on this behalf and I will gladly take any help I can get. 
Thanks in advance!

*Another thought*
Anyone know how to emulate it on Wine if not?

---

### Post by Hairy_Palms on 2007-06-23
photoshop 7.0 runs fine, 
Photoshop CS2 portable edition runs fine too, some people can get CS2 running but its slow and has problesm with the registration

---

### Post by Crafty Kisses on 2007-06-23
> **Hairy_Palms said:**
> photoshop 7.0 runs fine, 
Photoshop CS2 portable edition runs fine too, some people can get CS2 running but its slow and has problesm with the registration

You can run those on Wine right?

---

### Post by fdrake on 2007-06-23
> **Paradux said:**
> Hi all,
I'm brand new to Ubuntu as I just converted from Windoze XP. I think I've got the jist of most of it but I absolutely have to get Photoshop running! I have Crossover pro 6.0 and I can't install from the .exe file. I get past the virus scanning but can't get any further 'this operating system is not supported by this installation'
If CS2 isn't supported then which versions are?

I guess you guys have experience on this behalf and I will gladly take any help I can get. 
Thanks in advance!

*Another thought*
Anyone know how to emulate it on Wine if not?

don't try to emulate windows image or video editing software. it's not worth the time (an emulation requires at leats 4 times the time to complete that process under the native system). my suggestion is just create a partition (6-10 gb on ur hd) and install windows on it. you can access both partitions with some softwares from Linux and windows.

---

### Post by mack1082 on 2007-06-23
How well will it work in VMware?  I haven't tried, but I would think it would do fine on a fast enough PC.. it would save dual booting anyway.

---

### Post by Hairy_Palms on 2007-06-23
your wrong fdrake, photoshop 7.0 is just as fast under wine as it is native, cs2 portable is just as fast once its runnig it just has a long startup time. and the time it takes to startup is easily less tim than it takes to reboot

---

### Post by Crafty Kisses on 2007-06-23
> **Hairy_Palms said:**
> your wrong fdrake, photoshop 7.0 is just as fast under wine as it is native, cs2 portable is just as fast once its runnig it just has a long startup time. and the time it takes to startup is easily less tim than it takes to reboot

That answered my question. :p

---

### Post by fdrake on 2007-06-23
> **Hairy_Palms said:**
> your wrong fdrake, photoshop 7.0 is just as fast under wine as it is native, cs2 portable is just as fast once its running it just has a long startup time. and the time it takes to startup is easily less tim than it takes to reboot

i didn't express myself correctly, when i said about emulating photoshop cs2. u see wine(Wine' derives from the recursive acronym Wine Is Not an Emulator) it's not an emulator at all. vmware  is an emulator, and they require a lot of ram and time to run. wine on the other hand runs directly on the linux system.
don't know about crossover..
 again sorry for my misinterpretation.

---

### Post by gandrews on 2007-06-25
Regarding fdrake's comments (above):
-the name WINE is amusing, because WINE is, in a real sense, an emulator. It fools the applications it is hosting into thinking they are running on Windows, so--in that sense--it emulates a Windows environment. I believe the term originally meant a software emulation of a different CPU, however, sometimes called a "compatibility" mode.
-VMWare is in no sense an emulator. Yes, it needs gobs of RAM and disk, but that's because it's a virtualization platform. It provides a virtual machine into which you install an entire operating system (such as Ubuntu or MS Windows), and then install your apps for the "guest" platform.

So, if  you were to install one of VMWare's free products (Player or Server) on your Ubuntu system, and then install a licensed version of Windows XP (for example), you could run most of the Adobe products in a VMWare, umm, "window" on your Ubuntu desktop. Or full screen, if you prefer.

I say "most," because VMWare has some limitations. AFAIK, the virtual display card provided is quite limited. Most modern games won't install in a Windows guest, for example. Although I haven't tried it, I suspect Photoshop would run just fine, but you'd probably have difficulties with Adobe's video editor. VMWare may have some tweaks of which I'm unaware, however.

With regard to this thread's original topic:
-as a long-time Windows (and DOS) user, my opinion is that Adobe--particularly with regard to Reader (nee Acrobat Reader)--may have the second-to-worst Windows programmers on the planet. I've also owned and used Photoshop CS, CS2, and tried out the CS3 beta, as well as some other Windows-based Adobe products. I give them 11 out of 10 for style, but about 4 out of 10 for execution. Photoshop and Illustrator are remarkable, feature-laden mega-applications, but plagued with continuing bugs and what must be remarkably bad code underneath. 

For the money they demand, their products should be better crafted--a lot better.

And for the record, the absolute worst Windows-platform programmers on the planet work for Apple. iTunes for Windows is an abomination. Don't bother clicking while it's updating its database; the application just freezes. That's a "feature" incorporated into Banshee as well, I see. . .

Oh, well, 25 years ago the PC was considered more of a toy than a "real" computer. Folks were wondering back then if we'd ever be able to do anything useful on a "personal computer." Eventually, things always change. . .

8-)

---

### Post by phizikal on 2007-06-26
gandrews is right. ;)

---

### Post by umattu on 2007-06-26
> **mack1082 said:**
> How well will it work in VMware?  I haven't tried, but I would think it would do fine on a fast enough PC.. it would save dual booting anyway.


I have a virtual XP machine under VMware ONLY for photoshop cs2, if you ask me there is no noticable differance, but my virtual machine has a gig of ram dedicated to it.

---

### Post by cleentrax on 2007-06-26
> **fdrake said:**
> don't try to emulate windows image or video editing software. it's not worth the time (an emulation requires at leats 4 times the time to complete that process under the native system). my suggestion is just create a partition (6-10 gb on ur hd) and install windows on it. you can access both partitions with some softwares from Linux and windows.

That defeats the purpose for me. If I'm going to maintain a Windows license, there's no point in running Ubuntu.

---

### Post by fdrake on 2007-06-26
> **cleentrax said:**
> That defeats the purpose for me. If I'm going to maintain a Windows license, there's no point in running Ubuntu.

well even with vmware u need a windows license . right?

ubuntu is meant to be an open source system, well then why do u install the proprietary media formats, and drivers then?

Just because a software doesn't run (well) under ubuntu, u stop using it?? I am not talking just about photoshop but any kind of program. Personally i think that many people in this forum dualboot their computers, for many reasons (games, professional applications etc...). 

Anyway i do hope in the future  Ubuntu will be able to run under wine  more and more windows application , that would make Ubuntu the os of choice for professionals,students and maybe even for gamers.

---

### Post by cleentrax on 2007-06-27
You make some good points. I've been experimenting with Linux for 10 years, and I have been a 3-OS household for three years (OSX, Ubuntu, WinXP). Running multiple operating systems is a pain, due to permissions issues, incompatible file systems, etc.  Right now I have to use Illustrator, Flash and Photoshop for my business, but I would much prefer to do it with native versions, or with Wine, to avoid Windows entirely.



> **fdrake said:**
> well even with vmware u need a windows license . right?

ubuntu is meant to be an open source system, well then why do u install the proprietary media formats, and drivers then?

Just because a software doesn't run (well) under ubuntu, u stop using it?? I am not talking just about photoshop but any kind of program. Personally i think that many people in this forum dualboot their computers, for many reasons (games, professional applications etc...). 

Anyway i do hope in the future  Ubuntu will be able to run under wine  more and more windows application , that would make Ubuntu the os of choice for professionals,students and maybe even for gamers.

---

