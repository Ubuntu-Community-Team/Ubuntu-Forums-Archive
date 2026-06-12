---
title: "Web Server on Ubuntu Gutsy"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by dcj on 2008-01-24
I have installed Ubuntu Gutsy with the DVD (just a normal install, I have it running dual-boot with windows.) 

I wanted to try running an apache web server, along with mySQL and PHP. From what I've heard, this can be accomplished using the 'install a server' option on the gutsy DVD when you boot up. I tried this and selected this option; however after it selected my keyboard layout for me, I was hesitant to go any further in case it tried a fresh install and I lost all my things.

Is there an easy way I can install these things with the default install of gutsy gibbon? If so, how will it be different from if I selected the 'install a server' option from the boot DVD?

---

### Post by very_japi on 2008-01-24
Youll get a LAMP server uf you type this in a terminal in Ubuntu:

```

sudo apt-get install ssh mysql-server apache2 php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by hyper_ch on 2008-01-24
Follow that here (well, the accoording sections) for mysql, apache and php:

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4)

---

### Post by WorldTripping on 2008-01-24
There are a couple of ways that complement the above method;

One is use 'taskel'

```
sudo taskel install lamp-server
```

The other is essential using taskel, but in a GUI.

```
1. Open Synaptic Package Manager
2. Select "Edit" -> "Mark Packages by Taskel"
3. Select "LAMP Server"
4. Click OK
5. Click Apply
6. Wait for Synaptic to download and install the services.
```

Hope this helps.

---

### Post by dcj on 2008-01-24
I was hoping to install them straight off the cd as they're already on there. But I'll give it a go; the end result is the same.

---

### Post by WorldTripping on 2008-01-24
Either of the methods that I posted will prompt you to insert the DVD, rather that connecting to the 'net. (I think this is correct, as it is the way I installed LAMP, and I have no 'net connection.

The difference between your current setup and the 'Install a Server' option is that you currently have a desktop enviroment, and are going to add a server. The 'Install a Server' option is command line driven, with the option of adding a desktop enviroment later.

---

### Post by dcj on 2008-01-24
Thanks for your help, but I just tried with the first method posted, and yes it downloaded all the stuff from the net... well most of it I think.

From here, how do I configure and run my web server? I've never tried it before.

---

### Post by WorldTripping on 2008-01-24
This is a good place to start.

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by dcj on 2008-01-24
Cool thanks

---

### Post by Adler on 2008-01-24
Hi All,

I've run LAMP before, but not for a while. The reason @ the time was to play with different Web Site, eCommerce, and Blog solutions on a "test" box to see what I felt comfortable with before I went "Live". 

Well, I did go "Live", *but* with hosted services for my Joomla! Sites / Forums, and a WordPress Blog.

I've got LAMP going again on my machine, but can not remember what that cool GUI is that I used to Admin MySQL databases. 

Basically, I want to work on my Blog template, torture it, then save the CSS / php files, edit what I have on my Host, then keep doing other things. 

I've Googled my brains out, but can't seem to find that GUI to Admin MySQL. 

The whole thing was so sweet. Pull packages down and install a database, and play around.

Thanks in advance for any help.

Adler

---

### Post by hyper_ch on 2008-01-25
there's an excellent WUI for mysql: phpmyadmin

---

### Post by Adler on 2008-01-25
> there's an excellent WUI for mysql: phpmyadmin

hyper_ch,

I do have phpmyadmin installed.

I use [http://localhost/](http://localhost/) to show that Apache is running, and [http://localhost/testphp.php](http://localhost/testphp.php) to get to PHP successfully. 

I'm going crazy trying to get phpmyadmin launched. I know this is what I am looking for here. Thanks for that.

What is that command to launch phpmyadmin?

Adler

---

### Post by hyper_ch on 2008-01-25
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by Adler on 2008-01-25
> [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

hyper_ch,

Thanks that worked. Cool! I've now got that going in my Firefox Browser.

Now, I just need to upload the Word Press package, and play with my Blog.

As I mentioned I want to torture my hosted Sites, but before I do that, run it on my own "test" machine, before I edit a few things. I am sure that you have done that also.

Thanks again!

Adler

---

### Post by MasterJS on 2008-01-27
I just have a small question on all this. I've gotten the whole LAMP server installed with phpmyadmin and i've gotten the WordPress package installed. Do I need to buy a domain at a webhost to use? If so, after i buy a domain, what should i do to get it up and running?

---

### Post by stump138 on 2008-01-27
you can get a free domain name at [http://www.dyndns.com]("http://www.dyndns.com")

There are instructions there as to how to make it work as well. :)
gl

---

### Post by MasterJS on 2008-01-27
Does a domain at DynDNS allow you to have a website with advertisements? I'm looking to be able to gain a profit from mine.

---

### Post by Adler on 2008-01-27
> I just have a small question on all this. I've gotten the whole LAMP server installed with phpmyadmin and i've gotten the WordPress package installed. Do I need to buy a domain at a webhost to use? If so, after i buy a domain, what should i do to get it up and running?

MasterJS,

What did you use to get a MySQl database going? That is a database?

I probably can help you further.

Adler

---

