---
title: "Keyserver timing out"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by shavenlunatic on 2007-01-28
Hi, im fairly new to linux hence me using this guide:

[http://wiki.cchtml.com/index.php/XGL-Ubuntu](http://wiki.cchtml.com/index.php/XGL-Ubuntu)

Everything fine until. i get to 

```

    *  After you add the repos in the sources.list file, issue the following commands: 

   wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
   KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -

```

and i get:

```

:~$ wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add - KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
--20:52:51--  http://www.beerorkid.com/compiz/quinn.key.asc
           => `-'
Resolving www.beerorkid.com... 208.113.136.19
Connecting to www.beerorkid.com|208.113.136.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[===================================================================>] 1,692          9.78K/s             

20:52:52 (9.74 KB/s) - `-' saved [1692/1692]

OK
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```


if i ping subkeys.pgp.net i do get a response, so server is not down...

HEEELLPPP (thanks in advance)

---

### Post by sardion on 2007-01-28
Are you running edgy or dapper?

If edgy, you should use the XGL included in edgy.

In either case, I suggest undoing all the beerorkid stuff and instead using 

ubuntu.beryl-project.org

That is more recent and "more official" than what you were doing.
I suspect (though don't know) that the site you used is out of date and the keyserver issue reflects that.

---

### Post by shavenlunatic on 2007-01-28
> **sardion said:**
> Are you running edgy or dapper?

If edgy, you should use the XGL included in edgy.

In either case, I suggest undoing all the beerorkid stuff and instead using 

ubuntu.beryl-project.org

That is more recent and "more official" than what you were doing.
I suspect (though don't know) that the site you used is out of date and the keyserver issue reflects that.

I'm using edgy, how do i enable xgl that came with it? can't seem to find it anywhere or find any info online regarding it,,,


also, my source list includes

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by shavenlunatic on 2007-01-29
> **sardion said:**
> Are you running edgy or dapper?

If edgy, you should use the XGL included in edgy.


sorry for the *bump* but can anyone help / point me in the direction of doing this?

---

### Post by shavenlunatic on 2007-01-30
nm, i downgraded to dapper and got everything working instantly... edgy stole several days of my life.. long live dapper! :)

---

