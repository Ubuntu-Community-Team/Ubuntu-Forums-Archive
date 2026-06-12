---
title: "Installing java 1.5 (package sun-java5-jre and sun-java5-jdk don't exist)"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Sensei Eggwoah on 2006-08-28
In the common tasks--->programming section of the ubuntu desktop manual, there are instructions on how to install sun's java jre and jdk.  I have the extra repositories enabled.  However when I type
```
sudo apt-get install sun-java5-jre
```
I get the following message:
```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre

```
Same goes for the jdk. What am I doing wrong?

---

### Post by Titus A Duxass on 2006-08-28
Have a look on the Automatix webpage, that is an easy way to install the packages you want.

---

### Post by true_friend on 2006-08-28
yup he is right. use automatix for such tasks.
or enable repsitories in synaptic first. synaptic is package manager Go to Settings> Repositories and check all of them then click on reload. u will get these packages.

---

### Post by nrwilk on 2006-08-28
Did you make sure to do a```
sudo aptitude update
```first?

If you did run an update first, make sure you have the universe repositories enabled.

Nothing against it, but if you use Automatix you will not learn about your system.  Plus, this is such an incredibly easy thing to do without automatix.

Once you enable universe repositories, just do a```
sudo aptitude install sun-java5-jre sun-java5-plugin sun-java5-jdk
```

and you're done.  The sun-java5-plugin package is the plugin for firefox, so it is optional.

---

### Post by kernelpanicked on 2006-08-28
> **true_friend said:**
> yup he is right. use automatix for such tasks.
or enable repsitories in synaptic first. synaptic is package manager Go to Settings> Repositories and check all of them then click on reload. u will get these packages.



OR, he could just do it the right way. Run the following command,

```

sudoedit /etc/apt/sources.list

``` 
Look for the line like this
```

#deb http://us.archive.ubuntu.com/ubuntu/ dapper universe 

``` 
Uncomment it and add multiverse
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

``` 
Update your apt sources and install the package.

Seriously, how does one go from noob to self-sustaining user, if everyone keeps giving them the cheap way out?

---

### Post by Sensei Eggwoah on 2006-08-28
Apt-get seems to work easy enough for me assuming I actually have the right repositories installed.  I could have sworn I had enabled the multiverse repositories.  I guess not.  Thanks guys.

Also, what exactly is the difference between apt-get and aptitude?

---

### Post by Sef on 2006-08-28
> Also, what exactly is the difference between apt-get and aptitude?

Aptitude is an updated apt-get.  The former will remove all the dependencies downloaded, while the latter will not.

---

### Post by catlett on 2006-08-28
Aysiu gives a good summary of apt-get and aptitude. [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)  It is a little confusing but aptitude has a graphical front end as well. just type ```
aptitude
``` in the terminal 
If you are a little comfortable with adding repos and using the command line, try the Dapper Guide. It walks you through setup of the most popular desktop features [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

