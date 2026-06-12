---
title: "Version of php? says not installed, but it is."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by spcoex on 2008-02-24
Hi everyone, 

I have the LAMP stack installed on my ubuntu server (used the server installation option) and everything is working well (joomla, mediawiki, etc)

When I went to check which version of php I had installed - using php -v at the terminal - it says "the program 'php' is currently not installed" - what?? its is installed, otherwise none of my apps would be working. 

QUESTIONS: 

- am i using the correct command to determine which version of php im using (ie. php -v)?
- why is it saying is not installed??

Thx

---

### Post by Cypher on 2008-02-24
You're better of using the following in a file called p.php to get the version and mode
```

<?php phpinfo(); ?>

```

---

### Post by GreaterCore on 2008-02-24
Hi there,

I believe you may have confused the PHP module that is called from Apache itself from the CLI (Command Line Interface).  Try ''sudo apt-get install php5-cli''. I am guessing that you most probably have installed PHP5, but if you have not this will install it anyways.

Cheers.

---

### Post by mkoehler on 2008-02-24
It typically gives you the error "xxxxx is not installed" when it knows that you can find a package with that name in synaptic.  I have never personally used the ubuntu server distro, so I don't know how it sets up the LAMP (which packages it uses).  However, there isn't a binary called "php" in your PATH, but it knows where that binary is available from, so it is telling you how to get it.

In your case, you already have it.  I would follow the directions given by Cypher to figure out your version of php.

---

