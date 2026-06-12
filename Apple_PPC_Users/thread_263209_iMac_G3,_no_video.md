---
title: "iMac G3, no video"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by clyde9999 on 2006-09-22
No video using Ubuntu Dapper 6.06 ppc on my little iMac G3 400Mhz. When live CD gets to the point where video should start, I hear startup audio, but do not see anything.

Thanks in advance for any help.

---

### Post by sbentzen on 2006-09-22
sorry, it's not supported for g3 imacs EDIT: you should use the alternate installer

---

### Post by avtolle on 2006-09-22
Can you get to the command line by CTL+Alt+(f1-f6)?

---

### Post by clyde9999 on 2006-09-22
> **avtolle said:**
> Can you get to the command line by CTL+Alt+(f1-f6)?

Yes, I can get to the command line.

---

### Post by avtolle on 2006-09-22
[http://www.ubuntuforums.org/showthread.php?t=260558](http://www.ubuntuforums.org/showthread.php?t=260558) may be of help to you, then; let us know if it works.

---

### Post by clyde9999 on 2006-09-22
> **avtolle said:**
> [http://www.ubuntuforums.org/showthread.php?t=260558](http://www.ubuntuforums.org/showthread.php?t=260558) may be of help to you, then; let us know if it works.

Okay, I will let you know, and thanks!!

---

### Post by RHTopics on 2006-09-22
Here is another link on how to solve this problem.  This is a problem for both Breezy (5.10) and Dapper (6.06) releases.

[http://www.ubuntuforums.org/showthread.php?t=75604&highlight=imac+g3+live+cd+blank](http://www.ubuntuforums.org/showthread.php?t=75604&highlight=imac+g3+live+cd+blank)

Because people trying out Ubuntu for the first time on their iMac G3s run into this situation, the moderators should consider posting a sticky in this subforum for the solution.

---

### Post by clyde9999 on 2006-09-24
I can get to the Console and use "sudo vi /etc/X11/xorg.conf" to get to the xorg script, and I can navigate to the "Monitor" section, but have no ability to change any values. Maybe I need to login as root or something like that, but not sure how?? :-k

---

### Post by Ross Hend on 2006-09-24
I had the same problems with my G3 iMac. You get just a black screen don't you? Follow this thread and read the things it links to. This is for Kubuntu not Ubuntu and also for breezy not dapper so be careful to pay attention to the things that need to be done differently.

[http://ubuntuforums.org/showthread.php?t=95426](http://ubuntuforums.org/showthread.php?t=95426)

Hopefully that'll fix your problem. Post again if you need any assistance.

Edit: And about the editing problem, try using nano instead of vi, it's more like a traditional text editor.

---

