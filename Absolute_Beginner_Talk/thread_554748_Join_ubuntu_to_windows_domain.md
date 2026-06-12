---
title: "Join ubuntu to windows domain"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by dazormiq on 2007-09-19
I am playing with Ubuntu for the 4th time.  I swear it gets easier to use after every update.

I am an administrator of a 2000/2003 windows domain and would like to join my Ubuntu workstation to the domain.  I need to be able to map network drives, use my domain user name, and use server based printers.  Everything I have found while searching is configurations for setting Ubuntu up as a server, an authenticator, or for file sharing.  All I need is a setup for a plain old workstation.


There has to be an easier way to join a domain other than the 30 steps to try and get samba to function.

Any help is greatly appreciated.

---

### Post by kelnage on 2007-09-19
If I understand you correctly, you want to install Samba. Once that's installed, you go to System -> Administration -> Shared Folders and open the general tab. You enter the domain name and save the configuration. 

You should be able to pick up Windows machines in Places -> Network (though I find it often takes ~5 minutes to pick them up). 

You can also map network drives by using "Connect to server" and entering the correct values.

---

### Post by lisati on 2007-09-19
> **kelnage said:**
> If I understand you correctly, you want to install Samba. Once that's installed, you go to System -> Administration -> Shared Folders and open the general tab. You enter the domain name and save the configuration. 

You should be able to pick up Windows machines in Places -> Network (though I find it often takes ~5 minutes to pick them up). 

You can also map network drives by using "Connect to server" and entering the correct values.

I have found that the first time I go to places->Network to access folders on a windows machine it can sometimes take a while but once Ubuntu recognise the folders it can access things seem to go slightly faster.

---

### Post by ezphilosophy on 2007-09-20
> **dazormiq said:**
> I am playing with Ubuntu for the 4th time.  I swear it gets easier to use after every update.

I am an administrator of a 2000/2003 windows domain and would like to join my Ubuntu workstation to the domain.  I need to be able to map network drives, use my domain user name, and use server based printers.  Everything I have found while searching is configurations for setting Ubuntu up as a server, an authenticator, or for file sharing.  All I need is a setup for a plain old workstation.


There has to be an easier way to join a domain other than the 30 steps to try and get samba to function.

Any help is greatly appreciated.

Yes!  I have been trying to do this for over a year!  I work in an office that is using a windows 2000 network.  It requires us to input our username and password.  I have the only ubuntu machine in the office and I really just want to print.  However, in order to do that, I need to authenticate myself on the network.  I remember that about 6 months ago, I was able to authenticate myself and able to access the files.  However, now I can't even do that.  I would love to solve this problem.  Basically, I really only need to print to through another (windows) computer on the network but need to authenticate myself on the network first.

---

