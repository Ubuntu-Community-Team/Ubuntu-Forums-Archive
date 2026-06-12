---
title: "Ubuntu Workstation vs. Server..."
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by MCope on 2007-12-06
Hardware Info:
I built a new system with a Core 2 Duo processor,4 gig of memory,  SataII 400 gig HD, DVD Ide, Sata DVD RW and Nvidia 7300 256mb video.  I have Gutsy  64 bit Workstation running on it without any problems.  Well accept for the Realtek gigabit driver.  Which I down loaded the files and need to compile. So until that gets fixed, I am running  a Realtek 100mbs card.

Intended Use:
I plan on running VM Player to create a VM partition with XP PRO 64 bit running in it.  Not that I am thrilled to run XP but there are certain apps I need to run that won't run under Linux.  By running the XP in VM, I can have both Linux and XP talking to each other and acting as independent PC's.

I also plan on using the system under Ubuntu as a FTP server and have it work with the other systems using Samba to communicate with PC's on a MS Workstation environment.

Conclusion:
I have a choice of using VM Player or VM Box.  I did not see where there was a stable 64 bit VM Box.

If anyone out there has suggestions or have attempted this type of configuration, please let me know.

After running Gutsy 64 bit Workstation I am impressed with how it works.  Would it be better just to go over to 64 bit Server instead of using Workstation for my intended use?

Once I have accomplished my goals, I would like to publish how I made it all come together.  Which forum would one suggest to publish the information?

Have a great computing day!
Mike Cope

---

### Post by Hospadar on 2007-12-06
well I think probably workstation would be better, it sounds like you have a pretty capable machine and should have no issues handling the extra load of a GUI.  really the only difference between server and workstation is that server comes without and GUI, no gnome, etc. (although you can add it later if you want).  Any server stuff (ftp/ssh servers) can also be installed an will run the same as it would on server or workstation.

As for your virtual machine, there may not be a stable version for 64 bit of what you are looking for, you may want to consider just running 32 bit gutsy for the added compatibility, unless you are handling huge server loads or doing giant jobs, it's hard to notice a difference.  That said, I don't know about running a 64 bit os in VM that is supervised by a 32 bit OS, i'm not really sure if/how it would work, so that might be an issue.

---

### Post by Vadi on 2007-12-06
Actually I read that the server edition is specifically optimized for servers (how it handles applications requests, CPU management and all).

---

### Post by MCope on 2007-12-06
Thanks for the reply people.
I have just changed back over to the i386 Gutsy workstation.  I will eventually post my progress and report back when completed.  What I don't understand is why there is more strength support in the 32 bit side instead of 64.  With the systems being manufactured today, a lot of the current boards can support the 64 bit architecture without too much effort.

I can on think there is still so many 32 over 64 bit users the effort hasn't been as fast.

Everyone have a great day!
Mike

---

