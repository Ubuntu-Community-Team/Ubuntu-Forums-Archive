---
title: "Synergy Delay to Server from the Client"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by CaptainHowdy000 on 2008-04-17
[SIZE="2"]Howdy Everyone.
Now before I start I am going to admit that I am new to Linux but am enjoying the experience.
I decided to post my problem here because the forums are much more active here than at sourceforge.

I think I have a small problem that may or may not be related to synergy.
I have gotten it installed and it is running fine to move my mouse between my two systems.
The windows Xp box that I am using is the Server and Ubuntu is the Client.

I know that it is dead simple to run and setup on either system because it is working fine except for one issue.
The client box has an extremely large amount of lag with both the mouse and keyboard response when I am trying to use it.
Both systems are hooked up and hardwired directly into my router which is 100Mbs.

I am complete unsure of what exactly is happening with the system.
If I am typing into the keyboard on the client machine it will just freeze and then put in all of the keypresses extremely quickly.

I have already tried to open up the default port on my router for both computers in case that was the issue but I still have the same problem.
My xp machine does not have any sort of software blocking on it personally.

I am really looking forward to getting rid of that extra mouse and keyboard up on my desk.
Any help that you can give would be great.

Captain

EDIT: So I decided to try a few other things to make sure that it was not a networking issue with the router or port numbers.
I installed FireStarter to make sure that the ports are open and see what activity was going on.
I set it to allow all connections from the XP machine.
I also tried to run wireshark to see what ports it said are being used for the connection.
I opened up Ports 24800 Which is the default for Synergy.
I also saw activity on ports 37430 in ubuntu and saw activity on port 38844 in wireshark.
I opened all of the ports on my router as well and am still having the same issue.
When I ping to or from either machine the Delay is <1ms.
Just wanted to put out my quick update for what I have been trying.

EDIT 2: I just tried to set it up with the server side using my Ubuntu box and my XP box as the client and everything works fine now.
Guess I just have a little rewiring to do now is all.[/SIZE]

---

