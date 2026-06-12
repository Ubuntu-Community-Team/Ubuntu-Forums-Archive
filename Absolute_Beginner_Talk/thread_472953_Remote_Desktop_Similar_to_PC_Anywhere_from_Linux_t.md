---
title: "Remote Desktop Similar to PC Anywhere from Linux to Window and Vice Versa"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-13
I want to know what experienced folks are doing these days to remote control their desktops. I saw that VNC has been used and then i saw some posts about a program called ssh.

I have Ubuntu 7.04 running on my home PC and Windows XP pro in my laptop and at my office and I like to be able to remote my desk tops from either location.  Transferring of files would be cool too.   

[LIST=1]
[*]Windows XP Pro to Ubuntu 7.04
[*]Ubuntu 7.04  to WindowsXP Pro
[/LIST]

Any help will be appreciated.


Thanks in advancce,


VC

---

### Post by Songwind on 2007-06-13
VNC has both windows and linux versions.

Also, there are RDP clients for Linux and you can do remote X sessions with Cygwin from Windows.

---

### Post by lazyart on 2007-06-13
Ubuntu -> Windows:  Remote Desktop or VNC
Windows -> Ubuntu: VNC

ssh makes it a secure connection, because neither protocol is particularly secure.

Will your office machine even be able to connect back home?  You might have ports blocked by your friendly IT team (if you are your own boss then that's probably moot).  You'll also need a way to see your machine across the wild, wild internet... which requires a static IP or an account for dynamic dns provider (I use dyndns.org but there are others).  Then you need a hole in your router so that traffic can get through (port forwarding).

Another option is a service called Hamachi.  If you have the freedom to install such a thing, it can put your office machine on a virtual network with your home box, eliminating the static IP/ddyns provider and the ssh bit.

How much freedom do you have on your office machine?

---

### Post by videocheez on 2007-06-13
Do the remote x sessions involve using the terminal interface?  Could I use synaptic to install VNC in Ubuntu or will I need to use terminal?  I'm a super noob and those command line installs make me a little nervous 'cause I don't exactly know whats going on.

---

### Post by videocheez on 2007-06-13
> **lazyart said:**
> Ubuntu -> Windows:  Remote Desktop or VNC
Windows -> Ubuntu: VNC

ssh makes it a secure connection, because neither protocol is particularly secure.

Will your office machine even be able to connect back home?  You might have ports blocked by your friendly IT team (if you are your own boss then that's probably moot).  You'll also need a way to see your machine across the wild, wild internet... which requires a static IP or an account for dynamic dns provider (I use dyndns.org but there are others).  Then you need a hole in your router so that traffic can get through (port forwarding).

Another option is a service called Hamachi.  If you have the freedom to install such a thing, it can put your office machine on a virtual network with your home box, eliminating the static IP/ddyns provider and the ssh bit.

How much freedom do you have on your office machine?

Thanks for the specific info.  I currently use Radmin and No-IP to talk Windows to Windows and I was smart enough to become buds with the IT guy years ago. ;) .  I tried dyndns because my Linksys RV082 router software has  link to use that service but my Comcast IP address changes maybe once every 9 months so dyndns dumped me due to lack of activity.
I read about Himachi in maximum PC in last month's issue and I think and it looks pretty cool. Will that really work with Ubuntu?  How is ssh implemented?

---

### Post by videocheez on 2007-06-13
I downloaded the linux version of hamachi.  How do I install it?

---

### Post by Bd0g on 2007-06-17
You could use Radmins viewer 3.0 with wine 0.9.39 now... for a good connection to your office.

Have been using it for the last few days with good results.

---

### Post by ahujascrypt on 2008-05-29
Hey could you please send me a link to download Radmin 3.0. Their site only seems to have 3.2 which doesnt work with wine. I can be reached at [email]ahuja.sumit@gmail.com[/email]

Thanks

---

### Post by videocheez on 2008-05-29
> **ahujascrypt said:**
> Hey could you please send me a link to download Radmin 3.0. Their site only seems to have 3.2 which doesnt work with wine. I can be reached at [email]ahuja.sumit@gmail.com[/email]

Thanks
 
Sorry. I don't have a link to this program but I'm sure if you search the web you can find it.  I don't use radmin anymore, instead I use tight vnc. It works like a charm.

---

