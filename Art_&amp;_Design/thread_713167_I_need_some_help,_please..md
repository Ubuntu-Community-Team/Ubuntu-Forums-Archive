---
title: "I need some help, please."
date: 2008-03-02
forum: Art &amp; Design
---

### Post by xVehemencityx on 2008-03-02
Hi.  I've been reading guides on how to compile a tar.gz file, and they all say to use ./configure.  Well, when I type that, I get this.

```
./configure: 11: arch: not found
./configure: 24: arch: not found
[: 24: i686: unexpected operator
[: 31: ==: unexpected operator
./configure: 47: Syntax error: Bad fd number

```


What should I do?  Sorry for not knowing.

---

### Post by lyceum on 2008-03-02
You may want to change the title of your post. I do not know how to help you, but I read you post as I had no clue what you needed. Someone that could help you may not read you post because they do not know what you need.

Try these links:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

[http://www.gzip.org/](http://www.gzip.org/)

Not sure if they will help, but hopefully they can get you started.

Good luck!

:)

---

### Post by xVehemencityx on 2008-03-02
Really?  I always thought that not being specific made people want to figure out what I needed.  Thanks, though.  And thanks for the links.  They didn't really help, but when I get ./configure to work, I'm sure they will.  Not like it matters, because now my ubuntu won't boot.  It gives me this weird error.  I'm gonna reinstall it and start from scratch.

---

### Post by Whiffle on 2008-03-02
Sounds like you need to extract it first.  A tar.gz file is only a compressed archive, similar function as a zip file.

To make use of it do:

```

tar zxvf example.tar.gz

```

then you cd into the directory that it makes:
```

cd exampledirectory

```

and then:
```

./configure

```

After that runs, and runs successfully (it might error out if it doesn't find libraries that it needs, in which case you'll have to install those first, they can usually be found with aptitiude.

then do, this command actually builds the program:
```

make

```

and then you have a choice.  The standard linux way of installing something is:
```

make install

```

But that usually isn't convienient to uninstall. So, I install checkinstall
```

sudo apt-get checkinstall

```

Now you can do 
```

sudo checkinstall

```

and it will generate and install a deb package, which can easily be uninstalled later.

Hope this helps. :)

---

### Post by lyceum on 2008-03-03
> **xVehemencityx said:**
> Really?  I always thought that not being specific made people want to figure out what I needed.

I usually look for titles that I know what they are talking about, so I don't waist time on people with problems out of my league. 

> **xVehemencityx said:**
>   Thanks, though.  And thanks for the links.  They didn't really help, but when I get ./configure to work, I'm sure they will.  Not like it matters, because now my ubuntu won't boot.  It gives me this weird error.  I'm gonna reinstall it and start from scratch. 

what is the error? if it is error 17, I get that when my computer tries to boot from an external hard drive or flash stick. There is not OS so it just says "Error 17" . Just unplug the external and you are good to go, but a fresh install never hurt, especially when you are having other issues. (I only mention error 17 as I have been dealing with it since I started using Ubuntu and it never hurts to be proactive) 

good luck! :)

---

