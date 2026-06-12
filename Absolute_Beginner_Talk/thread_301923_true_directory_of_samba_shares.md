---
title: "true directory of samba shares"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by twidget on 2006-11-17
Hi
can anyone tell me what directory samba shares are mounted on? ie /usr/samba/local_host or whatever. at my work we run a circuit board layout tool called EAGLE. what im trying to do is make it so that all instances of EAGLE use the same directory on the same hard drive for the projects and lbr folders. im thinking of maybe just using a scrap pc i have to hold the files on a couple RAIDed harddrives. the problem is that while i can change the location for the directories EAGLE it wont accept smb// as a directory. i cant use nfs since the main computer used for EAGLE is running xp.

---

### Post by Swab on 2006-11-17
> **twidget said:**
> Hi
can anyone tell me what directory samba shares are mounted on? ie /usr/samba/local_host or whatever. at my work we run a circuit board layout tool called EAGLE. what im trying to do is make it so that all instances of EAGLE use the same directory on the same hard drive for the projects and lbr folders. im thinking of maybe just using a scrap pc i have to hold the files on a couple RAIDed harddrives. the problem is that while i can change the location for the directories EAGLE it wont accept smb// as a directory. i cant use nfs since the main computer used for EAGLE is running xp.

I think you'll need to restate the question.  It's not at all clear.  Are you asking how to access Samba shares from the XP machines?  If so, it's the same as a Windows share (\\servername\sharename)

---

### Post by twidget on 2006-11-17
sorry about that. let me try again.i have a program that lives on multiple computers at work.i want to have all the project and library files on one computer to keep things synchronized. i can tell the program under which directory these files are stored but it will not accept smb://computer/projects. what i would like to know is what i should tell it instead of smb://computer/projects.
ideally the final resting place of these directories will be an old computer with xubuntu installed but that's a project for later.
right now the files live on the windows box and im trying to get the program on my kubuntu box to access them.

---

