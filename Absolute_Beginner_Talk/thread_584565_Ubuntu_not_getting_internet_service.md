---
title: "Ubuntu not getting internet service"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by gcrussell1 on 2007-10-21
I've just installed Gutsy (dual-boot with XP Home) for my first Linux experience. My specs are as follows:

HP zx5000 laptop
3.0 GHz P4 Northwood
ATI Mobility 9600
768 MB DDR 2700

If any other specs are relevant, I'll be happy to give them, but we'll start with this.

So far, everything seems to be running well, contrary to most HP Laptop users' experiences with Gutsy. Everything, that is, except the internet connection. I'm on a university LAN at the Chinese university where I currently live and teach, and I've set my static IP, subnet, gateway, and DNS servers. Even with all of this information set up, I'm not getting any connectvity. Is this likely a problem on my end, or do some networks simply not support Linux? I'll see about talking to my network administrator tomorrow, since I can't really learn Linux without any connectivity, but if anyone can tell me what I might need to do on my end I would appreciate the help.

Thanks.

---

### Post by BaffledMollusc on 2007-10-21
> **gcrussell1 said:**
> I've just installed Gutsy (dual-boot with XP Home) for my first Linux experience. My specs are as follows:

HP zx5000 laptop
3.0 GHz P4 Northwood
ATI Mobility 9600
768 MB DDR 2700

If any other specs are relevant, I'll be happy to give them, but we'll start with this.

So far, everything seems to be running well, contrary to most HP Laptop users' experiences with Gutsy. Everything, that is, except the internet connection. I'm on a university LAN at the Chinese university where I currently live and teach, and I've set my static IP, subnet, gateway, and DNS servers. Even with all of this information set up, I'm not getting any connectvity. Is this likely a problem on my end, or do some networks simply not support Linux? I'll see about talking to my network administrator tomorrow, since I can't really learn Linux without any connectivity, but if anyone can tell me what I might need to do on my end I would appreciate the help.

Thanks.
As far as I know, networks are totally OS agnostic, so it shouldn't matter that you're using linux.

I once had a problem that the networking chip on my motherboard wasn't supported by the linux kernel. That might be worth checking. Aside from that, I haven't any suggestions, sorry.

I suspect that any other troubleshooters are going to ask you to at least run the command "ifconfig" in a terminal and post the output, so you might want to do that for a start :)

Edit: Oh, and and can you post the output of "lspci" as well? That should let us know what your networking chip is.

---

### Post by TeaSwigger on 2007-10-21
That it's Linux should not be an issue. That you're on a university LAN and moreover in China, now that could have a lot to do with it.

Are you referring to internet connectivity or with local network peers? If you are referring to or need to involve a LAN which is a Windows Network, this will require a component called SAMBA. Internet connectivity is common with Linux and Windows. Linux has a different network system from Windows however. SAMBA is required to interface a Linux computer with a Windows Network. This guide is very helpful in easing this somewhat challenging matter:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

On a side note, may I suggest my point of view: Linux is well worth working with, from other aspects such as philosophic points without ever coming to technical considerations, but one doesn't learn Linux so much as gain knowledge and skills by osmosis if you will - needs and wants. It makes your computer truly your own, granting you legal right to study and learn everything with the blessings of the software writers granted freely. By nature it brings responsibility; it is yours to make or break. Much learning and patience will likely be best involved. Good luck to you, and do enjoy yourself :)

---

### Post by gcrussell1 on 2007-10-21
The quick help from both of you is much appreciated. It appears I spoke too soon, however. I had switched from Ubuntu to XP to connect and post that message, and upon returning to Ubuntu to check ifconfig and lspci, I found that I was getting internet connectivity. I guess I just had to restart the OS to get moving.

Incidentally, I'm really, really new to this. So new that I don't even know how to run the commands ifconfig and lspci. Now, I don't expect anyone to tell me here, since it's my business to find the information myself, and I'm sure it's available in about a hundred thousand or so posts on this forum, but since you're already looking at this...

TeaSwigger, thanks for the encouragement - I'm really looking forward to getting to know Linux in all its glory. Both MS and Apple irritate the hell out of me with their monopolistic attitudes to OS's and other products, so I'm excited to move away from their bunk. Unfortunately I'll still be relying somewhat on MS, since I enjoy gaming here and there, but making the everyday move to a Linux OS would still be a nice triumph. Cheers!

---

### Post by BaffledMollusc on 2007-10-21
> **gcrussell1 said:**
> 
Incidentally, I'm really, really new to this. So new that I don't even know how to run the commands ifconfig and lspci. Now, I don't expect anyone to tell me here, since it's my business to find the information myself, and I'm sure it's available in about a hundred thousand or so posts on this forum, but since you're already looking at this...

No problem, and I'm glad things are working.

When people say they run a command under linux, they generally mean they typed in a specific command  in a terminal (or console). This is kind of like the MS-DOS command prompt thing in Windows.

To get a terminal you choose Applications->Accessories->Terminal.

This will give you access to the command line. Essentially this involves typing commands for the operating system to carry out. The command line can often be quicker and more powerful than using a GUI, but it takes some getting used to. Feel free to enter "ifconfig" and "lspci" in your terminal to see what happens :)

A guide to the command line can be found at, for example, [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by gcrussell1 on 2007-10-21
> **BaffledMollusc said:**
> No problem, and I'm glad things are working.

When people say they run a command under linux, they generally mean they typed in a specific command  in a terminal (or console). This is kind of like the MS-DOS command prompt thing in Windows.

To get a terminal you choose Applications->Accessories->Terminal.

This will give you access to the command line. Essentially this involves typing commands for the operating system to carry out. The command line can often be quicker and more powerful than using a GUI, but it takes some getting used to. Feel free to enter "ifconfig" and "lspci" in your terminal to see what happens :)

A guide to the command line can be found at, for example, [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Thanks - I vaguely knew most of that, but I didn't know where I was supposed to type the commands in, so thanks a lot for pointing out the terminal to me. I'm starting to pick up some of the (extreme) basics of Ubuntu already, and I really look forward to learning more. I'm going to check that linux commands site right now, as a matter of fact :biggrin:

---

