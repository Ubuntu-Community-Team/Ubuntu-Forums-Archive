---
title: "Install a GUI"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mattjriley on 2008-01-03
Hi all,

I'm brand new to ubuntu and have chosen to install it on my remote server - I log-in using an eRIC card which gives me a control panel.

I would very much like to install a graphical interface but have no-idea how to do this remotely, (I assume that if i had the server in my office i could pop-in a cd but it's 200 miles away)

Any help would be v appreciated

tnx

---

### Post by hyper_ch on 2008-01-03
what do you mean you login using an eRIC card and what kind of control panel do you get?

---

### Post by mattjriley on 2008-01-03
the eRIC card allows me to remotely see what my server is doing, basically a screen grab remote log-in thing.

I get the basic ubuntu black screen with white text

---

### Post by hyper_ch on 2008-01-03
well, simplest thing would be:

```

sudo apt-get install ubuntu-desktop

```
for Gnome
or
```

sudo apt-get install kubuntu-desktop

```
for KDE
or
```

sudo apt-get install xubuntu-desktop

```
for Xfce

But I still dunno if that really works with your eRIC card ;) but that's the simplest way to install a gui - btw, why do you want to have a gui on a server anyway?

---

### Post by mattjriley on 2008-01-03
Thanks,

All of these commands are missing packets on my server - probably, as you say, for a good reason with it being a web server.

I just wanted to run a graphical interface because i thought it might be easier to use, I'm trying to instal a couple of php functions and am having no luck.

On my old server (shared/pre-installed) all my php functions worked, now it seems that i have to switch them on. :(

I'm trying to get a basic php mail form to work which uses this code:

<?php
mail("$name < $email >", $subject, $message,"From: $name < $uEmail >");
echo "&myStatus=Complete";
?>

and a function which allows me to write/ rewrite to text fies

Thanks for your help, if you could give me any further pointers it would be greatly appreciated.

tnx

---

### Post by mattjriley on 2008-01-03
(Sorry about my syntax - I've just realized I should tag code correctly) :s

---

### Post by hyper_ch on 2008-01-03
I guess you have not the all necessary repositories enabled.

Are you sure PHP is running on that server? Just make a simple phpinfo file with this content:

```

<?php

phpinfo();

?>

```

and run it in the browser.

---

### Post by mattjriley on 2008-01-03
Yeah - have done that and I get an php page with various info on it

just not running all of the elements by the look of things - weird

---

### Post by hyper_ch on 2008-01-04
do you have on your server a MTA installed? Without MTA php can't send any emails.

---

### Post by Borbus on 2008-01-04
You could try to set up FreeNX but I haven't and any luck with it unfortunately. You could also use VNC.

---

### Post by mattjriley on 2008-01-04
> **hyper_ch said:**
> do you have on your server a MTA installed? Without MTA php can't send any emails.

I have a mail server installed and have some mail accounts set-up on there, but a basic php mailform from a web page wont work. I'm told by my server people it's a command line that I need to run, but they don't seem to want to tell me what it is. (little monkeys).

---

### Post by hyper_ch on 2008-01-04
so you can send email through your server using an email client?

---

### Post by mattjriley on 2008-01-04
that's right, but i want to use php's 'sendmail' to allow people to use a mail form on my website

---

### Post by hyper_ch on 2008-01-04
what are you using as MTA?

---

### Post by mattjriley on 2008-01-04
I'm not sure to be honest - done some digging but can't seem to find out. I have a dedicated server with Fasthosts in the UK, it' s what ever comes pre-installed with there ubuntu linux boxes i suppose.

---

### Post by hyper_ch on 2008-01-04
are you sure it's ubuntu on there and not centos? I see both are offered by fasthost.

---

### Post by mattjriley on 2008-01-04
is def ubuntu - i see it in the start-up info when i log-in. it's version 6.06.1

---

### Post by hyper_ch on 2008-01-04
post:

```

cat /etc/apt/sources.list

```

---

### Post by mattjriley on 2008-01-04
thanks for the code - i tried typing in but i got a syntax error. :( is this verbatim or do i need to add something else?

---

### Post by mattjriley on 2008-01-04
just tried again, it says:

```
-bash: syntax error near unexpected token 'cat'

```

---

### Post by hyper_ch on 2008-01-04
no that is strange. run these commands:

```

cd /etc/apt
ls -al

```

---

### Post by mattjriley on 2008-01-04
hang-on... my mistake, it's done something!

---

### Post by mattjriley on 2008-01-04
wow!

[IMG]http://www.formworksinternet.com/screengrab.gif[/IMG]

i got this!!!

---

### Post by mattjriley on 2008-01-04
Am not sure what i'm looking at here, if i tap up and down it mentions 'postfix'

Reading up on things it looks like this is the thing I need to get working properly.

---

### Post by Rossross on 2008-01-04
Are you telling me, its as easy as putting in that little line of code to install a different gui?? I certainly have a lot to learn about this linux business. :O

---

### Post by mattjriley on 2008-01-04
Am not really intersted in installing a GUI now, as hyper_ch said, there's not really much point on a web server.

I just need to get php postfix stuff to work.

---

### Post by hyper_ch on 2008-01-04
well, if you install LAMP + Postfix like it's described here:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

starting from step 10 up to step 13 you should have mysql, php, apache and postfix installed in a way that you can use php's mail capabilities.

---

