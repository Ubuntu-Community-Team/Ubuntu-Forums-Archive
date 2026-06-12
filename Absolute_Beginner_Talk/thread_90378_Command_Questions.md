---
title: "Command Questions"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Alok on 2005-11-14
Hi Everyrone

I am new to this. I downloaded and installed Ubunto 5.10 and it is running OK.
had some quesitons like
1) When I type "man mail" and hit enter it does not gice me any manula for the command man

2) I think there is some Shell difference. Is there anyways, I can go to the other(Korn) shell and see all these things like manuals for all Korn commands.

3) like "man finger" it again shows NO Manul found

I have a book which shows me how to work on Unix but all the commands there are like Korn shell commands. 

4) Is there anyways, I can go to Korn shell in Ubuntu?

please advise

---

### Post by Kapre on 2005-11-14
[QUOTE=Alok]Hi Everyrone

I am new to this. I downloaded and installed Ubunto 5.10 and it is running OK.
had some quesitons like
1) When I type "man mail" and hit enter it does not gice me any manula for the command man

2) I think there is some Shell difference. Is there anyways, I can go to the other(Korn) shell and see all these things like manuals for all Korn commands.

3) like "man finger" it again shows NO Manul found

I have a book which shows me how to work on Unix but all the commands there are like Korn shell commands. 

4) Is there anyways, I can go to Korn shell in Ubuntu?

please advise[/QUOTE]

maybe you did not install all the man pages. I just checked on mine and it shows the manual for finger. I dont think the man for mail is present (as I have the same output when I tried it).

K

---

### Post by kelsey23 on 2005-11-14
For man mail, install the docs for mail. I have the man for mail on my system :-)

As far as Korn, I have never used it, but the commands should pretty much be the same, the only difference would be the shell scripting. When you type:
$tar xvzf <file.tar.gz>
into bash, you aren't executing a bash command, but a program, tar in /usr/bin
Same thing when you type
$man <program>
you aren't typing a command specific for that shell, but just launching a program :-)

---

### Post by Alok on 2005-11-14
How do I install the Manual or all the man pages

please advise

---

