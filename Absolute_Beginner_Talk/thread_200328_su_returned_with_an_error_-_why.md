---
title: "su returned with an error - why?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by dglp on 2006-06-20
Recently I have been getting this error message every time I try to use Administrator Mode. 

I don't know what makes this happen, and I don't know how to get around the obstacle so that I can do things like use the package manager.

---

### Post by DSn0wMan on 2006-06-20
Could you provide more details on the problem? Posibly the command you are entering, and the error code you receive.

---

### Post by DirtDawg on 2006-06-20
try sudo

example:
sudo dpkg -i neato.deb

or if you wish:
sudo su

Sorry if this is obvious, but it's a common mistake amongst newcomers.

---

### Post by FredB on 2006-06-20
Indeed. Using sudo is a security feature, also used in MacOS-X terminal.

---

### Post by dglp on 2006-06-21
Thanks for responding.

DSn0wMan, I am using Kubuntu, and within it, various tools that give me the option of using 'Administrator Mode'. It's just a button on a given window, not a command-line function. Everything worked okay until recently when I started getting a pop-up error message in response to clicking on the Administrator Mode button. 

DirtDawg: Too right! Newbie I am, to the extent that I've forgotten everything I read about sudo - so your response is a helpful reminder.

---

### Post by cypher_666 on 2007-02-03
has anyone figured out why this is? i also am getting this error for no reason, i turned my laptop on, and got an update package notifier in my bottom bar, normally i click on it and it opens up and i upgrade the package, but i get the same error, a box pops up with the same error and i cant do anything apart from click OK

i get the same error when trying add/remove programs and when i type in one of the suggested terminal commands given above. i get this in repl:

>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0


hope someone sees this and can help

---

### Post by melancholeric on 2007-02-03
> **cypher_666 said:**
> has anyone figured out why this is? i also am getting this error for no reason, i turned my laptop on, and got an update package notifier in my bottom bar, normally i click on it and it opens up and i upgrade the package, but i get the same error, a box pops up with the same error and i cant do anything apart from click OK

i get the same error when trying add/remove programs and when i type in one of the suggested terminal commands given above. i get this in repl:

>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0


hope someone sees this and can help
Boot in recovery (single user) mode. Type "visudo" to edit the sudoers file. There's something wrong with the first 9 lines, obviously.

I've seen something very similar before, something utterly weird in the beginning of the file that simply should not be there and it had to be removed. The user in question didn't have a clue how it ended there. Might be a bug somewhere.

---

### Post by cypher_666 on 2007-02-03
thanks, ill save all me crap then give it a try :)

---

### Post by cypher_666 on 2007-02-03
just like to say that its worked a treat, there was some random stuff at the beginning about an error, so i deleted it and restarted and its all working fine now.

thanks very much, this place is great :)

---

### Post by melancholeric on 2007-02-03
What random stuff was that by the way? Because if it was the same thing that was posted before on this forum it's probably a bug, and quite a serious one too, and should be reported. I couldn't find anything about it on launchpad either.

---

### Post by klebsiella on 2007-02-05
Hi all,

It's my first reply in this forum and I just had the same problem that I resolved following the instructions of the  current thread. I edited the sudoers file and everything look to be arranged;

What I wish to add is the issue that Caused this problem. Actually, I allowed users to mount shared folder as super user in smb4k. I think this have modified the sudoers by adding a list of lines in the top of the file. These lines correspond to kde because anytime that I launch a kde application from the terminal I have this error appearing

X Error: BadDevice, invalid or uninitialized input device...........
....
...

Hope that will help...

all best

---

