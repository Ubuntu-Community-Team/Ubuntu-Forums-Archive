---
title: "help with perl script"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by dreven on 2008-01-16
I am totally new to linux and have absolutely no clue about perl.

I am trying to use a perl script called fapzilla.pl it is a program meant to show my bandwidth usage for wildblue satellite.    When i tray to run it i get this error message

./fapzilla.pl
Can't locate XML/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./fapzilla.pl line 24.
BEGIN failed--compilation aborted at ./fapzilla.pl line 24.


Any help would be much appreciated

---

### Post by mike^_^ on 2008-01-16
looks like you need the 'Simple.pm' perl module. see if you find it using 'locate'

```
sudo updatedb
```
```
locate Simple.pm
```

If you cant find it, try installing it with CPAN.

```
sudo perl -MCPAN -e 'shell'
```
```
cpan> install Simple
```

---

### Post by dreven on 2008-01-16
I found simple.pm is there supposed to be a directory that all perl scripts are supposed to be executed from?

---

### Post by dreven on 2008-01-16
I have perl 5.88 on my system but it is not in the directories that the script is looking for them in any suggestions? for instance you can tell by my post what directories it is looking for SImple.pm in    I did a search and Simple.pm is located in 3 different directories 

/usr/share/Perl/5.8.8/Test ,   /usr/share/perl/5.8.8/Filter ,  and also in /usr/share/Perl/LWP

---

### Post by musikgoat on 2008-01-16
> **dreven said:**
> I have perl 5.88 on my system but it is not in the directories that the script is looking for them in any suggestions? for instance you can tell by my post what directories it is looking for SImple.pm in    I did a search and Simple.pm is located in 3 different directories 

/usr/share/Perl/5.8.8/Test ,   /usr/share/perl/5.8.8/Filter ,  and also in /usr/share/Perl/LWP

Looks like you can add directories to @INC

here is instructions:
[http://www.perlmonks.org/?node_id=222277](http://www.perlmonks.org/?node_id=222277)

hope this helps,  also it may be good for you to keep with only lower case or upper case (if thats not just a typo :-) )

---

