---
title: "UBuntu 6.06, two newbies playing with SSH"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-08-18
I searched for SSH, google and forums, and I don't really get it. (Maybe because it's late).

So, can someone tell me what SSH is (In linux-stupid terms), and how to set it up?

Sofar, I gather that in a terminal, i'd type ssh <otherperson name>@<persons IP address)


But I don't even know how correct -that- is. So, anyone out there willing to suffer explaining to me? I appologize if I missed something on a link somewhere.

---

### Post by bodhi.zazen on 2006-08-18
ssh is a method of logging on to a Linux/Unix box remotely and securely. For example, on a network, I can install a ssh in windows (Putty) and access my Linux box. Works Linux to Linux/Unix, Windows to Linux/Unix, Unix to Linux/Unix NOT Linux/Uinx to windows.

ssh is primarily a CLI, but you can tunnel X through it as well.

ssh is from Unix, specifically Open BSD and is called Open ssh. Re try your search with open ssh rather then ssh.

[http://www.openssh.com/](http://www.openssh.com/)

---

### Post by bodhi.zazen on 2006-08-18
Set up of ssh is not hard, but I have not done it with Ubuntu in a while.

Add yourself, as a user, to the ssh group to start with. That may all you need to do.

---

### Post by Taigrr on 2006-08-18
So ssh isn't what i'd want to use one terminal from another computer?

I think I should have been more clear, so I appologize.

Using a remote desktop is too slow, so I wanted to just get to the command line (Or terminal..) directly, so less information has to be sent back and forth. Friend is on dial-up, so remote desktop is.. Annoying.

---

### Post by jak on 2006-08-18
It's incredibly easy to set up. You've already got ssh to access other machines, and if you want to set up an ssh server, just
sudo apt-get install openssh-server

and follow the instructions :)

You could always do it in synaptic, but the terminal screen in synaptic is too small for my liking when packages start asking questions.

---

### Post by bodhi.zazen on 2006-08-18
ssh is primarily a terminal connection and is the application of choice for what you want to do.

You are correct, it is slow as as a remote desktop, but it can be done.

---

### Post by jak on 2006-08-18
> **Taigrr said:**
> So ssh isn't what i'd want to use one terminal from another computer?

I think I should have been more clear, so I appologize.

Using a remote desktop is too slow, so I wanted to just get to the command line (Or terminal..) directly, so less information has to be sent back and forth. Friend is on dial-up, so remote desktop is.. Annoying.


No, ssh is exactly what you want, unless your friend is using Windows.
Your friend needs to set up the openssh-server so you can connect.

---

### Post by Taigrr on 2006-08-18
Okay, I connected. I just typed "ssh _friends IP address_", and it supposedly connected.

But, it asks for password. "joe@_ip address_'s password: "

Does he need to set that password, or is that his admin password (What he'd need to enter when using "Sudo"), or is it a password I must configure myself?

Thank you for putting up with me. =3

---

### Post by scxtt on 2006-08-18
your friend has to give you an account on his box for you to login to it ...

if you type **ssh <ip-address>** it defaults to using your current username ...

and for the record, you can ssh into a windows box ...

---

### Post by Taigrr on 2006-08-18
Ah! Okay, he made an account, and it worked great! I got in, and could use his computer as my own storage cabnet, should I want to screw with him.

But, I need to be on his name. He supplied his password, obviously being a friend asking for my help, but ssh hisname@hisIP just kinda sat there.

Is that not how i'd get on his name, can I get on his name, and does it matter if he's signed on or not?



Edit---

NEvermind, thank you all for all your help. I figured it all out, and that's one more thing to chalk on the learned scale. Too bad there's so much help.


Three cheers for Ubuntu! The only distro I havn't given up on.

---

### Post by nalmeth on 2006-08-18
Have a read of the output of:
man ssh

I don't know much about ssh, but I always find the man to be really revealing

---

### Post by steve.horsley on 2006-08-18
If you're interested, once you know how to log into his machine using SSH, you can also use sftp(secure FTP) and even connect using nautilus to do file transfer (File->Connect to server..., type SSH).

Also, if you connect using **ssh -X user@machine**, you can launch GUI applications on his machine and the window appears on your machine. Neat!

---

