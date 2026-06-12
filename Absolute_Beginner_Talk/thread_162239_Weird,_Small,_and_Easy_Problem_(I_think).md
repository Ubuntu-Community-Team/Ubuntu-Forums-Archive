---
title: "Weird, Small, and Easy Problem (I think)"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-18
I have the firestarter firewall set up to be one of the startup programs.  Whenever I log out and back in, or restart, or shut down and power up, it sometimes (not always) doesn't show the password dialog to sart firestarter.  Instead it just shows my normal desktop, but with nothing clickable. 

 If i type in my password(as if i'm typing nothing)  then firestarter starts, and i am able to click everything again.  

How does this disappearance of the dialog happen, and what can i possibly do to prevent it?

---

### Post by trent dillman on 2006-04-18
You could edit /etc/sudoers:

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by user1397 on 2006-04-18
Also, when my screensaver goes on (the blank one), and if it's left on for a while, i click to get out of it, but the mouse can't move. i have to replug the mouse into the computer. ?????????

---

### Post by user1397 on 2006-04-18
[quote=trent dillman]You could edit /etc/sudoers:

[http://www.fs-security.com/docs/faq.php]("http://www.fs-security.com/docs/faq.php")[/quote]
In a terminal i typed in "sudo /etc/sudoers", typed in my password, but all i got was : "sudo: /etc/sudoers: command not found"
what's going on?

---

### Post by OffHand on 2006-04-18
check the first page, reply 1-7, of this thread:

[http://ubuntuforums.org/showthread.php?t=131487&highlight=launch+firestarter+start](http://ubuntuforums.org/showthread.php?t=131487&highlight=launch+firestarter+start)

Pay extra attention to 6. Read it before you start.

---

### Post by sxtz on 2006-04-18
AFAIK, the firewall itself starts up with the machine, you don't really need to have the GUI in your startup.. but if you want it to, make sure you're running the command  ```
gksudo firestarter
``` instead of simply ```
firestarter
```

---

### Post by user1397 on 2006-04-18
Okay my firestarter problem was fixed, thanks.
Now, how about helping me with the question on the third post of this thread?
(with all due respect-:-D)

---

### Post by sxtz on 2006-04-18
[quote=erik1397]Also, when my screensaver goes on (the blank one), and if it's left on for a while, i click to get out of it, but the mouse can't move. i have to replug the mouse into the computer. ?????????[/quote]


hrmm.. well the screen's locked.. you're using the default environment, right (GNOME)?   tried using your keyboard to unlock/type in your pw?  what happens then?

---

### Post by user1397 on 2006-04-18
[quote=sxtz]hrmm.. well the screen's locked.. you're using the default environment, right (GNOME)?   tried using your keyboard to unlock/type in your pw?  what happens then?[/quote]
I am using GNOME. I'm sorta a beginner-please explain what you mean by "pw"?

---

### Post by user1397 on 2006-04-18
Also, i made an inbound policy for samba and for everyone in firestarter.
Is this bad? should I change it to something else? and if yes, what?

---

### Post by macdo on 2006-04-18
[QUOTE=erik1397]I am using GNOME. I'm sorta a beginner-please explain what you mean by "pw"?[/QUOTE]
pw: password

---

### Post by user1397 on 2006-04-18
[quote=sxtz]hrmm.. well the screen's locked.. you're using the default environment, right (GNOME)?   tried using your keyboard to unlock/type in your pw?  what happens then?[/quote]
It doesn't lock because i don't have too type anything. my mouse just doesn't move after!

---

### Post by sxtz on 2006-04-18
[quote=erik1397]Also, i made an inbound policy for samba and for everyone in firestarter.
Is this bad? should I change it to something else? and if yes, what?[/quote]

i'm unsure exactly what you mean.. do you mean you made an inbound policy for samba for everyone, or an inbound policy for samba and an inbound policy for everyone?  

the latter would allow anyone to connect to your machine, which is what you have the firewall to prevent in the first place... are you even using samba?  personally, i don't have anything in my inbound connections list.  all you have to do to enable web access with firestarter, for example, is allow outbound connections to port 80 (for http) and 443 (for https, used by the ubuntu wiki and many others).  established connections are allowed by default, so you don't need to set up inbound anything.

---

### Post by sxtz on 2006-04-18
[quote=erik1397]
 It doesn't lock because i don't have too type anything. my mouse just doesn't move after!
[/quote]

try hitting the spacebar a couple times to see if a password prompt comes up.

---

### Post by user1397 on 2006-04-18
[quote=sxtz]i'm unsure exactly what you mean.. do you mean you made an inbound policy for samba for everyone, or an inbound policy for samba and an inbound policy for everyone?  

the latter would allow anyone to connect to your machine, which is what you have the firewall to prevent in the first place... are you even using samba?  personally, i don't have anything in my inbound connections list.  all you have to do to enable web access with firestarter, for example, is allow outbound connections to port 80 (for http) and 443 (for https, used by the ubuntu wiki and many others).  established connections are allowed by default, so you don't need to set up inbound anything.[/quote] I meant an inbound policy for samba for everyone.  My outbound policy is just "permissive by default, blacklist traffic." Does all this sound good or no?
EDIT: If I dont put the inbound policy for samba for everyone, my windows box can't open the samba share!

---

### Post by user1397 on 2006-04-18
Had you a hello? Tear? Nothing? Not even a tad? :(
(austin powers joke)

---

### Post by user1397 on 2006-04-18
Pleeeeeeeease aaaaaaaaaaanswer somebody! :twisted:

---

### Post by sxtz on 2006-04-18
[quote=erik1397]I meant an inbound policy for samba for everyone. My outbound policy is just "permissive by default, blacklist traffic." Does all this sound good or no?
EDIT: If I dont put the inbound policy for samba for everyone, my windows box can't open the samba share![/quote]

regarding your outbound policy... permissive works just fine, but i feel, personally, that it's better to only allow what you use to access the net.  seeing as firestarter doesn't do much in the way of letting you chose the *applications* that connect outward, i feel it's best to only allow a certain set of *ports*, ie http(s), irc, etc.. to connect -- by using the restrictive default and opening up ports that you need.  some would argue that this type of setting is only needed on windows boxes that are frequently infected with all sorts of nasty $h!t, and as such must be prevented from "calling home.." but i think it helps, at least a tiny bit, if your box *does* end up being compromised.

as far as the inbound policy goes, if you need to have your win box share with your *buntu box, keep that samba rule in there.  there isn't any harm in it, as far as i can see.

---

### Post by user1397 on 2006-04-18
[quote=sxtz]i feel it's best to only allow a certain set of *ports*, ie http(s), irc, etc.. to connect -- by using the restrictive default and opening up ports that you need.[/quote]
What are all of the ports that i should allow if i put restrictive by default apart from https and http? (i don't use irc)

---

### Post by sxtz on 2006-04-18
[quote=erik1397]What are all of the ports that i should allow if i put restrictive by default apart from https and http? (i don't use irc)[/quote]

ALL of em? dunno.  I'm not sure what you use.  i know you should open up 123 for NTP, so ubuntu can grab the time when it boots.  67-68 would be a good idea, if your router/cable/dsl modem uses DHCP.  the rest you can kinda play by ear.  when you're running an app that needs to connect to the internet, check the "events" tab in your firestarter GUI. if it's been blocked, it'll register an event showing which port, ip, interface, etc.. it should be pretty easy to figure out from there.

you should try irc sometime.. the ubuntu irc channel is a good place to ask questions, after (of course) you take the preemptive steps of finding out if theres a post on the forum, a page on the wiki, or a link on google. 

  server: irc.freenode.net
channel:  #ubuntu

---

### Post by user1397 on 2006-04-19
[quote=sxtz]ALL of em? dunno.  I'm not sure what you use.  i know you should open up 123 for NTP, so ubuntu can grab the time when it boots.  67-68 would be a good idea, if your router/cable/dsl modem uses DHCP.  the rest you can kinda play by ear.  when you're running an app that needs to connect to the internet, check the "events" tab in your firestarter GUI. if it's been blocked, it'll register an event showing which port, ip, interface, etc.. it should be pretty easy to figure out from there.

you should try irc sometime.. the ubuntu irc channel is a good place to ask questions, after (of course) you take the preemptive steps of finding out if theres a post on the forum, a page on the wiki, or a link on google. 

  server: irc.freenode.net
channel:  #ubuntu[/quote]
Thanks! I also get a lot of TCP and UDP protocols, what are those?

---

