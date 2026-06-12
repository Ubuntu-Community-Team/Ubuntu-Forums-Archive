---
title: "Errors Setting up Ubuntu LAMP"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by djburke on 2006-06-01
I want am trying o set up a server for a personal website, so I installed Ubuntu on my old desktop. Before I found the wiki about setting it up, I had found info on another page and followed that([http://www.strdoc.net/ubuntu-apache-php-mysql-server/)](http://www.strdoc.net/ubuntu-apache-php-mysql-server/)). The only instructions there were to install apache2, ssh, php5, and mysql using the "sudo apt-get" command in the terminal. I didn't get any errors, but I didn't have any clue what to do next.

Then I fould the wiki ([https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)) and tried to follow those instructions. Everything works fine until I get to ther step "After Installing MySQL." The first step, installation of the database, appears to work fine. But the next step, "sudo mysql -u root" returns an error:
ERROR 1045: Access denied to user: 'root@localhost' (Using password:NO)

I checked the correct installation of Apache and php by going to [http://localhost](http://localhost) in firefox and I get errors there too. phpMyAdmin shows up as a link but does not allow me to log in. I typed in my username and password and again got error 1045:
#1045 - Access denied for user: 'dan@localhost' (Using password: YES)

So basically, I don't know who has access but it's not me. Do I need to uninstall and reinstall MySQL or something like that? I tried to do that in Synaptic, but I am a total noob, so I may have missed something?

Any help would be appreciated!

Dan

---

### Post by czambran on 2006-06-01
What happens when u go to: [http://localhost](http://localhost) ?

---

### Post by damianubuntu on 2006-06-01
You might find the shortest route is to uninstall apache, mysql,php etc from synaptic and then visit [www.apachefriends.org](www.apachefriends.org) (.com?) and get the full lampp suite from there.  It will install everything automatically configured, and I've never had any bother from it at all.

Having said that it is specifically configured for development rather than hosting, and so leaves a range of security issues open, but there are instructions for closing all the holes if you intend to deploy openly.

---

### Post by djburke on 2006-06-01
[QUOTE=czambran]What happens when u go to: [http://localhost](http://localhost) ?[/QUOTE]



When I go there I just see links for apache and for phpmyadmin. If I click on the apache link I get the regular apache homepage, saying that it is installed and ready fo info to be uploaded. When I click on phpmyadmin, I get a graphical login screen that doesn't let me log in, with the error I described in my original post.

---

### Post by Nequeo on 2006-06-01
> But the next step, "sudo mysql -u root" returns an error:
ERROR 1045: Access denied to user: 'root@localhost' (Using password:NO)

You probably need to type 'mysql -u root -p'. Last time I checked Ubuntu sets up the root MySQL user with a blank password. But you still need to tell mysql to log in with a password. Then if you get asked for a password, just leave it blank and hit enter.

The reason you can't log in to phpMyAdmin is that MySQL uses a seperate list of users to Ubuntu. You haven't created a 'dan' user yet, so you can't log in using 'dan'. But I bet if you tried to log in using 'root' and a blank password it would work.

---

### Post by Daremo on 2006-06-01
[QUOTE=czambran]What happens when u go to: [http://localhost](http://localhost) ?[/QUOTE]

try [http://localhost/apache2-default/](http://localhost/apache2-default/) . This is Ubuntu's default folder for Apache (not  just localhost like on other distros').

---

### Post by djburke on 2006-06-01
Thanks for the apachefriends link. I just reinstalled Ubuntu and grabbed that and it looks like I have everything I need. Great program.

---

### Post by Daremo on 2006-06-02
[QUOTE=djburke]Thanks for the apachefriends link. I just reinstalled Ubuntu and grabbed that and it looks like I have everything I need. Great program.[/QUOTE]

Apachefriends and XAMPP are great tools to have. However installing the "LAMPP" stack like this does not install apache or mysql as a service and as such other applications that you may want to use along with this may throw error messages - just somthing to keep in the back of your mind for future reference...

---

### Post by bluefrog on 2006-06-02
If you want an error less install of LAMP just grab a ubuntu sevrer cd and choose the menu "install LAMP" at boot time.

James

---

