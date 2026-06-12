---
title: "how to telnet with X forwarding?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by hoydooley on 2007-05-17
Hi,
I want to connect a school server on a solaris.
I used telnet to it. I can connect to it, but without X forwarding.
I tried ssh -X but the solaris host doesn't support ssh connection, so I have to use telnet.
Is there any way to connect it using telnet with X forwarding?

---

### Post by Cypher on 2007-05-17
Telnet doesn't support X-forwarding, sorry.. Only SSH does.

---

### Post by Psicolonia on 2007-05-17
i'm not sure what you mean by forwarding but you can do "export DISPLAY = yourmachineip:0.0" and try to run the apps...

---

### Post by Psicolonia on 2007-05-17
inside the telnet connection i mean. :)

---

### Post by hoydooley on 2007-05-17
Thank you for your replies but export DISPLAY myip:0 in telnet doesn't make it work.

I found out that other students who use windows xp uses rexec with a Xserver emulation program to connect to the school server with X forwarding. (I heard that X forwarding is something that enables me to remotely run X applications on my computer)

I tried to run rexec in terminal in feisty, but it saids "command not found"

Any suggestions?

---

### Post by hartz on 2007-05-18
You need an X-emulation program (more correctly called an X-server) on your local PC/workstation regardless of whether you use ssh with X-forwarding, or a direct connection (by setting the DISPLAY variable).

Both of these methods allow you to "see" the display on your local PC of an X-windows application running on a Linux or Unix system elsewhere.  That is why they say "display remotely".

In the instance where you use ssh with X-forwarding, the way the application connects back to your X-emulator on your PC is that it "tunnels" the data for the X-window session over the encrypted SSH session.  This is secure and allows the X-windows client to automatically connect back to you without having to do funny trickery on firewalls to allow the connection.

In the instance where you set the DISPLAY variable to point back to your workstation, the X-windows application's connection is independent of the ssh, telnet or rexec connection used to login in to the "remote" Linux/Solaris host.  However, the connection to display the X application window is a new TCP/IP session established backwards from the Solaris/Linux host back into your PC.  This requires jigery with firewalls if your PC and the Linux/Solaris systems are not on the same network.

Note:  Technically the ssh with X-forwarding should be called X-tunneling.  ssh X-forwarding allows you to hop form host-to-host, potentially spanning networks.  It allows you to get an X-window application to forward its display VIA a "forwarding host" to another machine.  However most people just call it x-forwarding when you specify the "-X" (or more modern "-Y") parameter to the ssh command.

Also Note:  When you use SSH to do this type of X-windows session tunneling, it DOES in fact set the DISPLAY variable, though it is set to point the display to a virtual X-server on the remote host, and the virtual X-serverthen captures, encapsulates, and tunnels the X-windows protocol data back to your PC. 

If your PC is running Linux, you do not need any extra software, such as an X-windows emulator, because  Linux already does X-windows natively (using Xorg as the x server application), and does so much much better than any emulator I've ever seen.

---

### Post by steve.horsley on 2007-05-18
I hope that explanation by hartz3 helped. 

I dont know about rexec - how that works. Assuming there are not firewalls between you and the Solaris box, you can do it with telnet from Ubuntu. Before you make the telnet call, use this command locally:
**xhost +**
which allows incoming connections to your X display. Then telnet to the Solaris box. Then on the solaris box, issue this command:
**export DISPLAY=yourip:0.0**
The only space whould be between export and DISPLAY. yourip dhould be your PC address, not the Solaris IP address.

---

### Post by heimo on 2007-05-18
About xhost +, from man xhost:
> 
       +       Access is granted to everyone, even if they aren’t on the  list
               (i.e., access control is turned off).


I don't think that's something I'd do. Sounds insecure.

---

### Post by steve.horsley on 2007-05-18
True. It means that any other PC on your network could create a window on your screen. 
But if you can read the man file, you can see that 
**xhost +sloarisipaddress**
will allow that box only to open windows on your screen.
Being a lazy so-and-so, I have never bothered to give the specific address.

---

### Post by hoydooley on 2007-05-19
Thanks a million for all your replies.
I don't think my computer is behind firewall because I could run X applications under windows xp on this same computer. I followed the explanations of steve.horsley but still cannot run X applications.
```
forrest@forrest:~$ xhost + solarisip
solarisip being added to access control list
forrest@forrest:~$ telnet solarisip
Trying solarisip...
Connected to solarisip.
Escape character is '^]'.


SunOS 5.8

login: A20
Password: 
Last login: Sat May 19 05:28:55 from myip
[A20@lab A20]$ export DISPLAY=myip:0.0
[A20@lab A20]$ xclock
Error: Can't open display: myip:0.0
[A20@lab A20]$ icfb   
*ERROR* X Window Display Initialization failure
*WARNING* X Window Display Initialization failure

```
plz help~~

---

### Post by cacycleworks on 2007-05-19
> **hoydooley said:**
> 
[A20@lab A20]$ xclock
Error: Can't open display: myip:0.0
[A20@lab A20]$ icfb   
*ERROR* X Window Display Initialization failure
*WARNING* X Window Display Initialization failure
[/code]
plz help~~

have you tried this:
$ xclock &

The & launches the process in the background (which probably means if it didn't work then, it wouldn't now??)  Anyhow, if you don't background the process, you can't type in that terminal anymore.

googling on *remote connections in x* found me this:
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)

Good place to start... I'll be working on this, too, soonish, as we transition away from windblows as much as possible. I had a KILLER .xinitrc when in college...

:)

---

### Post by lazyart on 2007-05-19
I hope you typing in your ip address in substitute for "myip"


Check my sig about setting up a secure remote X session....

---

### Post by hartz on 2007-05-19
> **hoydooley said:**
> Thanks a million for all your replies.
I don't think my computer is behind firewall because I could run X applications under windows xp on this same computer. I followed the explanations of steve.horsley but still cannot run X applications.
```
forrest@forrest:~$ xhost + solarisip
solarisip being added to access control list
forrest@forrest:~$ telnet solarisip
Trying solarisip...
Connected to solarisip.
Escape character is '^]'.


SunOS 5.8

login: A20
Password: 
Last login: Sat May 19 05:28:55 from myip
[A20@lab A20]$ export DISPLAY=myip:0.0
[A20@lab A20]$ xclock
Error: Can't open display: myip:0.0
[A20@lab A20]$ icfb   
*ERROR* X Window Display Initialization failure
*WARNING* X Window Display Initialization failure

```
plz help~~

You need to substitute your local workstation IP address where it says "myip"

When using Ubuntu, there is an extra step required before it will accept display requests, besides the xhost ipofsolarisbox command.

[LIST=1]
[*]On the menu, select System -> Administration -> Login Window
[*]Select the "Security" Tab
[*]Make sure the "Deny TCP connections on Xserver" option is UNCHECKED
[/LIST]

---

### Post by steve.horsley on 2007-05-19
Nice one, hartz3. It's a long time since I used telnet and X. I wasn't aware of that little security feature.

---

### Post by hoydooley on 2007-05-21
I unchecked the System>Administration>Login Window>'Deny TCP Connections to Xserver' checkbox.
and the following method solved the problem.
```
$ xhost + schoolserverid
$ telnet schoolserverid

Login: myid
Password: ******

Welcome!

$ setenv DISPLAY myip:0.0
$ xclock
```

And "setenv DISPLAY " part needed be replaced to "export DISPLAY=" in some other shell.

Thank you very much for all of you.

---

### Post by heimo on 2007-05-21
Please see posts #8 and #9 in this thread about how to use xhost more securely.

---

### Post by hoydooley on 2007-05-21
> **heimo said:**
> Please see posts #8 and #9 in this thread about how to use xhost more securely.

Oops. I forgot that. 
```
 $ xhost + 
``` should be changed to ```
 $ host + schoolserverip 
```
Thanks for the advice. I've changed my reply thread now reflecting your advice.

---

### Post by jonwh25 on 2008-06-16
> **hartz said:**
> You need to substitute your local workstation IP address where it says "myip"

When using Ubuntu, there is an extra step required before it will accept display requests, besides the xhost ipofsolarisbox command.

[LIST=1]
[*]On the menu, select System -> Administration -> Login Window
[*]Select the "Security" Tab
[*]Make sure the "Deny TCP connections on Xserver" option is UNCHECKED
[/LIST]

How is this done under 8.04? I don't see a Login Window option under System -> Administration.

Nevermind... have to be the sudo user.. :) figured it out.

Thanks

---

