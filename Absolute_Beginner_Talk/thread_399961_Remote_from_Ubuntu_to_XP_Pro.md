---
title: "Remote from Ubuntu to XP Pro"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by quickwitt on 2007-04-02
I am trying to use Terminal Server Client to connect from Edgy Ubuntu to an XP Pro desktop over a private LAN. Remote connections are enabled on the XP machine. Each time I try to connect I receive the error "No Route to Host". I have tried RDP and RDPv5. Any help would be greatly appreciated.

Thanks!

---

### Post by oracle5 on 2007-04-02
When I have to connect to a windows machine I install real vnc server on the windows machine. I then use krdc on the linux side to connect. 

oracle5

---

### Post by Marsolin on 2007-04-03
Have you tried pinging the IP address of the Windows system to make sure that network traffic is getting though?  The other items to confirm are that Remote Desktop is enabled on the Windows system and its firewall isn't blocking the connection.

---

### Post by quickwitt on 2007-04-03
I can ping the machine with no packet loss. Remote connections are enabled on the machine also. I regularly connect Windows to Windows with the same two computers.

Thanks.

---

### Post by Sentinel83 on 2007-04-03
quickwitt,

Can you disable the xp firewall and try again?  The RDP connection should go over port 3389 for both windows and non windows, but disabling the firewall will make sure that the Ubuntu version is trying on the port it uses by default and is not getting blocked.

Also, I don't want to oversimplifiy, but make sure that the remote desktop option is checked (not remote assistance, as I am sure you have done) and you can use the Firewall link in the Remote desktop section of the window to configure it or view help files on the Windows firewall.

---

### Post by quickwitt on 2007-04-03
Good suggestions.

The Windows firewall is disabled and there is no other software firewall in place. 

Remote connections are enabled on the target machine.

Thanks!
Q

---

### Post by Wicca on 2007-04-04
*No route to Host*
Looks like something else is going on, not particularly bound to RDP.

In Terminal Server Client, have you tried connecting to the IP address of the host instead of the name?

---

### Post by quickwitt on 2007-04-04
That worked! Connected wirelessly over the LAN with 24-bit color and very little lag.

Now if I can solve one minor audio problem...

Bye, bye Windoze!


Thanks alot.

:guitar:

---

### Post by Wicca on 2007-04-04
Just as I thought.
Your Ubuntubox can't resolve the hostname of the Windowsbox, and therefore: "can't find route to host".
Although this can be annoying, in a small LAN there is always the possibility to connect at IP level so this is not a really big problem.

Glad for you you got it working.

---

### Post by Marsolin on 2007-04-04
Good call, Wicca.  I have to do the same thing on my systems, I'm just so used to it now that I completely forgot it's not the usual Windows way.

---

