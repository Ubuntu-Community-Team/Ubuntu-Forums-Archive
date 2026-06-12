---
title: "ssh help"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by stake on 2006-10-21
1. How do i install ssh?
2. How can i configure it?
3. What should i do in order to make it work?
4. What i must do in order to let someone join my pc?
5. How can i connect to someone's pc?
6. Can i remote with ssh Windows XP or any other version of linux or just Ubuntu?
7. With ssh you can remote the desktop or just the terminal?

i need details in order to understand because i am new in linux world

p.s: sorry for my bad english

---

### Post by dbd on 2006-10-21
This should answer some of your problems:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by nyinge on 2006-10-21
1 - 5 and 7 should be answered in the link dbd provided.  As for #6 of your question, you'd need a ssh server installed on your XP, since XP doesn't come with one AFAIK.  

Any suggestion about F/OSS ssh server on XP?

---

### Post by hyper_ch on 2006-10-21
Cygwin could be installed on XP... it has a SSH server I think....

---

### Post by StormNet on 2006-10-21
I ssh from my desktop or laptop into my server all the time using XP, i am currently trying out 2 different environments in order to accomplish this. OpenSSH for Windows, and Putty. Each has it good points and things that need to work on. My personal taste leans towards OpenSSH which allows me to SSH into my server from any command prompt and convinient for me. Putty you have to use its own terminal in order to access the other machine.

PuTTY
[http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")
OpenSSH
[http://sshwindows.sourceforge.net/]("http://sshwindows.sourceforge.net/")

---

### Post by hyper_ch on 2006-10-21
Oh, I thought he wanted to access his winxp machine through SSH :)

---

### Post by stake on 2006-10-21
sjau  that i was asking for ... i want to access to my friends WinXP pc !!! is that possible with the Cygwin ?

StormNet i have a putty on my WinXP but how can it help me ?

---

### Post by hyper_ch on 2006-10-21
stake: You must check whether Cygwin also offers a SSH Server... I'm not sure about that...

Otherwise you could install a vnc client on his WinXP box and then have a connection through that... meaning remote desktopping instead of "pure shell2 as it is with SSH

---

### Post by StormNet on 2006-10-21
Unfortunately, i am not able to access my desktop from where i am, but you can follow these instructions of on how to use PuTTY.

[http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter2.html#gs]("http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter2.html#gs")

It will step you through almost every step of the way. All you will need is:
[LIST]
[*]Host Name: the IP of the computer you want to log into
[*]Protocol: SSH
[*]Port: 22 (thats the default port, unless you changed it)
[/LIST]

---

### Post by Quintin Riis on 2006-10-21
Search [www.google.com](www.google.com) for the following terms:
PuTTY
TightVNC
remote desktop 
ssh 

..and do some reading.

Read the manual page for ssh.  'man ssh' in a terminal.  sshd should be installed by default.  Try 'ssh 127.0.0.1' to see if sshd is running and accepting connections.

If after looking at the links pasted above and reading on google you still have issues let me know.

---

