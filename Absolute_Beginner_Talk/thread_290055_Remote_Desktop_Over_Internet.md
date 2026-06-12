---
title: "Remote Desktop Over Internet?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2006-10-31
My dad needs to reformat his computer (darned Windows), and after seeing my laptop with Compiz, he wants to give Ubuntu a shot. However, he's a very "average" computer user, and just wants things to work without much effort.

I'm going to go and set up Ubuntu and get everything running, so most problems will be fixed (if any) from the beginning (as far as hardware drivers and such).

However, I'm worried about simple little things, ie most terminal operations. I know it won't be hard to fix most of the problems, but I don't want to have to drive 30 minutes to his house to fix something simple.

Is there an easy method of allowing me remote (secure) access to his desktop? I see System -> Preferences -> Remote Desktop, but it (and most posts I could find in the forum) seem to deal with local networks instead of connections over the Internet.

I haven't ever messed with remote access to desktops before, so be easy on me. :) Is there an easy way to get this established?

---

### Post by tronica on 2006-10-31
basically you would set up a vnc server on your dads computer, and if hes behind a router, you forward port 5900 i think it is, to his computer. I will see if i can find any guides, to help you. i havn't done this in years.

---

### Post by Jussi Kukkonen on 2006-10-31
I advice against opening a Remote Desktop for the whole internet... install ssh server on the machine, set it up with only key-based logins and you'll be fine. It'll be pretty much the most secure remote access you could set up, and you'll still be able to run desktop apps remotely if there's a real need (ssh allows X forwarding).

The only difficult thing there is setting up the public key stuff (well, it's only difficult if you haven't done it before) -- try the ssh solution out with normal password login first, but do aim for key-based-logins only. That way you won't have to worry about script kiddies running brute force password attacks on the machine.

EDIT: by the way, if he has a dynamic IP you'll have to either ask him what it is everytime before connecting or set up a dynamic dns service...

---

### Post by bmillsap on 2006-10-31
If you enable remote desktop on his machine, you should be able to use a VNC client on your machine to access his desktop.  If he's behind a router, you would need to forward the appropriate port (default is 5900) to his machine.

You can change the port from the default and use a password to establish some security, but it won't be encrypted or anything (I think), I don't know how much security you're looking for.

I'm running 6.06, but there are posts here of people having issues on 6.10 with not being able to have this work correctly when the remote desktop is password protected, you might want to look at those if you're going to install 6.10

---

### Post by wpwood3 on 2006-10-31
> **bmillsap said:**
> 
I'm running 6.06, but there are posts here of people having issues on 6.10 with not being able to have this work correctly when the remote desktop is password protected, you might want to look at those if you're going to install 6.10There is a bug in the Edgy version of VNC (Vino) that causes it to forget your password each time you reboot or X is restarted.
Go with Dapper and you'll be ok.

---

### Post by David Corrales on 2006-10-31
> **wpwood3 said:**
> There is a bug in the Edgy version of VNC (Vino) that causes it to forget your password each time you reboot or X is restarted.
Go with Dapper and you'll be ok.

No wonder I was having trouble with this :evil:

---

### Post by brentoboy on 2006-10-31
> **Jussi Kukkonen said:**
> by the way, if he has a dynamic IP you'll have to either ask him what it is everytime before connecting or set up a dynamic dns service...

or, you could check out [http://no-ip.info](http://no-ip.info)

they let you define a name such as:

my-dads-ubuntu-pc.no-ip.info

and you can install a little app on your dad's PC that will tell the no-ip.info server where to find his PC.

once you set this up, any internet based DNS server will be able to tell you the IP address of the host named: my-dads-ubuntu-pc.no-ip.info

and you can use that hostname directly in VNC.

---

### Post by jpkotta on 2006-10-31
There is also hamachi.  I've had better luck with this, because I can't get port forwarding to work with my gateway.  It works great with ssh or anything else.  You don't have to tunnel VNC through ssh to encrypt it either, because the VPN is already encrypted.

[http://www.hamachi.cc/](http://www.hamachi.cc/)

---

### Post by Jussi Kukkonen on 2006-11-01
> **brentoboy said:**
> [QUOTE=me]by the way, if he has a dynamic IP you'll have to either ask him what it is everytime before connecting or set up a dynamic dns service...

or, you could check out [http://no-ip.info](http://no-ip.info)[/QUOTE]

brentoboy, that is dynamic dns ( see the logo: *"No-IP.com - The dynamic DNS leader"*)...

---

### Post by the_priest on 2006-11-01
> **Jussi Kukkonen said:**
> I advice against opening a Remote Desktop for the whole internet... install ssh server on the machine, set it up with only key-based logins and you'll be fine. It'll be pretty much the most secure remote access you could set up, and you'll still be able to run desktop apps remotely if there's a real need (ssh allows X forwarding).

Then what program would you use on the local XP or ubuntu machine to view and control the desktop on the remote Ubuntu machine?

---

### Post by Jussi Kukkonen on 2006-11-01
> **the_priest said:**
> Then what program would you use on the local XP or ubuntu machine to view and control the desktop on the remote Ubuntu machine?
He mentioned "mostly terminal applications" so I figured seeing the Desktop wouldn't be that important for him and he also mentioned having Compiz on his machine so I assumed he's running Ubuntu locally... 

To answer your question:
* On a local ubuntu machine I'd just run ssh with X forwarding and start the apps from command line, e.g. *"sudo synaptic"* works fine. 
* If the local machine was Windows, I'd have to install an X server (like Cygwin/X) before I could do that .

Running X over ssh is slow, so this is not very usable for everyday use. From the problem description I thought it wouldn't matter.

---

### Post by bluenova on 2006-11-01
> **the_priest said:**
> Then what program would you use on the local XP or ubuntu machine to view and control the desktop on the remote Ubuntu machine?
VNC over SSH if you really need to see the whole desktop, otherwise just SSH X forwarding as above.

---

### Post by Xappe on 2006-11-01
I would install a freenx server on your dad's machine. It's the fastest remote desktop solution i've tested so far. You can't see your father's desktop as he sees it (you can't connect to local sessions), but you can login and get your own desktop on his computer.

---

### Post by bodhi.zazen on 2006-11-01
I like ssh and putty:

See here:

[ HOWTO control your home PC from your office (terminal, putty, ddclient & sshd)](http://ubuntuforums.org/showthread.php?t=256102)

And here:

[Access your Linux computer graphically and securely using SSH and VNC](http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/)
_Note_: I like ultraVNC.

And here:
[Basic SSH server configuration how-to](http://www.linuxforum.com/linux_tutorials/16/1.php)

---

### Post by tonyr1988 on 2006-11-03
I installed FreeNX and tested it out. It works fine, and it (+ SSH) is fine for what I'm needing to do.

However, I'm curious: When under FreeNX, I can do everything on my computer as if I'm on the host computer. But, it doesn't reflect it on my host's monitor (ex: when I move the mouse, click menus, or open programs, my host just sits there).

I didn't mess too much with VNC, but will it be able to do that?

Like I said, not completely essential, just curious.

Thanks for all your help!

---

### Post by DSn0wMan on 2006-11-03
I don't want to confuse the issue any, but vnc is lame.

It's best to use NX server and client.

[http://www.nomachine.com/](http://www.nomachine.com/)

NX uses ssh, and is pretty easy to install. It's also far faster than VNC.

---

### Post by lazyart on 2006-11-03
VNC does show output on both machines.  It's not terribly fast, but if you just need to configure a couple things or show him how to do something it's good enough.

---

