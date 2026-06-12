---
title: "building server - a couple of questions/problems with more technical aspects"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by TheAddict on 2008-03-01
Okay, so I am in the process of configuring Feisty desktop to run as a file/print server, and have set up Samba to share the files, but now I need a way of remote accessing the box as I plan to run it headless. 

So I have read around and the tutorial I am following shows how to implement this using VNC, but the problem is, I have either screwed up the configuration somehow, or I just don't know how to connect, so if someone could give me a link to a idiotproof guide to setting up VNC on your box, that would be great. I am using ultraVNC client on the laptop to try and connect, but just get "failed to connect" or similar. 
The reason I am wanting to use VNC over SSH is that I am not confident in my use of the command line, and as such I need the GUI like a baby needs its secuirty blanket. that is also why I'm not using the server edition.

I'm also struggling with configuring the system to become the print server as well (read: i have no clue where to even start), so a pointer would be appreciated.

I realise that there a bunch of other threads regarding this, but I couldn't make heads nor tails of any of em. hence the new post

thanks a bunch for any help you can provide

---

### Post by jeffus_il on 2008-03-01
You can run any gui application on the remote computer after you have connected using ```
ssh -X targetmachine
```, by just typing the program name, try ```
xclock
```

---

### Post by banewman on 2008-03-01
This should help with the vnc -
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
:)

---

### Post by TheAddict on 2008-03-01
Awesome!!

Thanks for the tut link mate...

and jeffus

I'm confuddled.. do you mean to say that I can run GUI apps through an SSH connection, without doing VNC through SSH?

---

### Post by jeffus_il on 2008-03-01
> **TheAddict said:**
> Awesome!!

Thanks for the tut link mate...

and jeffus

I'm confuddled.. do you mean to say that I can run GUI apps through an SSH connection, without doing VNC through SSH?
Definitely, with no extra setup, try it! ( you must pass the -X parameter when running ssh as shown previously)

---

### Post by TheAddict on 2008-03-01
okay.. so 

```

dean@file-server:~$ ssh -X file-server
The authenticity of host 'file-server (127.0.1.1)' can't be established.
RSA key fingerprint is 00.00.00.00.00.00.00.00.00.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'file-server' (RSA) to the list of known hosts.
dean@file-server's password:
Permission denied, please try again.
dean@file-server's password:
Linux file-server 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sat Mar  1 23:58:31 2008 from 192.168.1.4
dean@file-server:~$ xclock
Error: Can't open display:
dean@file-server:~$


```

is what I got.... (whoa, thats heavy I don't know if I needed to include all of that)

I am connected via my windows laptop, is that gonna make a difference

---

### Post by rapiscan on 2008-03-01
On your server, you need to configure SSH to allow X11 forwarding.  In the terminal (on your server) type:
```
gksudo gedit /etc/ssh/sshd_config
```
Find this line in the config file:
```
#   ForwardX11 no
```
Uncomment it by removing the '#' and change it to yes.  This will allow you to run GUI applications on the server.

---

### Post by TheAddict on 2008-03-01
> **rapiscan said:**
> On your server, you need to configure SSH to allow X11 forwarding.  In the terminal (on your server) type:
```
gksudo gedit /etc/ssh/sshd_config
```
Find this line in the config file:
```
#   ForwardX11 no
```
Uncomment it by removing the '#' and change it to yes.  This will allow you to run GUI applications on the server.

Okay, so I ran gedit /etc/ssh/sshd_config

turns out that x11 forwarding was already allowed...

---

### Post by TheAddict on 2008-03-01
Okay... 

I gave up on this for the night last night... I can get SSH to work now worries, but I think I might have left some extremely important information out

I'm trying to VNC from a m$ machine.. not another ubunutu machine..

is that gonna make a difference?

---

### Post by rapiscan on 2008-03-01
I don't have any immediate advice regarding X forwarding.  There seem to be many threads relating to the issue that you describe.  If you would like to get X forwarding working, I would suggest searching and checking out solutions in those threads.

Regarding VNC, did you check out the link that banewman posted?  Here  is another one helpful howto which has a section about the windows client:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

There shouldn't be any problem using TightVNC on windows.  If you continue to experience problem with VNC, I would try to be as specific as possible with the problem(s) and post the exact error message.

---

### Post by TheAddict on 2008-03-01
Thanks for that mate.. I was searching the forums as I got your reply, and was in fact reading that very link you provided. 

I did read the link that banewman posted,and i tried to follow it as best I could, but my mind was swimming.. I will give it another go now, 

Anyways... perhaps I will let this thread die, and keep reading until I can understand how to fix the prob... cheers mate

---

### Post by rapiscan on 2008-03-01
No problem.  But dont' feel like you can't post again if/when you run into specifc problems, we'll be happy to help.

---

