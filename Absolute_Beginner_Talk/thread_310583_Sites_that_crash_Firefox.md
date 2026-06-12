---
title: "Sites that crash Firefox"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by ddbann on 2006-12-01
Hi
I am new to Linux/Unbuntu. Certain sites like [http://www.twit.tv](http://www.twit.tv) or 
[http://www.nickjr.com](http://www.nickjr.com) crash my Firefox browser as soon as they start to load up. What will fix this?

---

### Post by Pjotr123 on 2006-12-01
I suppose you use version 6.10 (Edgy Eft) with Firefox 2 and Adobe flash player plugin?

I had the same problem as you. Flash content crashed FF straight away.

Therefore I switched back to using the very stable Long Term Support version of Ubuntu, 6.06 (Dapper Drake). Problem solved.

Greeting, Pjotr.

---

### Post by LLRNR on 2006-12-01
Hi there !

I tried both of the websites you pointed out, none of them crashed my FF. Could you please tell us what kind of Ubuntu you run and which version of Firefox you have ? Also, did you install the Flash & other plugins ?

LLRNR

---

### Post by sonnywise on 2006-12-02
I have the same problem but I don't want to switch back to 6.06 'cause 6.10 has a lot of improvements.

Anyone who solved this plugin problem ?

---

### Post by speedman on 2006-12-02
Are people completely incapable of using the search feature in the forums?  There are several solutions that are easily found if you take a few minutes to search on "edgy firefox" right here on ubuntuforums (without the double quotes).

The most effective solution is to change your the DefaultDepth to 24 in /etc/X11/xorg.conf.


Regards,

SM

--
The sum total of a person's knowledge does not indicate how intelligent they are for nobody knows everything.  The ability to find the answers to one's questions is a true sign of intelligence.

---

### Post by Aranel on 2006-12-02
The simplest solution is to follow the instructions in [this thread](http://www.ubuntuforums.org/showthread.php?t=286069). I edited the /etc/firefox/firefoxrc file as shown there, and it worked for me.

---

### Post by Lord Illidan on 2006-12-02
No crashes here.

---

### Post by deadgobby on 2006-12-02
I use Eft and went to the links provided and no crashes. It could be the flash player. You can go to Mozzila and one click install Flash Blocker
[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)
 See after you install and restart FF and see if the sites still crash. You'll see a flash player F symbol where the Flash Player has been blocked. You just click on the F symbol to activate the flash player. 
I did have this problem when running Dapper and flash blocker helped out.
Gobby

---

