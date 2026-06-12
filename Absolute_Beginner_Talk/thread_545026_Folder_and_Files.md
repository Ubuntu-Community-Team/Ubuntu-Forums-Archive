---
title: "Folder and Files"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-07
Ok, I have a real newbie question.  I used to use SuSE, but because  of a few reasons I got rid of it.

I am curious to know about folders and files.  I have a TON of music files that I need to put in a folder.  By the way, this is a new install and the first time I have used Ubuntu.  In SuSE I would log in as root, go to the /usr folder, create a folder for /music and grant full permissions to it.

I noticed that in Ubuntu there isn't a root?  I don't recall being asked for a root password.  su in the terminal doesn't work either.  

I guess the first question is: do I even need to put all my music/movie/pictures in the /usr directory?

Secondly, why isn't there an option to log in as root?  Why isn't there a second password config for su?

---

### Post by forestpixie on 2007-09-07
as far as music files go - i previously had put all mine in one directory - but in /home - they live on their own drive now.

there is a root account but it's disabled and you have to enable it - haven't been here long enough to worry about the difference in using sudo to accomplish what I want

---

### Post by ExSuSEusr on 2007-09-07
Ok...

The reason I asked is because, typically, the /home is on a different partition that isn't nearly as large as /usr...  Just wasn't sure.

I like this distro so far.  It's nice to find a good, solid Linux distro that doesn't require 4 days straight of configuring and trying to get things to "work."  I'm very impressed with it so far.

---

### Post by dickohead on 2007-09-07
In ubuntu you do root commands using the sudo command (super user do) eg:

sudo mkdir /music
sudo chmod 755 /music
sudo chown -R your-user-name-here /music
sudo chgrp -R your-group-here /music

Does that help?

Personally, I keep all of my music either in my /home/me/music folder or on a Samba file server so I can have it on my notebook when sitting outside :D

---

### Post by forestpixie on 2007-09-07
> The reason I asked is because, typically, the /home is on a different partition that isn't nearly as large as /usr

Depends how you set up to start with - I originally used 1 80Gb drive for linux - root had 8Gb, swap had 1 Gb the rest I gave to /home

---

### Post by ExSuSEusr on 2007-09-07
Ahh ok cool... thanks!

Just wait till I start asking about 3D acceleration enabling with an ATI Radeon 9600.  :)

And, wine!

---

