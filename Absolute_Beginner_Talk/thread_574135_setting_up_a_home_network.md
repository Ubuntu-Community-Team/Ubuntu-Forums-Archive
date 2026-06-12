---
title: "setting up a home network"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by jcats on 2007-10-12
I know this should go in "Network", but I am completely new to  Ubuntu and to Linux. 
I have 2 Windows boxes networked together. I want to add my Ubuntu box to the network.
I have a wired Linksys router and it sees all the computers. I installed Samba, and from the Ubuntu box, I can see the shared files of the Windows boxes. But I can't get the Windows boxes to see the Ubuntu box.
I do have files in the Ubuntu box, as shared.
Any help here would be most appreciated.
Thanks in advance
Jcats

PS What does "bump" mean?

---

### Post by steve-shinn on 2007-10-12
I had the same issues a few months back, try this link and the guides contained within the link. It worked for me.
[http://ubuntuforums.org/showthread.php?t=432075](http://ubuntuforums.org/showthread.php?t=432075)

Good luck

---

### Post by jgrabham on 2007-10-12
> **jcats said:**
> 
PS What does "bump" mean?

Bring Up My Post  ;)

---

### Post by phr0ze on 2007-10-12
Try to use Ubuntu machine IP address instead of name on the windows machines.

Bump is used in forums to 'bump' a conversation back to the top of the list so it gets more attention. I try to avoid doing it.

For example. You ask a question and no one answers for a week. You would post in your own thread the word 'bump', this will bring your thread back to the top of the list so it gets more exposure.  Very few people look at stuff that is more than a few pages deep and with the speed threads are created here that could be just a few hours.

Instead of bump, find your original thread and post some of the additional steps you have taken since your original post. This will show others that you are trying, and it avoids answers that you have already done.

---

### Post by jcats on 2007-10-13
Thanks peoples, for the replies. I'll try not to bump :)
Thanks Steve for the link. I spent a bit of time going thru it, but my ignorance of Linux is killing me.
I installed Samba, and that got me to the point where I can see the Windows boxes. I can ping all three of the computers, linux can ping the Windows and vica versa. But still Windows cannot see the shared files in the Ubuntu box. There is talk in your link of changing settings in Samba. How do I get to it? (sorry if this seems so simple for some of you)
 I noticed that the Windows units are listed as "workgroup" and the Ubuntu 1 is listed as "mshome". I'm sure that is an issue, but I can't figure out how to change that.
This morning when I booted up and checked the Ubuntu network, there now is 2 computers listed in mshome.  1) jcats-desktop, which was there before and when I click on it, I see my shared files. The other one is listed as random numbers and letters. When I click on it, after several minutes of searching, it tells me it cannot open the files.
Thanks again for all your help. Any links to help educate me on the ways of Ubuntu and/or Linux would be most appreciated.

jcats

My network is set up on DHCP, so the addresses are constantly changing. Should I be assigning static addresses? This is never an issues with just Windows

---

### Post by andguent on 2007-10-13
I'm on Gutsy, so it is possible your menus are different, but try clicking the System menu -> Administration -> Shared Folders.

If it isn't there, try using Add/Remove programs to install samba, the windows file sharing mechanism. Note: I just tried following my own notes and found that Add/Remove has a program called "Samba" which really should be called "Samba Config Helper" or similar. It seems helpful nonetheless.

The power user way of doing it is to edit /etc/samba/smb.conf with a text editor, but that isn't necessarily newbie friendly. :)

---

### Post by jcats on 2007-10-28
[FONT="Comic Sans MS"]I've been away for a while, because I've discovered thats it's my lack Linux skill is what is holding me back. So for the last few weeks, I've been studying.
Thanks, Steve for your link on setting up Samba. Between my better understanding and your link, I now have a fully functioning network.
Thanks to everyone that took the time to answer. I'm sure Ill be back with more noob questions ;)
jcats[/FONT]

---

