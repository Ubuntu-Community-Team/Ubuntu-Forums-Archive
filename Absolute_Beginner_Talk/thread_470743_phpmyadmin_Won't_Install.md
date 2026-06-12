---
title: "phpmyadmin Won't Install"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by -fred- on 2007-06-11
I setup the following to do some local developing:
- apache2
- php5
- mysql5
- phpmyadmin


my problem is in the phpmyadmin install.  when i go to run the setup script i get the "Open With/Save To Disk" window

any ideas as to why this is happening?

---

### Post by srt5 on 2007-06-11
Have you been trying to configure everything manually? I installed phpmyadmin last night in about 2 minutes by simply typing ```
sudo apt-get install phpmyadmin
``` into a terminal. Does this not work for you? If your more comfortable using Synaptic it should be in there also. You may need to include universe/multiverse repositories and refresh your package lists.

Hope this helps.

---

### Post by -fred- on 2007-06-11
i did sudo apt-get and that downloaded and extracted the packages just fine.  problem is when im trying to actually install the program by using the setup script, i get prompted with a download window for the setup.php file.  

i've never setup phpmyadmin before, but from what i read, running the setup script should walk me through a few steps to connect the program to mysql.

still not resolved

---

### Post by TriggerHappyChewie on 2007-06-11
What setup script?  It should create a link in the /var/www/ directory.  You should be able to access it like so:

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Put in your IP for localhost if you aren't on the server itself.

---

### Post by -fred- on 2007-06-11
its not that i can't access or find the directory.  when i do enter in the path... i get a download window asking to download the .php file instead of actually displaying that page

---

### Post by Cypher on 2007-06-11
You'll want to also do this:
```

sudo apt-get install libapache2-mod-php5

```
and then your .PHP files will start working, as opposed to asking you to download them.

---

### Post by -fred- on 2007-06-11
cypher,

thanks for the recommend, believe it or not i actually picked up that component and installed as well.  should i have to start or configure php to become active?

---

### Post by Cypher on 2007-06-11
Can you go to /etc/apache2/mods-enabled and see if "php5.conf" and "php5.load" exist there. If they do, you might want to restart Apache with "sudo /etc/init.d/apache2 restart" and see if things work any better..

---

### Post by -fred- on 2007-06-12
> **Cypher said:**
> Can you go to /etc/apache2/mods-enabled and see if "php5.conf" and "php5.load" exist there. If they do, you might want to restart Apache with "sudo /etc/init.d/apache2 restart" and see if things work any better..

ok i tried that and the problem is still happening.  i think part of the problem is that i have two installs of apache.
apache
apache2    

if i wanted to keep apache2 how do i get rid of the other installation of apache?

somehow i will get this to work.
-fred-

---

### Post by mdbarton on 2007-12-02
I have the same problem [http://localhost/phpmyadmin.index.php](http://localhost/phpmyadmin.index.php) downloads a file rather than executing the php script.  [http://localhost/info.php](http://localhost/info.php) runs fine.

---

### Post by ruibernardo on 2007-12-02
Please do not create links from /usr/shar/phpmyadmin to /var/www. That's why the problems happens. After you install phpmyadmin you just go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) even if there is no phpmyadmin directory in /var/www. If you created one, remove it.

When you install phpmyadmin (with "sudo apt-get install phpmyadmin" or another package manager) a new alias is created in /etc/apache2/conf.d/phpmyadmin.conf. That is why there is no /var/www/phpmyadmin directory and still phpmyadmin is working.

More info about this problem and the solution here in this thread: [phpmyadmin package does not install under /var/www]("http://ubuntuforums.org/showthread.php?t=591952") . That thread also gives you a solution on how to make phpmyadmin not accessible to the outside world.

---

### Post by mdbarton on 2007-12-03
Thanks epimeteo, however it does not matter if the symlink is there or not.  I still get a blank page on [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) tries to download the PHP file.  Why is it not executing the PHP?  I have php files under [http://localhost/](http://localhost/) that execute ok.

---

### Post by mdbarton on 2007-12-03
I can't execute any PHP files that have been installed in /usr/share/phpmyadmin
I have copyied my info.php file from /var/www/ to /usr/share/phpmyadmin and [http://localhost/phpmyadmin/info.php](http://localhost/phpmyadmin/info.php) works fine!  I can't figure out why the PHP files that have been installed in /usr/share/phpmyadmin don't...

---

### Post by ruibernardo on 2007-12-05
mdbarton, it seems that clearing the cache in Firefox and restarting it can solve that downloading problem.

---

### Post by mdbarton on 2007-12-06
Thanks epimeteo - I saw that advice when searching for a solution, tried it and it didn't work (unfortunately!).  I'm going to completely remove PHP, MySql, Apache and PHPMyAdmin, re-install and try again.

---

### Post by mdbarton on 2007-12-06
removed and purged the apache2, php5 and phpmyadmin packages, reinstalled and now it works.  I don't recall doing anything different to the first time I installed!

---

