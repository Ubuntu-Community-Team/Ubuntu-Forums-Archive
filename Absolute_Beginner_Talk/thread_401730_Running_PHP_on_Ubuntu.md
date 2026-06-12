---
title: "Running PHP on Ubuntu"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Matt Nichols on 2007-04-04
I am looking to be able to run PHP files that I have written in Firefox as if they were on my server. Though I know I can use Apache to do this (I got it to work swimmingly back when I was using Windows), I am yet oblivious as to how I may do this in Ubuntu. I have installed php4 with Apache, though I am not sure how to run/use it. I also am unsure of whether I am following the right path to my goal. Once I get this working, I ideally would not get the download dialog but the actual page when trying to view my PHP files in Firefox. Any wisdom would be appreciated...thanks.

---

### Post by amohanty on 2007-04-04
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

HTH
AM

---

### Post by Matt Nichols on 2007-04-12
So now I am still (with Apache & php4 running successfully) having the problem of Firefox not running my PHP script, just giving me the options of "downloading" it or running it with gedit. Any ideas? Thanks.

---

### Post by hyper_ch on 2007-04-12
Well, open a shell terminal and execute:

For PHP4
> 
sudo a2enmod php4


For PHP5
> 
sudo a2enmod php5


It might be that the php module isn't enabled yet.

---

