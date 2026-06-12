---
title: "A tool to search the web and download files?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by James85 on 2007-10-02
When I used Windows I had a program called websnake that would search the web for different files like pictures or music files, and download them all to a folder for me.

Is there anything like this for Ubuntu?

I tried searching in Synaptics and Google, but i didn't find anything.

---

### Post by Paul820 on 2007-10-02
Have you tried running it in wine?

---

### Post by kellemes on 2007-10-03
And if Wine doesn't work (it's not in there app.db) you can always setup a vm using VirtualBox or some other brand..

---

### Post by Oki on 2007-10-03
I have never used websnake before, and I really don't understand what you are looking for. 
Download files can be done with p2p programs or torrent sites. If you want to download files from one or more sites you could use wget. It is command based but works very well; I tried and it downloaded an entire site to a folder on my pc. Take a look at this thread; [http://www.linuxforums.org/forum/linux-applications/3277-webcrawler-such-teleport-pro-superbot-linux.html](http://www.linuxforums.org/forum/linux-applications/3277-webcrawler-such-teleport-pro-superbot-linux.html)

To see the different options for wget take a look at the man page;  [http://www.cbi.pku.edu.cn/Doc/CS/wget/man.wget.html](http://www.cbi.pku.edu.cn/Doc/CS/wget/man.wget.html)

---

### Post by n3tfury on 2007-10-03
i use google + right click/save as...   ;P

---

### Post by floke on 2007-10-03
> **n3tfury said:**
> i use google + right click/save as...   ;P

ah the old ways are always the best!

---

### Post by yodel on 2007-10-03
that's great.
wget -rp url

---

### Post by James85 on 2007-10-03
> **Paul820 said:**
> Have you tried running it in wine?

> **kellemes said:**
> And if Wine doesn't work (it's not in there app.db) you can always setup a vm using VirtualBox or some other brand..

I installed Ubuntu Linux to use Linux programs. What's the point of leaving Windows but using the programs in Linux with wine?
Anyway, my cousin told me that wine isn't very reliable.

---

### Post by James85 on 2007-10-03
> **n3tfury said:**
> i use google + right click/save as...   ;P

> **floke said:**
> ah the old ways are always the best!

You must be newer to Linux than me Lol!, even **I** know that Google isn't a Linux app like websnake.

Look here: [http://www.websnake.com/](http://www.websnake.com/) If you had used Google before posting, you would have understood my question. But thanks for trying to help me as best as you could.

---

### Post by James85 on 2007-10-03
> **Oki said:**
> I have never used websnake before, and I really don't understand what you are looking for. 
Download files can be done with p2p programs or torrent sites. If you want to download files from one or more sites you could use wget. It is command based but works very well; I tried and it downloaded an entire site to a folder on my pc. Take a look at this thread; [http://www.linuxforums.org/forum/linux-applications/3277-webcrawler-such-teleport-pro-superbot-linux.html](http://www.linuxforums.org/forum/linux-applications/3277-webcrawler-such-teleport-pro-superbot-linux.html)

To see the different options for wget take a look at the man page;  [http://www.cbi.pku.edu.cn/Doc/CS/wget/man.wget.html](http://www.cbi.pku.edu.cn/Doc/CS/wget/man.wget.html)

Thanks Oki !! That was a great link, I got all the commands for wget. I didn't realise that it was so easy to do all this stuff with the terminal. Just realised that the terminal has man pages in it. I copied and pasted man -k and then added loads of stuff after it. Amazing.

---

### Post by Paul820 on 2007-10-03
> **James85 said:**
> I installed Ubuntu Linux to use Linux programs. What's the point of leaving Windows but using the programs in Linux with wine?
Anyway, my cousin told me that wine isn't very reliable.

Because some people have to get away from the grasp of microsoft, but they need one or two programs to be able to be run in ubuntu that they cannot get replacements for. It was only a suggestion, i don't use it myself.

---

