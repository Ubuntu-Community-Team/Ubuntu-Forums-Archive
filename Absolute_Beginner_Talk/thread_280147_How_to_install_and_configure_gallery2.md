---
title: "How to install and configure gallery2 ?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by gwolfman on 2006-10-19
Sorry if this seems too n00b, but I can't seem to figure it out.

I installed ubuntu-server 6.06.1 (dapper drake)and after I've prepared everything for gallery2, I ran the command 'sudo apt-get install gallery2' and everything installed fine.  I'm not sure what to do next.  I think I'm supposed to use my web browser (firefox) and go to the 'gallery2/install/' folder.  How am I supposed to do this when I don't (by default) have xwindows/gnome installed.  I'd prefer not to install this as it would take up lots of wasted space.  I know of lynx (text based web browser), but I think that would be all too complicated (especially for my first gallery/gallery2 install).  Any ideas?  Thanks!

Update:  gallery2 was installed in '/home/username/gallery2/'  Is that the correct location?  Shouldn't the gallery2 folder be in '/var/www/gallery2/'?

-GWolfman

---

### Post by dmizer on 2006-10-19
here's the guide i used: [http://easylinux.info/wiki/Ubuntu_dapper#Image_Gallery_Server](http://easylinux.info/wiki/Ubuntu_dapper#Image_Gallery_Server)

my gallery server is here so you can take a look and see what it's like: <removed>

be sure you read all the "read #" before you try to install.  just because you've done a server install doesn't always mean you have an active and installed web server.

your server should be on a local lan ... so just use another computer and browse to:

[url]http://server.ip.address.number/gallery/gallery2/install.php

---

### Post by gwolfman on 2006-10-19
The only thing different there was I didn't install phpmyadmin, but I got that up and running. There's a section of code and the last part says to run this command:
```
sudo sh /usr/share/gallery/configure.sh
```

Since this is gallery2, I looked in '/usr/share/gallery2/' but the file doesn't exist in that folder or the one stated above.

Any help would be greatly appreciated.  Thanks!

---

### Post by ca1vin on 2006-10-19
I take it you solved the problem of pointing a browser from another machine at [http://yourwebserver/gallery2](http://yourwebserver/gallery2) to do configuration?

Just ran the install myself, and the directory it installed for me was indeed /usr/share/gallery2.  You can, during installation, (and it recommends this) change this, and it suggests you change it to /home/username/gallery2.  Did you do this?

Putting the gallery2 directory in /usr/share/ seems to be an ubuntu customization thing, which makes the gallery configuration confusing, but I think its actually a good thing, and functionally equivalent to putting it in your home directory.  If your gallery2 folder was /var/www/ the config files would be in your web root, and configuration details would be open to public view.

So if your gallery2 folder is in /home/username/, you're fine.  If it's lost, maybe install again and stick with the default location or change as you wish.

That's assuming I know what I'm talking about - which has been known to happen on occasion.

---

### Post by gwolfman on 2006-10-19
> You can, during installation, (and it recommends this) change this, and it suggests you change it to /home/username/gallery2. Did you do this?
Yeah, I did that.

But let me backup a little.  I kept trying to run the install (through firefox) from my server which doesn't have xwindows installed.  I didn't think that I could run it from another machine.  Also, when I connected I couldn't see a folder called gallery2, so I thought I did something wrong.  Then I read something about aliases in apache2, and looked that up, and finally realized it was that (an alias).

Now one last question.  When I go to my webserver, [http://mywebsite/gallery2](http://mywebsite/gallery2) all works.  I have phpmyadmin installed, but I'd like to prevent all access to [http://mywebsite/phpmyadmin](http://mywebsite/phpmyadmin) OR to ONLY allow access to that from my private LAN and exclude all incoming internet access to that.  Any ideas?

---

### Post by dmizer on 2006-10-19
good to hear you got it all working.

to restrict access there are several things you can do, but we need to know about your network.

do you have a router?  if so, then your gallery will not be visible from the outside, only from your local lan.

but if the computer which is serving your gallery has a direct connection to your modem, then you will need to configure iptables.  to do this on a machine that does not have a gui, you will need to install webmin.  here is the best howto i've found for installing webmin: [http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin](http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin)

once you have webmin installed, you can configure iptables in a web interface (much like you did to install the gallery).

---

### Post by gwolfman on 2006-10-19
Sweet, thanks.  I'll look into that!  How come you say that if my server is behind a router that it can't be seen from outside my LAN?  Can't I just forward port 80 and everything work fine?

-GWolfman

---

### Post by dmizer on 2006-10-20
> **gwolfman said:**
> Can't I just forward port 80 and everything work fine?

yes, but you actually have to physically enable port 80 to be forwarded to your server in order for it to be visible.  and by default, your router should block that.

actually, i think i misunderstood.  i thought you didn't want anything on your server to be accessible from outside your lan.  but if you want your gallery to be viewable ouside your lan, you will also be exposing your phpmyadmin.  i think there's a way to bind phpmyadmin to localhost ... beyond that, i'm not too sure.  reading through phpmyadmin's config file might give you some clues.

btw: if you have a router, you won't need a firewall (your router is your firewall).  but webmin is still a handy tool to have on a server.

---

### Post by gwolfman on 2006-10-24
> "but if you want your gallery to be viewable ouside your lan, you will also be exposing your phpmyadmin. i think there's a way to bind phpmyadmin to localhost..."
That's exactly what I was refering to.  I only want gallery viewable outside my LAN, and NOT phpmyadmin.  I guess I could just uninstall it and then reinstall it when I need too, but I'd like to limit the access.  I didn't know what to look for before, but maybe the word "bind" (as you mentioned) added to my search will give me better results.  Thanks for you help!

---

### Post by Georges on 2007-01-05
to remove phpmyadmin from outside, best is just to set up ah .htaccess in the phpmyadmin folder to restrict it to be viewable by IP adresses you know to trust.
I won't for now search how to do this, but there is enough .htaccess documentation around the net, so you should figure it out.

---

### Post by JasonWalton on 2008-01-03
I've just gone through the trouble of installing on Ubunut 7.10 (Gutsy Gibbon), so I wrote a quick little tutorial:

[http://www.thedreaming.org/2008/01/03/gallery2-on-ubuntu/](http://www.thedreaming.org/2008/01/03/gallery2-on-ubuntu/)

This assumes you installed Ubuntu Server, so you already have Apache2, PHP, and MySQL all set up.

Hope that helps!

---

### Post by peter3 on 2008-05-10
It seems 8.04 may not be ready for Gallery2 yet.  
Here are some problems experienced on an attempted installation:
/etc/gallery2/config.php was a 0 size (empty) file.  
/etc/gallery2/apache.conf still had the first line commented out, so no alias existed.
After copying /usr/share/gallery2/install/config.php-template into the above config.php and removing the comment from the first line of apache.conf, the install proceeded well.  On the system check, a fatal error was generated by a limit of 16M for memory in php5.  I increased that to 64M and the rest of the install proceeded smoothly until I tried to start gallery2.  At that point the received this page on my browser:

Error
Error (ERROR_BAD_PARAMETER) :

    * in modules/core/classes/helpers/GalleryEntityHelper_simple.class at line 39 (GalleryCoreApi::error)
    * in modules/core/classes/GalleryCoreApi.class at line 2259 (GalleryEntityHelper_simple::loadEntitiesById)
    * in init.inc at line 185 (GalleryCoreApi::loadEntitiesById)
    * in main.php at line 180
    * in main.php at line 94
    * in main.php at line 83

and now I'm entirely stumped.  

Any help or comments would be greatly appreciated.

Peter

---

### Post by peter3 on 2008-05-10
OK, I made it work by re-running the install process with no changes.
This time when I finished, it all worked.
Please excuse the noise.

Peter

---

