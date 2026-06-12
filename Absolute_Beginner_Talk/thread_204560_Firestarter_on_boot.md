---
title: "Firestarter on boot"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by mo_roodi on 2006-06-27
Ok this is going to be a very newbie question, but how can I start Firestarter on boot? In Windows (I think that shows how much of a newb I am!) there's like a start-up group in the Start menu... Is there something similar in Ubuntu? I've been searching for a while but I can't seem to find anything!

Also I know Firestarter requires super-user privileges... is there any way to stop it asking me for a password (I want this ONLY for firestarter... all other apps should ask for the password.

Thanks in advance,

Mo

---

### Post by frodon on 2006-06-27
Firestarter is always running on boot, if you want to check that run this command in a terminal : ```
sudo /etc/init.d/firestarter status
```
The GUI is useful only if you want to modify some rules or disable the firewall, you don't need to have the GUI opened to have your firewall running.

---

### Post by 23meg on 2006-06-27
> In Windows (I think that shows how much of a newb I am!) there's like a start-up group in the Start menu... Is there something similar in Ubuntu?System / Preferences / Sessions / Startup Programs
> 
Also I know Firestarter requires super-user privileges... is there any way to stop it asking me for a password (I want this ONLY for firestarter... all other apps should ask for the password.
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Disclaimer: Bad practice, not recommended.

---

### Post by mo_roodi on 2006-06-27
Thanks for the replies guys

[QUOTE=frodon]Firestarter is always running on boot, if you want to check that run this command in a terminal : ```
sudo /etc/init.d/firestarter status
```
The GUI is useful only if you want to modify some rules or disable the firewall, you don't need to have the GUI opened to have your firewall running.[/QUOTE]

Frodon, just another quick question... If I do it this way and start the gui through Gnome (say if I didn want to modify a rule) would it initiate another instance of firestarter (i.e. would I have 2 instances of firestarter running) or would the GUI be for the the instance of firestarter already running (if that makes any sense...)

Many thanks,

Mo (the newb)

{Edit} Sorry mis-read your post! All is working well now... I'm happy... Thanks for all the info guys.

---

### Post by frodon on 2006-06-27
Well let me explain you how all that works in a simple way.

Ubuntu like all 2.4 and 2.6 linux kernel series has a build-in firewall called netfilter which is so damn powerful. The common language used to configure netfilter is iptables and firestarter is a frontend for iptables.
Firestarter convert what you click in an iptables script therefore several instance of firestarter don't have any sense on the firewall level.
In all the cases your iptables script is running and the GUI allow you to modify it. So configure the rules once and don't bother again with firestarter because the iptables script will be auto-launched on boot.

I saw your edit but i tought it would interest you to learn more.

---

### Post by mo_roodi on 2006-06-27
Thank you Frodon, I'm an IT graduate so computer's really do interest me, but I work alot of the time and wish I had more time to learn about Linux (university only uses Windows which is a little limited in my opinion). It's really is a pleasure to know the if I have any problems there are alot of helpful individuals on the ubuntu forums that are willing to help. I knew bits about iptables, but didn't know that Firestarter was a front end.

I love the fact that ubuntu is so easy to use, and yet out of box it is well configured and simply lets you get on with it! No mess, no fuss... 

Once again I thank you for all your assistance. 

Mo

---

### Post by dolby on 2006-06-27
reading the forums for a while read many times thats possible to set the iptables policy via firestarter and then even though not running firestarter every time at startup,the policy activates. tried doing that many times but everytime i close firestarter everything changes in iptables. if i  *sudo iptables -L* theres nothing at all. just the defaults when i installed ubuntu
anyone know how to do that?

---

