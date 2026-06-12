---
title: "I need to save a website"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-12-31
My dad needs me to download his website so I can rebuild it when he kills his domain.

how can I do this and download everything with the site?

---

### Post by aysiu on 2007-12-31
Use FTP? How did you upload the site in the first place?

---

### Post by fiddledd on 2007-12-31
wget will download an entire website, it's already installed I believe. There's a GUI for it if you prefer it, it's called gwget. I think it's in the repositories.

Edit: I it did again, typed too slow, posted too late :)

---

### Post by koenn on 2007-12-31
wget -r  -l inf -np [http://www.whatever.xx/](http://www.whatever.xx/)

or something like that. man wget or wget --help will show options

---

### Post by tdrusk on 2007-12-31
[http://www.agmedicalequipment.com/](http://www.agmedicalequipment.com/)
this is the site.
I tried the wget command above but it only downloaded the index page. I need it to download the whole site into multiple html files as is.

I just downloaded each page using firefox. I was hoping there was a cool cli way to do it.

---

### Post by fiddledd on 2007-12-31
> **tdrusk said:**
> [http://www.agmedicalequipment.com/](http://www.agmedicalequipment.com/)
this is the site.
I tried the wget command above but it only downloaded the index page. I need it to download the whole site into multiple html files as is.

I use gwget to do exaclty what you are trying to do and it downloads the entire site. I know wget will do this also as gwget is just a frontend. If you don't want the gui then type man wget in a terminal to see what options you need.

---

### Post by EXCiD3 on 2007-12-31
Whats wrong with using FTP?

---

### Post by tdrusk on 2007-12-31
> **EXCiD3 said:**
> Whats wrong with using FTP?

me, I don't know how.

---

### Post by EXCiD3 on 2007-12-31
Very simple, if you know the FTP username and password you can use FileZilla to browse the files on the webserver.

---

### Post by dcstar on 2007-12-31
> **tdrusk said:**
> My dad needs me to download his website so I can rebuild it when he kills his domain.

how can I do this and download everything with the site?

Go into Synaptic and install the **webhttrack** package.

---

### Post by Dr Small on 2007-12-31
If the website uses any Php, it will not download the source of the Php files (using wget). You would have to use FTP.

Using an FTP Client and connecting to the server with the proper username & password is as simple as eating pie ;)

Dr Small

---

### Post by frenchsquared on 2007-12-31
Can you get Filezilla on lynx

if so is as simple as copy and past 

I would like filezila foe ubuntu if anyone knows how to install
thanks

---

### Post by frenchsquared on 2007-12-31
wOW sorry that was stupidly easy

---

### Post by brunovecchi on 2008-01-15
I'm surely late for this but, as I see that the thread is solved, I want to share my solution. I lke simple solutions!

wget -rkpl 0 URL

-r= recursive: follows the links
-k= changes links adresses to their local file adress
p= downloads images
-l= recursion level. 0 for infinite.
I use it all the time to locally save tutorials, howtos and stuff. You never know!

---

### Post by FrankVdb on 2008-04-30
Make sure you copy any database files as well!

If the site was made with software like Joomla or Drupal, you won't be able to reinstall it if you don't have the MySQL database.

---

### Post by Crick on 2008-05-03
I have to second wget. 

> wget -r --convert-links -nH [http://www.website.org](http://www.website.org)

Will get that whole website.

Yet another reason why Ubuntu rocks. wget is natively there on the system, whereas the Windows approach means having to go on the web download, and figure out the gui of whatever it is you are using, and either paying or searching for serialz.

In this case CLI is so much easier, free, ethical and just plain works.

---

