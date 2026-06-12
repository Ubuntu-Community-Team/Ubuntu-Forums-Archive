---
title: "Proxy woes"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Cod on 2006-07-11
I'm really struggling with getting Snyaptic or Aptitude to work.

When I try to update packages (either using "sudo apt-get update" in a terminal, reload in Synaptic, or update in Aptitude) I get the same problem: 407 Proxy Authentification required.

So I'm sure it's a proxy problem.  I'm at work and have to use a proxy to get outside.  In Firefox, I entered the proxy address into the relevant bit of connection settings.  When I use the web for the first time a window pops up asking for my username and password, I enter it, and everything is fine.  So I know that I can get round the proxy with Ubuntu.  Good.

But I cannot update packages.  I know that the connection settings in Firefox do no also set the connection settings for Synaptic etc.  Looking throught the forums for the past few weeks I have tried several approaches:

1.  In a terminal window I have entered "export http_proxy="http://username:pword@proxyaddress:port"
But this doesn't work - I get the usual proxy authentification error.  When I use "printenv" I can see that http_proxy has been set as instructed.

2.  I have edited apt.conf to include the line:
Acquire::http::Proxy "http://username:pword@proxyaddress:port";
But this doesn't work.  Where should apt.conf be located, out of curiosity?  I have tried rebooting after editing and saving, to no avail.

3.  In Synaptic, under preferences -> settings -> network I have entered a manual proxy configuration using the syntax:
username:pword@proxyaddress
for both http and ftp proxy.

I have tried various combinations of the above.  Nothing works.  I've searched the forums and the web and these three suggestions are the only things I find. Can anyone tell me what I'm doing wrong and help me put it right?  I can use the internet fine, but I can't install / update packages.

Thanks in advance

---

### Post by mister_p_1998 on 2006-07-11
I used to run my Ubuntu box through a proxy on my windows box), worked ok on web & newsgroups, but synaptic wouldnt connect properly, I got a router and all problems were solved.

---

### Post by Cod on 2006-07-11
The problem is that I'm at work and can't do anything to the network setup.  I just have a LAN cable coming out of the wall.

---

### Post by insyzygy on 2006-07-11
Have you tried using apt-get directly. I had read that some people had success with that when synaptic wasn't working.

If you want to search for something you can do 

```
apt-cache search (what you want)
```

This will give a list of things matching that name

and then to install

```
sudo apt-get install ( your package)
```

To remove things you can do 

```
dpkg -r (pacakge to be removed) 
```

Obviously this doesn't fix your problem with synaptic but if it works at least in the meantime maybe you can install packages.

---

### Post by Cod on 2006-07-11
Thanks for the help.  Unfortunately my problems are not confined to Synaptic, but apt as well.

For example, if I want the package Gnomebaker using:

```
apt-cache search Gnomebaker
```
returns nothing.

Then using:
```
sudo apt-get install Gnomebaker
```
reutns an error (couldn't find package...).

This is possibly because I can't use update, e.g.
```
sudo apt-get update
```
Gives me the usual 407 Proxy Authentification Required error.

I have set the http_proxy using:
```
export http_proxy="http://username:pword@proxyaddress:80
```

I thought that maybe my source list is bad but when I use Firefox to go to the source address, it's fine.

I'm stumped.

---

### Post by insyzygy on 2006-07-11
I don't know, hopefully someone with more experiences on proxies will help out. One thing you can do for sure if you really need something now (though this is kind of a hack) is download the packages manually from 

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
 
and install by 

```
 sudo dpkg -i (yourpackage.deb) 
```. 

The main drawback to this is if package A depends on B, dpkg will tell you and you'll have to go find B install it and then try to install A again, synaptic or apt-get will just get all the dependencies for you, this is painful if there are lots of dependencies. I've used this to install packages on computers that didn't have networking working by downloading on another computer and transfering via a usb key. Its definitely a hack but might be useful till you get this working.

One other thing, you may be aware of this but if not it would be useful to know that
```
export http_proxy="http://username:pword@proxyaddress:80
``` 
only will apply to a given terminal while that terminal is open. So if you typed this once in one terminal and then open a second one you need to type that again in the new terminal for it to apply to what you do in the new terminal, or even in a different tab I think.

---

### Post by l.tambiah on 2006-07-11
> **Cod said:**
>  
2.  I have edited apt.conf to include the line:
Acquire::http::Proxy "http://username:pword@proxyaddress:port";
But this doesn't work.  Where should apt.conf be located, out of curiosity?  I have tried rebooting after editing and saving, to no avail.



hmm, at my work place the above will make my apt-get work. 

```
sudo vim /etc/apt/apt.conf
``` 
then added as you did:

Acquire::http::Proxy "http://username:Password@proxyAddressPortNum";

---

### Post by Cod on 2006-07-11
Thanks again for the help.  I'll have a try at the hack, at least that way I may be able to install something.  It is frustrating about the proxy problems though.

Can anyone else shed some light?

---

### Post by groggyboy on 2006-07-12
I managed to get synaptic working behind a proxy without any need for the terminal or conf files.

From inside Synaptic: "Settings > Preferences" and then click on the "Network" tab.  Configure as nescessary.  GUIs are amazing things, yet very few linux people ever seem to want to use them! :)

---

### Post by insyzygy on 2006-07-13
If you look in the following at the bottom of the page
[http://www.ubuntuforums.org/showthread.php?t=96802]("http://www.ubuntuforums.org/showthread.php?t=96802")
someone has a discussion of the fact that they needed to include the domain 

```
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT";
```
instead of
```
Acquire::http::Proxy "http://MYNAME:MYPASS@MY.PROXY.COM:MYPORT";
```
in /etc/apt/apt.conf.

There also was a discussion of NTLM, some secret microsoft proxy protocol. 
One guy claimed to be able to use a  python script that negotiated the proxy 
[http://www.geocities.com/rozmanov/ntlm/]("http://www.geocities.com/rozmanov/ntlm/")
according to this website as well as microsoft 
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;q315909]("http://support.microsoft.com/default.aspx?scid=kb;EN-US;q315909")
This error 407 is due to the fact that they are using this special protocol. Could one of these be the issue?

I looked at that python script and it seems that it sets up a proxy server on your own system (with the ip address 127.0.0.1 at port 5865). You configure the script with your password and username and the actual proxy server for your company. You tell all your programs to use the scripts proxy server and it forwards them to your companies, doing the microsoft 
protocol correctly, at least that seems to be how its supposed to work.

It seems if this ntlm thing is the problem firefox should have been more trouble to get working, but maybe it has this built in by now.

---

