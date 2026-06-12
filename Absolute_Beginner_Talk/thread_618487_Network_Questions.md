---
title: "Network Questions??"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2007-11-20
Hi People!!!

At the moment i live in denmark in a hostel with wired network, in that network i assume that there are a lot of windows pcs (600 people live there) a few macs and a few x-boxes. So i would like to know:

1) What address should other people use to see my shared files? and where can i find it to tell them?

2) Is there any program that i have to install before other people can see my computer and witch one?

3) Where do i have to go or what do i have to do in ubuntu to see other peoples computers?

---

### Post by Inxsible on 2007-11-20
1) You can create a windows share using Samba

2) You can use VNC to login to other people's machines

3) You can set up your machine as the vnc server for others to login to your machine

4) You can also use RDP to do it.

5) or NXServer


if you go with RDP, you will not have to install anything. VNC and NXServer does need other apps and a bit of configuring. Samba is different from the other three, where others have to login to you machine, and samba actually just provides a link to 1 or more of your folders, that you have shared.

---

### Post by G. Cotgreave on 2007-11-20
ok i can say that i understand what you're saying but i don't know how to do all that stuff u told me :(:(:( can you help me a bit more with every question if possible? Sorry but i am a complete noobie:(:(:(

---

### Post by Inxsible on 2007-11-20
How Tos : 

[FreeNX]("http://ubuntuforums.org/showthread.php?t=1968&highlight=Freenx")

[Resumable VNC]("http://ubuntuforums.org/showthread.php?t=488207&highlight=Freenx")

[Remote Desktop RDP]("http://ubuntuforums.org/showthread.php?t=342574&highlight=Freenx")

[NXServer]("http://ubuntuforums.org/showthread.php?t=441496&highlight=Freenx")

NXServer and FreeNX are similar, just that FreeNX is the open source version.

Hope that helps

---

### Post by G. Cotgreave on 2007-11-20
Thank you very very much!!!!! This community is wonderfull!!!! I never regret that i switched to ubuntu!!!!

---

### Post by Inxsible on 2007-11-20
> **G. Cotgreave said:**
> Thank you very very much!!!!! This community is wonderfull!!!! I never regret that i switched to ubuntu!!!!Try to follow the how to which uses RDP over SSH or VNC over SSH. That way your connections are more secure. NXServer and FreeNX how-tos do use SSH.

---

### Post by HermanAB on 2007-11-20
You may find that for starters, the easiest way to exchange files is with FTP.  You can get the Filezilla FTP server and client for both Linux and Windows from Sourceforge.  FTP is relatively simple, easy to set up and secure and it is cross platform and well known.

Standard Windows networking uses the Server Message Block (SMB) protocol.  It is very chatty, slow, insecure and difficult to set up.

SSH is a secure shell and a secure transport using the Secure Sockets Layer.  It is the easiest way to set up encrypted tunnels between machines.  It is native to Unix and can be installed on Windows using Cygwin.

Do not confuse security with privacy.  SSH is secure and private, since it uses strong encryption. FTP can be secure, but it is not private, since transfers are in plain text.  FTP can be tunneled over SSH (SFTP) making it both secure and private.  SMB is insecure no matter how you install it and it is also not private, so it is the worst option by far.  SMB can also be tunneled over SSH, but then it is not compatible with Windows machines anymore, unless you jump through a lot of hoops.

If you want to see how vulnerable your dorm network is, install tcpdump and do this:
$ sudo tcpdump -A -s 256 -i eth0

or this:
$ sudo tcpdump -A -s 256 -i eth0 | grep user
$ sudo tcpdump -A -s 256 -i eth0 | grep pass 
then click your email client send/receive button.

The above should quickly convince anyone that using SSH is probably a good idea...

'Hope that helps!

Herman

---

### Post by G. Cotgreave on 2007-11-20
ok i can say that i am a bit confused!! So here's my problem: my computer is part of a network in a hostel as i said before therefor i cannot ask from people to install stuff on their computers in order to see mine i need a ''clean'' solution that requires settings and installations only on my computer.

---

### Post by Inxsible on 2007-11-20
> **G. Cotgreave said:**
> ok i can say that i am a bit confused!! So here's my problem: my computer is part of a network in a hostel as i said before therefor i cannot ask from people to install stuff on their computers in order to see mine i need a ''clean'' solution that requires settings and installations only on my computer.The question that arises then is :

What are the other computers capable of doing?

I think most Windows computers might be able to do Remote Desktop as a client. although I am not sure how secure it will be or whether or not they can support SSH.

---

### Post by G. Cotgreave on 2007-11-20
Ha Ha!!! This is why i need you guys!!!! I don't have a clue!!!! this hostel is full of student's that they mostly use windows, my roomate and and a couple of more they have a mac and i know there is for sure 2 x-boxes!!! I need a solution that will give as much access as posible from both sides!!!

---

### Post by jonandrews on 2007-11-21
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by G. Cotgreave on 2007-11-21
Thnk you very much for the gude!!! But i still have one more problem...:( I did all the steps in the guide but I cannot finish the last step cause i don't have access to other people computers...Usualy people here that use windows the just go to RUN write the name of the computer that they want to access and they can see the shared folders of the computer. Isn't there a similar way for ubuntu?

---

### Post by Bigbird999 on 2007-11-21
Total newb here but I was able to follow this How to  [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)
and set up Samba so I can see both share my Linux files and acess files on my windows computer.  U took me just a few mins,  Personally I don't have any security concerns but with 500 plus users you might want to be a bit more careful than me.  I just assume that everybody can see what I am doing all the time so I act accordingly and don't keep my state secrets in shared directories.

BB

---

### Post by G. Cotgreave on 2007-11-21
I have done all this but still i cannot ask from people to do stuff on their computers as it is needed to from the guide, don't forget this is a public network that i am trying to access so the only access i have is on my computer and nothing else. Can people on windows use the run command as they are used to do? and if yess what should they run??

---

### Post by G. Cotgreave on 2007-11-24
Help...Anyone...?

---

