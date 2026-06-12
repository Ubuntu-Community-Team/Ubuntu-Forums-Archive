---
title: "Problems, can't install packages."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-25
hey

I am a web developer, and I am new to linux.

I am facing some problem with the Synaptic Package Manager.

I need to install a web server on linux, so I need apache, php, and mysql.
I went to the Package Manager to install apache ... it worked. but when I wanted to install php I couldn't find it so went to the repositories and did exactly what is mentioned in the documents, I added php [http://www.php.net](http://www.php.net) php4 in the custom and it gave me an "unable-to-find" error statement ... 

I signed in terminal as root and them I typed:

```
apt-get install php4
```
but it gave me this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

What does that mean? and how can I install php and mysql without getting such errors?

any help will be appriciated.

---

### Post by gondilon on 2006-04-25
when you go to the repositiories, set the repository as [http://ftp.debian.org](http://ftp.debian.org) sarge main. That should enable you to get the packeges you need.

---

### Post by mostwanted on 2006-04-25
[QUOTE=gondilon]when you go to the repositiories, set the repository as [http://ftp.debian.org](http://ftp.debian.org) sarge main. That should enable you to get the packeges you need.[/QUOTE]

For the love of FSM, don't do that. Don't mix Ubuntu and Debian repositories. See my answer in your other topic.

---

