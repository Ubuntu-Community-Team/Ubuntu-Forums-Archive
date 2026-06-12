---
title: "Apache Index"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by ErikaCruz on 2005-10-03
I can't find Index.php created.  I can only find Index.html.  Do I have to created?  The software I am installing asks me to make sure that the Apache's DirectoryIndex has a "index.php" and then says

DirectoryIndex index.php index.html index.html.var

Please any help will be appreciated.

---

### Post by dcraven on 2005-10-03
Yes. You may need to place your own index.php in the /var/www/ folder on your server if you want that page to be served. It could be that the application you are installing is not located in /var/www/ though (most things installed via apt are not). In this case, your best bet is to create an alias to the appropriate directory instead. This happens in your /etc/apache2/apach2.conf file. The following is my entry for Wordpress that I give you as an example:
```

Alias /blog "/usr/share/wordpress"
<Directory "/usr/share/wordpress">
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
</Directory>

```

As you can see, this actually has it's own DirectoryIndex setting. You also need to ensure that the appropriate permissions are given to the files being served. In most cases you can use something like "chown -R www-data:www-data /usr/share/wordpress" given the example above.

HTH,
~djc

---

### Post by ErikaCruz on 2005-10-04
Thanks,

The installation in /var/www is one of the things I don't understant.
I got the software from [http://arias.sourceforge.net/documentation.html](http://arias.sourceforge.net/documentation.html) .  
When it starts to explain the web server configuration it mention the Aria's **Installation** that may be in /var/www.  They did not explain how to install it.  I only donwloaded the software.  How do I install it?  Since I did not find any www folder in /var I created the folder and then I copied all the files I download to that folder but I am afraid that's not the installation right?
Thanks for your help

---

### Post by Mustard on 2005-10-04
Have you done tarball installations before?  That is an installation involving a tar.gz file.

---

### Post by ErikaCruz on 2005-10-04
No.  I just click on the link and then it saved it to my desktop.  So I did not download it properly or what do I have to do?  Thanks for your help.

---

### Post by Mustard on 2005-10-04
There is a HOW-TO in the Hoary Hedgehog Tips and tricks forum concerning tarball installations.  I'll try to find it.

Here is something to browse over while I'm looking. :D

[http://www.ubuntuforums.org/showthread.php?t=58343&highlight=tarball](http://www.ubuntuforums.org/showthread.php?t=58343&highlight=tarball)

You could also open up the tarball using gzip and have a look for a README file or an INSTALL file.  You can open them up and read the instructions given by the developer.

Ah..I just realised something actually.  There is an Aria package in synaptic package manager.  Have you used synaptic package manager before?  Its much simpler.

---

### Post by ErikaCruz on 2005-10-04
Thanks so much.

---

### Post by matthewv on 2005-10-04
If I understand things correctly, the tarball just needs to be extracted to DocumentRoot of your webserver, in this case /var/www. Then navigate to the setup page and a setup routine should run.

---

### Post by ErikaCruz on 2005-10-04
But the folder www does not exist under /var.  Do I have to create it or it means I have done something incorrectly.  I think the setup folder is only if I want to install it on windows.  They explain how to use it when they explain how to configure the SW on windows.

---

### Post by Mustard on 2005-10-04
Hmmm...I hope you try Synaptic before the tarball installation, ErikaCruz.  It will save you some grief if you're fairly new to it all.

> But the folder www does not exist under /var. Do I have to create it or it means I have done something incorrectly. I think the setup folder is only if I want to install it on windows. They explain how to use it when they explain how to configure the SW on windows.

If you havent run any './configure' or 'make' commands I think we can assume you havent installed anything yet.  You've just downloaded the file.

What you should try first though is to go to your System>>Administration>>Synaptic PackageManager program

In the package manager you can type 'aria' in the search field and it will bring the application up in your list of programs, if its available in your selected repositories.

Ah...hehehhe..scrap that....wrong Aria program...DOH!

Stick with the tarball installation I guess.

---

### Post by matthewv on 2005-10-04
The installation does not have to be in /var/www. It can be placed elsewhere, as long as the DocumentRoot variable in apache's httpd.conf file points to the location where you have placed aria. Ensure that the DirectoryIndex variable in httpd.conf contains index.php. Once your webserver is set up, navigate to [http://localhost/aria/setup/index.php](http://localhost/aria/setup/index.php) to run aria's setup "program".

---

### Post by matthewv on 2005-10-04
[QUOTE=Mustard]Hmmm...I hope you try Synaptic before the tarball installation, ErikaCruz.  It will save you some grief if you're fairly new to it all.



If you havent run any './configure' or 'make' commands I think we can assume you havent installed anything yet.  You've just downloaded the file.

What you should try first though is to go to your System>>Administration>>Synaptic PackageManager program[/QUOTE]

In addition to my previous post:
Unless I've misunderstood something, aria is written in PHP. This means that it does not have to be compiled, but rather served through a web server. As PHP is a server-side scripting language, the web server will parse the php file's upon request, outputting html.

---

### Post by Mustard on 2005-10-04
[QUOTE=matthewv]In addition to my previous post:
Unless I've misunderstood something, aria is written in PHP. This means that it does not have to be compiled, but rather served through a web server. As PHP is a server-side scripting language, the web server will parse the php file's upon request, outputting html.[/QUOTE]

Yeah..my bad...I was going off the rails with that one. :D  I realised it was a different aria program in synaptic.

---

### Post by ErikaCruz on 2005-10-04
Thanks Mustard I did it.

---

### Post by Mustard on 2005-10-04
Your doing better than me so far. :)

Don't forget matthewv. ;)

---

