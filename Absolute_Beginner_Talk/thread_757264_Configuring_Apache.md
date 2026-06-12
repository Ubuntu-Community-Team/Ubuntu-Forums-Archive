---
title: "Configuring Apache"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by x4KlV2OI on 2008-04-16
i have cded to apache, tried ./configure all went well but then this error popped up:

```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr

```

Thx for the help on the other post.:guitar:

P.S. i want to learn howto use tarballs due to alot of programs that aren't able to be gotten using the apt-get command.

---

### Post by shasan on 2008-04-16
Not sure if this will help you at all, but if you're just trying to get a web server up you might consider [XAMPP]("http://www.apachefriends.org/en/xampp.html"). It comes with Apache, MySQL, PHP, Perl, etc already configured. You'll have to be sure to lock it down if your server is accessible online, though. The installation for XAMPP is really easy, literally just un-tar the file into your /opt directory and run "/opt/lampp/lampp start". By the way, you should just be able to double click on a tarball and have it open.

Of course if you're doing this to learn how to use the command line and get accustomed to Linux, then that's not very helpful! Just wanted to let you know about other options. :)

---

### Post by Oldsoldier2003 on 2008-04-16
> **blakedut2 said:**
> i have cded to apache, tried ./configure all went well but then this error popped up:

```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr

```

Thx for the help on the other post.:guitar:

P.S. i want to learn howto use tarballs due to alot of programs that aren't able to be gotten using the apt-get command.

Apache is a big project for a first compile. Why not install apache from the repos and practice on something like pidgin which just happens to have a nice [tutorial]("http://ubuntuforums.org/showthread.php?t=613049") until you get a little more comfortable?

---

### Post by spiderbatdad on 2008-04-16
While the focus of this article is securing apache, it also cover compiling from source...the best way to go with apache.
You will need build-essential from synaptic before you can compile source code.
[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

---

### Post by x4KlV2OI on 2008-04-16
thx for your help, where do i get pidgin though?:confused:

---

### Post by Oldsoldier2003 on 2008-04-16
> **blakedut2 said:**
> thx for your help, where do i get pidgin though?:confused:

click the link for the tutorial I posted, it walks you through the procedure step by step. The tutorial is a very good one and has been maintained and updated so its current and valid :)

---

