---
title: "rdesktop assitance please"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Accurax on 2006-11-21
Hi uys,

thanks for the help yesterday, i managed to get ubuntu installed and working correctly .... and i think im smitten :-({|= 

Anywhoo, the main reason i acheived motivation to install ubuntu is  work orientated.

Let me elaborate, I work with a company that provides sage accounts software hosted on servers in canary wharf.

Now, they connect through terminal services.

great, no problems, on windows box's.

But i have a potential customer who has decided to use ubuntu in his offices at work (excellent choice if i maye say so).

Basically i need to get ubuntu to connect to the terminal services server in london and therefore allow him to access sage from his nix box.

A little reading around pointed me to rdesktop, which i believe is exactly the answer i am looking for.

One problem, im new to linux, my customer isnt able to help, as he only really uses ubuntu "out of the box" as it were.

I am under the impression that installing software on a linux machine, is different and soemwhat more complicated than on its windows alternative.

Ive searched for rdesktop tutorials, and found one (on these very forums in fact), but they all go straight over my head at the moment im afraid.... its a lot to take in.

Can anyone advise me on the basics of what im trying to do.... or at least help me reach the point where the tutorials make sense, im sure i can figure things out from there.

I really really appreciate any help any can give me.

Im going to go and read that tutorial again, maybe something will ignite a spark of realisation   :rolleyes:

---

### Post by Shuja on 2006-11-21
Use the windows terminal service client instead.

---

### Post by lazyart on 2006-11-21
Just go to Applications->Internet->Terminal Services Client

Enter the computer name (or ip addresss), set the protocol to RDP and optionally add the username password and domain.  Click connect and you should be able to log in to the remote machine.

I do this plenty.  The connection info can be saved and you can use that to launch in the future.

---

### Post by Accurax on 2006-11-21
ok ive just tried it over my local network.

I put the ip of my windows machine in, and hit connect.. with RDP selected... but it gives me an error... any clues?

---

### Post by lazyart on 2006-11-21
What error did you get?

Is the Windows machine set to allow RDP connections? Control Panel->System->Remote->Allow users to connect remotely to this machine.

---

### Post by aspNetCarlos on 2007-01-15
Hi am also new to Ubuntu,  i also have a remote desktop problem. I use rdesktop 1.5 to connect to my windows xp pro machine then i connect to my job through cisco vpn and run remote desktop from my xp machine to connect to my work machine. But i constantly get disconnected and i get   this message
"ERROR: recv: Connection reset by peer"

---

### Post by stealthwave on 2007-03-12
Thanks for your in-put. I am brand new to linux ( Ubuntu ) like it alot. I got everything working thanks to the forums.

I only have 1 more program to see if i can it running on ubuntu is quickbooks pro 2006 and if i can get that to run bye bye microsoft.

The only question i have about rdesktop how do you get out of it when you open it in full screen?

---

### Post by p2im0 on 2007-08-03
Would have been nice to have an answer to this post.  Currently RDP'd into a windows box in fullscreen and I have no idea how to get out....
dammit.



Woohoo, just figured it out:  Ctrl-alt-enter goes in and out of Fullscreen for RDP on Ubuntu for future reference!!

-P2

---

