---
title: "could someone explain network &amp; ssh"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-08-23
I am trying to learn more about computers and Ubuntu. On an old machine I have set up a server using Ubuntu Server. All is well sometimes . . . I can connect to the network using nuatilus. I am asked for user name, host and password. That works fine. However when I try to connect to the machine using ssh that same password gets me a message that my password is incorrect. So are ssh  and networking are completely different? I guess what I need to know is how do you set permissions and passwords in ssh on (I guess) the server machine? 

Here is the error I get:
debug1: Authentications that can continue: password
Permission denied, please try again.

Thanks Tim

---

### Post by asmoore82 on 2007-08-23
are you using the same username accross both machines? if not you have to tell ssh the username with '-l' (lower-case L)

```
~ $ ssh -l *<username> <hostname>*
```

---

### Post by asmoore82 on 2007-08-23
Oh, i misunderstood I think ... you aren't on the commandline, but using the "connect to server" with SSH ...
you need to install sshd, the ssh server on the machine you want to connect to.

EDIT: the sshd package name in synaptic is 'openssh-server'

---

### Post by SVWander on 2007-08-23
> **asmoore82 said:**
> Oh, i misunderstood I think ... you aren't on the commandline, but using the "connect to server" with SSH ...
you need to install sshd, the ssh server on the machine you want to connect to.

EDIT: the sshd package name in synaptic is 'openssh-server'

Actually the problem is with the command line and not a problem connecting to the server using Places/Connect to Server. In fact one of my machines is connected to the server and downloading file right now. The password . . . and everything worked just fine. However when I try to connect using the command line I get the error message. I have never been able to use the host name to connect. However for a short time I was able to connect using :
 ssh -v [email]george@192.168.x.xx[/email] 
Now when I use the command I am asked for  the password. The password is correct but I get:
debug1: Authentications that can continue: password
Permission denied, please try again.

So maybe I am confused about connecting to the network and ssh . . . LOL I don't know what the hell I am doing!

TM

---

### Post by dwhitney67 on 2007-08-23
Use asmoore82's advice.  The proper syntax is:

```
$ ssl -l username sshServer
```

If the login ID that is currently used on the client system is the same on the server system, then the -l username is optional.  If you want to connect to the server using a different login ID, then the -l is not optional.

The -v option you are supplying is not needed.  That is for verbose output.

Btw, unless you want to enter an IP address for your server, the best thing to do is to create an alias for it in the /etc/hosts file.

Anyhow, here are examples:

$ ssh -l joe 192.168.1.105

$ ssh -l joe timbuktu

$ ssh timbuktu

---

### Post by SVWander on 2007-08-23
> **dwhitney67 said:**
> Use asmoore82's advice.  The proper syntax is:

```
$ ssl -l username sshServer
```

If the login ID that is currently used on the client system is the same on the server system, then the -l username is optional.  If you want to connect to the server using a different login ID, then the -l is not optional.

The -v option you are supplying is not needed.  That is for verbose output.

Btw, unless you want to enter an IP address for your server, the best thing to do is to create an alias for it in the /etc/hosts file.

Anyhow, here are examples:

$ ssh -l joe 192.168.1.105

$ ssh -l joe timbuktu

$ ssh timbuktu

OKAY, Thank you. With the correct syntax I was able to use the command
```
 ssl -l username sshServer
```

However it still get: Permission denied, please try again.

Is the problem on the server side. I used the command:
 useradd <name> -m -G users
 smbpasswd -a <name> 

As I said I can connect with nautilus to the server but not through the command line. I will go back and supply an  alias for it in the /etc/hosts file. I think I am getting somewhere now. LOL don't laugh to hard at me.
tm

---

### Post by Dr Small on 2007-08-23
Make sure the computer that has the openssh-server on it has port 22 enabled.

---

### Post by qpieus on 2007-08-23
Are your passwords the same on each computer? When you are connecting to the server via ssh, you need to use the username for your account on the server and the login password for that account on the server. Your username and password for your regular workstation won't work unless they happen to be the same as on the server.

Earlier you mentioned you used the smbpasswd command at some point. That command is for setting a samba password, so it has no bearing on you trying to connect via ssh.

Here's the command I use to ssh into my server:

ssh username@serverIPAddress

it'll connect and then prompt me for my password (for that account of the server).

---

### Post by SVWander on 2007-08-26
Thank everyone that answered my question. I finally got ssh working. I still have many questions bout it. Especially to make it work over the internet. I am now seven hours from my server but I have no idea how to connect to it. I am sure I would have had to set the router up before I left.
Tim

---

### Post by dwhitney67 on 2007-08-26
Congrats on getting SSHD working.

Your assumption is correct.  To access your server from the outside, you will need to configure your router to forward port 22 packets to the server.  I use a Linksys router, therefore if you have the same then I can tell you exactly what to do.  Otherwise I suggest you reference any documentation you have on your router.

Oh, and by the way, when you ssh to your server from the "outside" world, you need to ssh to the IP address assigned to you (actually your router) by your ISP.  If you have trouble remembering numbers, considering setting up an account and URL(s) at [http://www.dyndns.com](http://www.dyndns.com).  It is free.

---

### Post by Warren Watts on 2007-08-26
Having SSH set up on your server also poses some security risks to your system, and you should take some precautions to insure people you don't want having access to your system **don't** gain access.

One way is to move your SSH listening port to something other than port 22, making it harder for hackers to find

Another way is to restrict who is allowed to log in remotely.

Here is a link to a Thread regarding some measures I took to secure my server, along with some follow up suggestions from other forum members:
[URL="http://ubuntuforums.org/showthread.php?t=520668"]
http://ubuntuforums.org/showthread.php?t=520668[/URL]

Believe me, if you have open and active listening ports, people are constantly trying to get in.  My server gets at least 15-20 illegal log in attempts a week, both thru SSH and FTP.

If you want to see who has been attempting to access your system, take a look at the auth.log files in /etc/log

---

### Post by punkybouy on 2007-09-02
"However it still get: Permission denied, please try again.

Is the problem on the server side. I used the command:
useradd <name> -m -G users
smbpasswd -a <name> "

Isn't the smbpasswd command for samba and not ssh?

---

