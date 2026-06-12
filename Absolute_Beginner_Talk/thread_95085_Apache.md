---
title: "Apache"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-11-25
When I ran Windows, I set up my Apache server and could add files to it directly from a folder in C:/Program Files/Apache Group.  I would like to run Apache in Ubuntu as well.  I googled it and came up with a lot of websites about Apache, but not much about the basics (setting it up for the first time, adding files to the server, etc.).  Could someone tell me how to do so or direct me to a site that can?  Thanks, I appreciate it.

---

### Post by bfonseca on 2005-11-25
[QUOTE=apmcavoy]When I ran Windows, I set up my Apache server and could add files to it directly from a folder in C:/Program Files/Apache Group.  I would like to run Apache in Ubuntu as well.  I googled it and came up with a lot of websites about Apache, but not much about the basics (setting it up for the first time, adding files to the server, etc.).  Could someone tell me how to do so or direct me to a site that can?  Thanks, I appreciate it.[/QUOTE]

Hi, I just got my apache started and it is running great.  To get started follow these steps:

1. System ==> Administration ==> Synaptic Package Manager
inside of synaptic search for apache. once found check the appropriate boxes to   install apache(apache should be one of the boxes needed.

2. Once that is done,then apache chould be running. Inside the terminal type:
sudo /etc/init.d/apache stop

3. Copy over the html or htm files to /var/www/

4. sudo /etc/init.d/apache start

5. run which ever browser and type [http://localhost](http://localhost) or [http://(IPADDRESS](http://(IPADDRESS))

6. It should be running just fnie now. 

7. when updating the /var/www directory dont forget to: sudo /etc/init.d/apache stop and then when done: sudo /etc/init.d/apache start

For some reason when I try to make changes or update the website, while apache is running I have problems.  So now I stop and start it. (no more Problems):D 

Brian

---

### Post by bfonseca on 2005-11-25
Oh if you wanna import, ftp, or just mv the html, htm file(s), or folders you must do this as superuser (sudo)  Good Luck!
Brian

---

### Post by wsanders on 2005-11-25
First, run

```

sudo apt-get install apache2

```
This will install apache, when it's done you can open a browser and type in either [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) . 

Your web data is stored in /var/www . You can create a shortcut to this on your desktop by running:
```

cd ~/Desktop
ln -s /var/www "Apache Root"

``` 
(you can rename Apache Root to whatever you want the shortcut on your desktop to say.)

---

### Post by amcavoy on 2005-11-25
OK that worked well.  I have registered a static DNS address, does anyone know how I configure Apache with this?  Thanks again.

---

### Post by ubuntufella on 2005-11-25
[QUOTE=apmcavoy]OK that worked well.  I have registered a static DNS address, does anyone know how I configure Apache with this?  Thanks again.[/QUOTE]
I am a n00b, but I do use apache ([http://phoenixpc.ath.cx](http://phoenixpc.ath.cx)) and I find that not much configuration is needed to be done once it is setup. All you need to do is set up an account (which you have done as you said before) and get that staticd DNS to redirect to your computer's public IP address. If you are behind a firewall/router/NAT then you need to set up port forwarding fot HTTP TCP port 80. (If you ISP has blocked port 80, use 8080).

---

