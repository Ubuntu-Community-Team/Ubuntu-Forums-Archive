---
title: "apache help please"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by uraliss on 2006-10-02
Hi folks,
I have installed apache on my server and it all seems to be working as i can access the apache welcome screen from another pc.
My question is where do I put my index.html file so that its the first page that is seen when i browse to my server?

Thanks in advance

---

### Post by Bachstelze on 2006-10-02
In /var/www, you can change it in Apache's config though.

---

### Post by dmizer on 2006-10-02
you put it in /var/www

you can also configure apache to look in a different folder if you like.

there's a fantastic howto for that here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F)

keep in mind, when you are putting files in /var/www, that you will need root rights (sudo).  this is a safety.  many people end up changing the permissions of /var/www to make it easier to transfer files etc, but i highly suggest you avoid this.

---

### Post by uraliss on 2006-10-26
Many thanks for your help on this. Problem now sorted

---

### Post by trunning on 2006-10-27
This is related to this problem too. I can get the apache page internally on my network. However when I am outside of the network I cannot access the page. I setup gotdns to put to the server and setup a filter to redirect port 80 to the server, but I am not able to see the page. What changes do I need to make on the linux box to make this happen.

Thanks

Trunning

---

### Post by j1mc on 2006-10-27
> **dmizer said:**
> you put it in /var/www

you can also configure apache to look in a different folder if you like.

there's a fantastic howto for that here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F)


I tried setting up an alias file per those instructions, but I must be missing something.  I'm getting the following error in my /var/log/apach2/error.log file.

```
[Fri Oct 27 20:05:34 2006] [error] [client 127.0.0.1] File does not exist: /var/www/home
```

My /etc/apache2/conf.d/alias file looks like this:
```
    Alias /localhost "/home/jim/www"

    <Directory "/home/jim/www">
  	Options Indexes FollowSymLinks
	AllowOverride All
	Order allow,deny
	Allow from all
    </Directory>
```

I've also tried "/home/jim/www" without the quotation marks around it, and I got the same results.

Any advice?  What am I missing?  Thanks!!

---

### Post by j1mc on 2006-10-27
> **j1mc said:**
> 
Any advice?  What am I missing?  Thanks!!

Nevermind . . . I found something that works in [this entry]("http://ubuntuforums.org/showthread.php?t=188125").  Thanks!!  :)

---
apache alias problem

---

### Post by halitech on 2006-10-27
> **trunning said:**
> This is related to this problem too. I can get the apache page internally on my network. However when I am outside of the network I cannot access the page. I setup gotdns to put to the server and setup a filter to redirect port 80 to the server, but I am not able to see the page. What changes do I need to make on the linux box to make this happen.

Thanks

Trunning

sounds more likely a problem either with the router or the ISP blocking port 80. see if you can ping the machine over the internet or load it by ip. maybe try setting it to load on port 8080 and see if it works.

---

