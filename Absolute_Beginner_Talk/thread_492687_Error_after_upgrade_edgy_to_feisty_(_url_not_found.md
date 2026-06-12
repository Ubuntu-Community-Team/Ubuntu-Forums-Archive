---
title: "Error after upgrade edgy to feisty ( url not found )"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by pandusetiawan on 2007-07-05
I'm new member in this forum, anyway, i update the old server from dapper -> edgy (no problem) but when i upgrade edgy -> feisty, how come i can't go to my website url ? there's popup window telling me to save the file or open it, which is the file is the url of my website ? can anyone here help me find the answer?

i used /var/www/ as a root folder for the php file, but why i can't use it anymore? is it anything happen to my apache or php after the upgrade, how can i fix this?

thanks and best regards
pandu

---

### Post by scragar on 2007-07-05
I got that same error myself when PHP was not configured properly, apache didn't know how to proccess the file so itjust dumped it out for the browser, and without being told to render it as HTML firefox ask's you to download it.

try either re-installing PHP, or check your path to PHP in the apache config

---

### Post by pandusetiawan on 2007-07-05
sorry, i'm looking everywhere in google about your way, but it seems i can't get any luck to try the things, so i try to install php5 using apt-get install php5, i can use again my apache to show the php file, in this case i try to show the phpinfo.php (succeed! before installation -> failed), but still i cannot get any information why i can't get into my url web site, do you have any documentation or link to some thread that have the same issue ?

btw, thx scragar for your response,,, :)

best regards,
pandu:(

---

### Post by scragar on 2007-07-05
I just used the SPM to reinstall apache and PHP and it started working again, so I didn't create  any forum messages about it at the time...

if you try re-installing it and it doesn't work look into installing LAMP from apachefriends.org since that's a pre-configured PHP+MySQL apache server.

---

### Post by pandusetiawan on 2007-07-12
hi all, after i had a headache solving the problem, i ask google 'bout this and i mixed all the clue i've found, and here's what i've done :

1. I add this line to my httpd.conf (you need to change the directory in load module):
         LoadModule php5_module /usr/lib/apache2-extramodules/libphp5.so
         AddHandler php5-script .php
         AddType text/html .php

2. I edit all of my php.ini (i got two php.ini file), by uncomment the extension = mysql.so and the extension_dir= {i input the location of libphp5.so}

and there you go, my website become normal again,,,

PS : this is for the one who had installation problem on LAMP[hp5]

---

