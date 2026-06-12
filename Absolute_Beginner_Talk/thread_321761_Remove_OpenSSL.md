---
title: "Remove OpenSSL"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by lotusvball on 2006-12-19
I would like to uninstall OpenSSL.  I don't want to have it at this time.  Extreme newbie the the linux world and I have too many other things to do and learn first.  I installed LAMP and with that I think OpenSSL installed also.  I want to unistall OpenSSL, but I am not sure if it will break anything.  I have a webserver running with Apache2, php, and mysql.  I also use Webmin.

---

### Post by schwascore on 2006-12-19
If you mean OpenSSH, then:

```
sudo apt-get remove openssh-client openssh-server
```

Shouldn't break anything aside from your ability to ssh into / out of the machine.

If you *really do* want to remove OpenSSL, that will cause a lot of trouble with your machine.  It will remove the ability of your machine to communicate with other machines using SSL - that's usually seen as a problem.  If you still want to remove OpenSSL:

```
sudo apt-get remove openssl
```

---

### Post by lotusvball on 2006-12-19
So openSSH is the same as OpenSSL?  for installation and removal purposes.

---

### Post by schwascore on 2006-12-19
no, they are not the same.  OpenSSH allows you to log into computers through an encrypted command line (often called ssh-ing).  The client allows you to ssh to other machines while the server allows you to ssh into your own machine.

OpenSSL is a package that allows other software to understand Secure Socket Layers (used to secure / encrypt network communication) - basically SSL is responsible for the "secure" websites you visit ex: web banking, payment sites like Paypal, etc.

I don't know of any reason why OpenSSL should be removed, but if you want to make sure that no one can gain command line access to your machine, just remove openssh-server.

I hope that clears things up.

---

### Post by lotusvball on 2006-12-19
Actually no.  I need to remove OpenSSL because I don't have the knowledge or time to deal with it at this time.  I am trying to install Axigen for a mail server and it is giving me problems with SSL running.  I want to remove SSL and get Axigen running and then when I have more time I will start to learn about SSL.  Until then I would like to remove OpenSSL but I am not sure how or what problems I would cause (besides reduced security).

---

### Post by schwascore on 2006-12-19
OpenSSL is benign on its own... it does not actively do anything.  That is, it is not a running process on your computer.  It is merely a set of files that allow other programs to use Secure Socket Layers.  If you still want to remove it, the only side effect that I can think of is that any software that uses SSL might not work correctly, especially if they come across SSL being used on an outside machine.  For example, I do not know what would happen if you went to an SSL secured website withouth OpenSSL installed.  Perhaps nothing, but I've never tried it.

Worst case scenario is that you uninstall it and things break.  Then all you have to do is re-install it and things should work again.

If Axigen is complaining about SSL, it is probably in the configuration of Axigen.  Axigen is probably configured to use SSL and unless you generate a SSL certificate, it could be confused.  Why don't you check the config for Axigen to see if you can turn of its use of SSL rather than removing it all together.

---

### Post by lotusvball on 2006-12-19
So what it sounds like is the program I am trying to install, Axigen, is set to use SSL and I need to create the CA for it to work.  Therefore I should leave OpenSSL alone.

---

### Post by schwascore on 2006-12-19
From what you have described that is definitely what I suggest.  Try to reconfigure Axigen because that would be my first guess as to where the problem is.  I am not very familiar with setting up Axigen, so I can't offer any specifics, sorry.

---

### Post by lotusvball on 2006-12-19
Thank you very much.  I will work on that part tonight.

---

