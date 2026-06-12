---
title: "SSH Connection Refused"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-12-02
I am feeling reasonably clueless about this one ....

I have installed openssh-server on one machine.  Fresh install of Gutsy server and nothing else on th e machine.

I am using Putty to connect and I get the message Connection Refused.

If I use command line ssh user@host I get more or less the same thing
ssh: connect to host name port 22: Connection refused

Tried from another machine and the same message.

But I can ping the IP and the host name without issue.

Could this be something in the router I need to set.  I have had a look round but cannot see any obvious place.  The router is an Edimax ADSL2+ Router if that helps at all.

Any suggestions appreciated.

---

### Post by callan79 on 2007-12-02
> **expatCM said:**
> I have installed openssh-server on one machine.  Fresh install of Gutsy server and nothing else on the machine.


Hi There,

First thing I'd suggest is to try this on the machine that has SSH running :

```

ssh localhost

```

Let us know the result!

Callan

---

### Post by expatCM on 2007-12-02
On the server I get this

```
ssh localhost
ssh: connect to host localhost port 22: Connection refused.

```

---

### Post by Warren Watts on 2007-12-02
> **expatCM said:**
> On the server I get this

```
ssh localhost
ssh: connect to host localhost port 22: Connection refused.

```

Just tried the above on my ssh-server equipped server and got the same error.

BUT:
```
ssh -l {username} localhost
```
where {username} is the user you want to log in - allowed me to log in

In Putty, try putting your username in the Auto-login username field under Connection | Data

---

### Post by expatCM on 2007-12-02
From a client I opened putty and put in the username and then tried to connect.  Same error - Connection refused.

I then went to the cli and put in the following

putty servername user

and as a new event

putty user servername

For both items the putty terminal opened as a black window.  No command line and no prompt for the password.  When I clicked the X to close the window a message appeared "Are you sure you want to close the session" , but as mentioned it is not clear that the session was open.

if I used 

putty -l user servername 
(or ssh -l user servername)
then the connection was refused.

---

### Post by Dr Small on 2007-12-02
Is port 22 opened on your server ?

---

### Post by expatCM on 2007-12-02
I have not closed it.  I got the idea that it is open unless it is closed?

How can I find out?

---

### Post by Dr Small on 2007-12-02
No. The ports should be closed by default.
Please try installing firestarter and opening port 22 under the policies tab:
```
sudo apt-get install firestarter
```

---

### Post by expatCM on 2007-12-02
Sorry ... could I just confirm that I understand what you are suggesting .....

You want me to install Firestarter which is fine but Firestarter needs a GUI so presumably I will also need to install a Desktop on the server as well?

---

### Post by Dr Small on 2007-12-02
Oww. Well if you are on a server, forget firestarter unless you plan to install Xorg...
We'll have to find out how to change iptables to open port 22.

---

### Post by cherry316316 on 2007-12-02
> **Dr Small said:**
> Oww. Well if you are on a server, forget firestarter unless you plan to install Xorg...
We'll have to find out how to change iptables to open port 22.

oh i have the same problem 
I use the wireless network provided to me by my college.
when I do
"ifconfig"
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh <user_name>@10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file (file attached) and I added line
AllowUsers <user_name>

but its still not working. which IP address I am suppose to use.

i also followed the instruction on this website and did whatever written thr
[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)

but of no use so far. I have a firestarter (ubuntu firewall ) installed. I also
tried with stopping it but no success.


i already had the firestarter , and after reading ur post, i also opened port 22 in firestarter, but it still didnt work. . 

i have attached my /etc/ssh/sshd_config   file for reference 

in case u have come something of this type or if u have idea whats the problem is then do let me know.

---

### Post by Dr Small on 2007-12-02
I must inform you, that a connection refused has nothing to do with the SSH service.
A refused connection is the result of a firewall disallowing access to the port.

---

### Post by cherry316316 on 2007-12-02
> **Dr Small said:**
> I must inform you, that a connection refused has nothing to do with the SSH service.
A refused connection is the result of a firewall disallowing access to the port.

i also tried using ssh by killing the firestarter service , as i used to use firewall in window
and i had idea that firewall can block the ssh connection, but it didnt help

when i try to connect remotely , it says 
```
  ssh <user_name>@10.XXX.XXX.XXX
ssh: connect to address 10.XXX.XXX.XXX port 22: Connection timed out 
```

---

### Post by Dr Small on 2007-12-02
Killing firestarter will have no effect. Firestarter is only the Graphical User Interface of IPTABLES, your actual firewall.

---

### Post by cherry316316 on 2007-12-03
> **Dr Small said:**
> Killing firestarter will have no effect. Firestarter is only the Graphical User Interface of IPTABLES, your actual firewall.

    *  Yes, I am using Ubuntu 7.10 gusty.
    * I checked every thing mention on the website and open all the required port but still i was not able to connect
      through ssh to my computer, this was the case when I was using internet on wireless, as most of the time I use wireless network.
    * But Today, I was on lan/ ethernet of my college network , and to my surprise, I was able to connect through ssh to my computer.
    * I noticed that on wireless I have IP : 10. XXX . XXX . XXX , whereas on lan , I checked today I am getting IP: 131.. AAA . XXX .XXX ,also, I have noticed that the IP address of my college server is is 131 . AAA . XXX . XXX. Which means , when I am on wireless , I am
      not on the local IP network , and hence I need to connect to gateway first ( I guess ) and then to my computer.  (where AAA are same and XXX is some random variable need not be same )
    * My Problem: I don't know , how to connect to gateway and then to my computer , I only know command "ssh <user_name>@<I.P.>"


if you have any idea, then do let me know.

Thanks

---

