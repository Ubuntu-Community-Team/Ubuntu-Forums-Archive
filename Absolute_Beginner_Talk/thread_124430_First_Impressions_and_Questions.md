---
title: "First Impressions and Questions"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by alex_s on 2006-02-01
I've tried a couple of distros so far, but Ubuntu has definately been my favorite. Recently, I've decided to give it another shot and install Breezy. I must say, it looks beautiful and is very stable. I have, however, had a few issues. When I tried to install drivers for my (ATI) video card, my computer would simply lock up , at which point I would have to manually restart my computer. Similarily, my (Canon i860) printer doesn't seem to be too compatible with linux, so I've basically given up on using it in linux. I can still print from Windows, so I guess that's ok.. maybe I have to look into VMware as an option? Anyway, I have a couple of questions. 

1) Azereus is slow. On Windows, I used BitComet as my torrent software, which supported multi-torrent downloading. Azereus is similar, but it really does seem to slow down my computer and take up a lot of ram. Are there any other options? (all java programs, including the limewire lookalike "frostwire" seem to be running ridiculously slow). 

2) I was browsing the web, and suddenly a "System Log" window popped up. It seems as if someone is trying to hack into my SSH server.. 
>  Jan 31 20:30:55 localhost sshd[26896]: Invalid user pm from 61.208.89.194
Jan 31 20:30:55 localhost sshd[26896]: (pam_unix) check pass; user unknown
Jan 31 20:30:55 localhost sshd[26896]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=koba.adogawachu.ed.jp 
Jan 31 20:30:57 localhost sshd[26896]: Failed password for invalid user pm from 61.208.89.194 port 41301 ssh2
Jan 31 20:31:00 localhost sshd[26898]: Invalid user am from 61.208.89.194
Jan 31 20:31:00 localhost sshd[26898]: (pam_unix) check pass; user unknown
Jan 31 20:31:00 localhost sshd[26898]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=koba.adogawachu.ed.jp 
Jan 31 20:31:02 localhost sshd[26898]: Failed password for invalid user am from 61.208.89.194 port 41385 ssh2
Jan 31 20:31:04 localhost sshd[26901]: Invalid user close from 61.208.89.194
Jan 31 20:31:05 localhost sshd[26901]: (pam_unix) check pass; user unknown
Jan 31 20:31:05 localhost sshd[26901]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=koba.adogawachu.ed.jp 

And it goes on... SSH looks pretty useful so I don't really want to disable it, what can I do?

3) Where can I find a good guide/book that will teach me linux commands/tips


Thanks. Overall, although I have a few issues, Ubuntu seems like a great project and I plan to stick with it.

---

### Post by grimmson on 2006-02-01
After being a 11 year windoze user I think ubuntu is kinda fun. I'm not the sharpest tool in the shed but I've been able to make it work so far. Try this for nvidia paying attention to your card number [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=install+vidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=install+vidia) I think it took 15 minutes start to finish for a newbie like me. try a search for ubuntu guide. I know i've seen an unofficial for 5.04. Wish I could help more but I'm not much farther laong than you.

---

### Post by christhemonkey on 2006-02-01
[www.tuxfiles.org]("www.tuxfiles.org")
Really helped me get my head around it!

---

### Post by Lord Illidan on 2006-02-01
[quote=grimmson]After being a 11 year windoze user I think ubuntu is kinda fun. I'm not the sharpest tool in the shed but I've been able to make it work so far. Try this for nvidia paying attention to your card number [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=install+vidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=install+vidia") I think it took 15 minutes start to finish for a newbie like me. try a search for ubuntu guide. I know i've seen an unofficial for 5.04. Wish I could help more but I'm not much farther laong than you.[/quote]

He has an ATI card..

You want some help with Ubuntu and a guide? How about the wiki : [http://wiki.ubuntu.com/]("http://wiki.ubuntu.com/")

About Linux Commands, don't forget google.

Also, before you type a command into the terminal... such as... ```
top
```, type ```
man *name of command*
``` without asterisks..
It will give you info about said app..

eg, ```
man top
```

```
       The  top  program provides a dynamic real-time view of a running system.  It can display system summary information as well as a list of tasks currently
       being managed by the Linux kernel.  The types of system summary information shown and the types, order and size of information displayed for  tasks  are
       all user configurable and that configuration can be made persistent across restarts.

```

---

### Post by alex_s on 2006-02-01
Thanks guys for the help. Anyone have any idea how to stop the attack on my ssh server? Thanks again.

---

### Post by grimmson on 2006-02-01
I said I wasn't the sharpest tool in the shed. fact of the matter is I'm an idiot. I skipped over that whole ati part some how. Oops.:rolleyes:

---

