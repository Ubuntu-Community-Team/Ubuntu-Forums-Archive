---
title: "Installing Automatix"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-01-24
I downloaded it but when I try to run or extract here I get an error could someone please give me a direct link and instructions. Sorry about the dumb question but I just started using ubuntu about 30 min ago.

and does anyone know how to install firefox 1.5 and flash support ? thankx :)

---

### Post by dueY on 2006-01-24
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by DAXP on 2006-01-24
That post should help, and Automatix can install Firefox 1.5 and most, if not all, plugins.

---

### Post by xXx 0wn3d xXx on 2006-01-25
I tried to install it with automatix but it didn't work :( Is there any other way ?

---

### Post by Sokraates on 2006-01-25
Could you post the error message? 

Did you manage to start Automatix? If so, did you enter your user-password when asked? If not, you (or Automatix in this case) won't be able to install anything.

Just for clarity's sake: whenever you want to install something or otherwise change systemsettings, you need to have "root"- (sometimes also referred to as "superuser") rights. In ubuntu there is per default no dedicated root-account for performing mainanance work. Rather the command 

```
sudo xyz
```

is used. "sudo" will start the command "xyz" with superuser rights. Before, it will ask for your user password. You will see this everytime you start synaptic.

So if you enter no/a wrong password when Automaix starts, it won't run with the rights necessary to install anything.

---

### Post by Bartender on 2006-01-25
Hi, MC1234 -
Hope you don't mind if I drop in on this thread.  On the Automatix thread, I see this instruction:

[COLOR="DarkSlateBlue"]To install Automatix in Ubuntu, do the following from terminal:
Code:

sudo apt-get install xterm 
wget [http://beerorkid.com/automatix/automatix_5.0-1_i386.deb](http://beerorkid.com/automatix/automatix_5.0-1_i386.deb) 
sudo dpkg -i automatix_5.0-1_i386.deb[/COLOR]

Is that all there is to it?  Just copy, paste into terminal, & click "Enter"?  Some things are truly simple in Ubuntu, and lots of things aren't.  Often the helpful folks on these forums assume levels of competency that us newbs don't have, and I'm unable to distinguish the projects that are incredibly easy from the ones that aren't but nobody bothered to include the 39 other steps between start & finish.
Automatix sounds like a really neat package which isn't all that tough, but if MC can't make it happen then I'm likely to run into the same probs...

---

### Post by bloodborne on 2006-01-25
Yep, that's all there is to it. Copy-paste those three lines one at a time into the terminal, and then run Automatix from Applications ---> System Tools ---> Automatix. Couldn't be easier! :)

---

### Post by chimera on 2006-01-25
That's what automatix is for after all - making things easy for new users.

---

