---
title: "associate firestarter with a program ?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-11-15
Hi

I just configured the firestarter 'Outbound traffic policy' to 'restrictive by default'.  Now that means I have to specify which ports I want firestarter to open by adding a new rule.
However, programs like 'sopcast' recommend opening a range of ports e.g. 3900-13900 for it to work. This would mean that I make a new rule to open this range of ports, making my system insecure even when I am not using the program. 

Instead,[COLOR="Red"]** can I specify or associate a particular program with firestarter, so that it only allows that program to access whichever ports it wants to access, and then close them when the program is not in use ?**[/COLOR] 
I remember doing this with 'Zonealarm' in windows, but can't figure out with firestarter.

:)

---

### Post by wieman01 on 2007-11-15
That's not possible, you'll have to open these ports.

However, this does by no means mean that your system will be insecure. As long as there are no services using these ports, your system is secure. So opening these ports will entail no further risks unless you start running programs & processes that happen to use them (such as Sopcast).

---

### Post by genbuntu on 2007-11-15
Oh, so that means these ports will only be opened whenever a program (such as sopcast) tires to access these .. hmm.... 
What if a 'malicious' program tries to access these ports ?
But I guess it is still safer than making the outbound traffic policy _permissive_ by default ?

-------------
Its sad to hear that this cannot be achieved in firestarter because it is such a good and useful feature. Would any other firewall be able to do so, like guarddog etc.?

---

### Post by wieman01 on 2007-11-15
Simply close inbound and open outbound traffic.

These ports will be open for outbound traffic, however, an intruder won't be able to compromise your system as long as there is not faulty service running on them. So again, you are safe.

Yes, make outbound traffice restrictive by default, this way you can control your system and you know what's going on.

---

### Post by hyper_ch on 2007-11-15
You could, of course, write a shell script which first set "opening" rules in iptables, then start the application and when the application is closed set the "closing" rules in iptables...

---

### Post by wieman01 on 2007-11-15
> **hyper_ch said:**
> You could, of course, write a shell script which first set "opening" rules in iptables, then start the application and when the application is closed set the "closing" rules in iptables...
Which is tougher for a beginner than it sounds. 

Do you have an example? Would be interesting...

---

### Post by genbuntu on 2007-11-15
oh, that sounds interesting (linux has a solution for everything.. haha ;) ).
Yes, although I'm still a beginner but keen to learn linux, so might try that if I were able to.

Wieman: thanks for your clarifications. 

------------------
I'm off for now, but you may leave any further comments or advices . :)

---

### Post by hyper_ch on 2007-11-15
Nope, iptables is above my skills (never really bothered to get into it)... however in my "howto xfce wallpaper change) script there's a code snipped provided by someone else that checks if certain programs are running. Maybe taht could be used to determine whether the "closing" command should be issued or not.

---

