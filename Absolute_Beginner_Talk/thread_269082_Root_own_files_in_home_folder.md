---
title: "Root own files in /home folder"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by SirShaggy on 2006-10-01
OK, just a couple of questions here......
I just did a fresh install of Ubuntu (Dapper) on a new (to me) laptop.
After the basic install, then update, I installed all of the packages I like to use and the multimedia stuff. Anyway, I was just looking in MY /home folder and there are files in there owned by root. Is this normal? I would assume (being new to Linux in general) that roots files would be in the /root folder and all the files in /home/shaggy would be mine?!?!
Two of the file folders in question are: initng and modem. They were both created as I was setting up the extra programs I use and working with my Very, Oh so FUN, Winmodem!
Anyway, just curious if I made mistakes while configuring this laptop or if this is somewhat normal. I know I make mistakes, sometimes I just don't know till it's too late!:-D 
This is my 5th Ubuntu install, 3rd system, and each one gets better and easier. This time, I did away with XP. It was way to slow on this Celeron D anyway. Thanks again for your time,
SirShaggy

---

### Post by duan on 2006-10-01
whatever you install with the 'sudo' command gets owned by root by default.

maybe you installed the software to $HOME as an option with the sudo command?

but yes the stuff in your home folder should  belong to you by default, and the files owned by root in / but it doesn't mean things wont work otherwise.

in ubuntu you sort of are always root(if you only have one user), but 
security is ensured with the sudo command. Makes life easier.

---

### Post by SirShaggy on 2006-10-01
Thank you. I assumed that is what I had done. Everything does work fine, I just had to ponder and ask. I am the curious type!
SirShaggy

---

### Post by duan on 2006-10-04
Pleasure.
the only issue I can thinik of though is if you upgrade distributions and you have files lying around in strange places that it might be more difficult to keep track.

---

### Post by aysiu on 2006-10-04
The only thing I can think of is launching graphical applications with *sudo* instead of *gksudo* or *kdesu*.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

