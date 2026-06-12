---
title: "Alternative to IIS (internet information services)"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by moredhel on 2006-12-21
[Running x/kubuntu 6.10 edgy]

Hi, I'm not a beginner at linux, but I have no experience with something like this, so I will put it in here...

Basically, when I'm on windows I install IIS (internet information services), which enables me to run my asp website offline, instead of having to upload to see the final result, and was wondering if there is an alternative that can be used on linux.

and before you say it, no I will not use PHP. Perhaps it is slightly more powerful, but its harder to read and write, (well in my opinion it is anyway).

thanks in advance

Moredhel

---

### Post by po0f on 2006-12-21
moredhel,

I believe the combination you are looking for is [Apache2](http://httpd.apache.org/) and [mod_mono](http://www.mono-project.com/Mod_mono).

---

### Post by moredhel on 2006-12-21
That is just what i need, except it is ASP.NET, not asp. thanks anyway

---

### Post by Moobert on 2006-12-21
> **moredhel said:**
> [Running x/kubuntu 6.10 edgy]

Hi, I'm not a beginner at linux, but I have no experience with something like this, so I will put it in here...

Basically, when I'm on windows I install IIS (internet information services), which enables me to run my asp website offline, instead of having to upload to see the final result, and was wondering if there is an alternative that can be used on linux.

and before you say it, no I will not use PHP. Perhaps it is slightly more powerful, but its harder to read and write, (well in my opinion it is anyway).

thanks in advance

Moredhel

I take it your using VBScript ?

[http://www.sun.com/software/chilisoft/index.xml]("http://www.sun.com/software/chilisoft/index.xml") is an option.. but not cheap.

There's also [http://www.apache-asp.org/]("http://www.apache-asp.org/") for Perl ASP.

I would reconsider PHP, I've developed in both and PHP is much easier to use.
For one it has much better OO, File uploading is handled sanely :),  there's
 inbuilt graphic functions, massive base of libraries eg [http://pear.php.net]("http://pear.php.net"),
 and great frameworks eg [http://www.codeigniter.com]("http://www.codeigniter.com")

If PHP syntax is really not you thing then there's other languages like:

Python eg
[http://pylonshq.com/]("http://pylonshq.com/")
[http://www.turbogears.org/]("http://www.turbogears.org/")

Not forgetting rails:
[http://www.rubyonrails.org/]("http://www.rubyonrails.org/")

---

### Post by schwascore on 2006-12-21
Count this as another vote for PHP.  If you're into web-dev using linux, you'll need to learn it at some point.  It has really matured over the past few years - don't be afraid to take the plunge!  There is a reason there is a "P" in LAMP!

just my $0.02

---

