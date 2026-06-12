---
title: "Can't view webpage at locaolhost"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by LadyLuck on 2006-12-24
HI all and happy holidays. I have 6.06 with Apache 2 and PPHP5 setup and I am taking my very first babysteps in embedding php in html. How do I get Firefox to display my webpages locally? All I get is the 404 Not found. I cannot even view the intro.html in
/usr/share/apache/default-configs/apache-ssl/intro.html

It may be as simpe as not putting the files in the right directory, 

any help apprecitaed

LL

---

### Post by po0f on 2006-12-24
LadyLuck,

Are you getting the default page when you browse localhost?  Or is it not even connecting to that?  Make sure Apache2 is started:
```
[FONT="Courier New"]$ sudo /etc/init.d/apache2 start[/FONT]
```
If you change any of Apache2's config files, you will have to restart it as well.  Just do the same as above, but use 'restart' instead of 'start'.

By default, pages should go in /var/www/htdocs.  You will need sudo access to create/edit your web pages in there.

---

### Post by LadyLuck on 2006-12-25
Thank you po0f. There wasn't a htdocs directory in var/www/ so I made one and stuck some trial files in there and it works. I had checked that apache2 was running (sudo /etc/init.d/apache2 restart) and php was respondig (php -v), something I should have mentioned in my first post.
But thanks again
LL

---

### Post by LadyLuck on 2006-12-25
Ok I'm still having problems. When I turn my browser to a simple text file containing

```
<?php
      phpinfo();
?>

```
When I embed the same text in a file with a html header I only get the header e.g.

```
<HTML>
        <HEAD>
                <TITLE>
                        Mixing HTML and php!
                </Title>
        </head>
        <Body>
                <H1>
                        Mixing html and php
                </h1>
                <?php
                        phpinfo();
                ?>
        </Body>
</HTML>
```

---

### Post by po0f on 2006-12-25
LadyLuck,

Is Apache set up to use PHP?  I don't know if the default configs that come with it have PHP enabled.  Also, is this test page in a file ending in the *.php extension?

[EDIT]

Grammar.

---

### Post by LadyLuck on 2006-12-25
Thanks again, I was looking for a red faced smley to express my embarrasment. Apparently Apache comes with php enabled as default.
LL

---

### Post by po0f on 2006-12-26
LadyLuck,

So was it the file extension?  I've done that several times, wondering why won't my web page work.  Slap your forehead, kick your bum, you made a boo-boo.  ;)

---

