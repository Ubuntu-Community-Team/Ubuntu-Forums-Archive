---
title: "apt-mirror for ppc binaries"
date: 2007-06-21
forum: Apple PPC Users
---

### Post by johng4 on 2007-06-21
I've got a server at home that I use for caching most everything I can.  It has squid, dansguardian, and apt-mirror as its primary features.  All of them work beautifully.  However, on my network of 8 computers I have 2 PPC Ubuntu installations (well.. 3 when you add in the ps3).  Problem is I can't seem to find information on getting the powerpc-binaries on my mirror.

Any help?  Seeing as how my iMac is the slowest machine on my network, I could use it more than on my other machines.

---

### Post by atom on 2007-07-06
There are powerpc binaries in the main repository. If you're using apt-mirror just copy your lines and add -powerpc: 

deb-powerpc [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main main/debian-installer restricted restricted/debian-installer universe universe/debian-installer multiverse multiverse/debian-installer
deb-powerpc [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-powerpc [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

---

### Post by johng4 on 2007-07-08
Thanks.

My cache server took a dive on me, but once I get it back up and running I'll get those added in.  My home network is pretty evenly split at this point between PPC Ubuntu and 32bit Ubuntu.  

Hopefully I'll be replacing it with an X10 mac server which I'll happily put ubuntu ppc server on.  Should be a project in and of itself.  

The guy I'm getting the server from is promising me 4GB of RAM too. :)

---

### Post by atom on 2007-07-08
i'm mirroring ppc for ps3 as well. though, i'm attempting to set up a 4 console cluster. :)

---

### Post by ashruakkode on 2007-07-10
please help how can setup mirror in our local network

all clients and servers ubuntu

Thanks in advance
asharg

---

### Post by johng4 on 2007-07-10
Ok.. I hate posting tutorials in existing threads, but if its usefull I'll just recreate it, and hopefully this one will get a sticky unlike the kernel tutorial I made :(


_**Step 1: Setup your server **_
I did this on my cache server, which by its name implies that it was a dedicated server.  You can do this on a day-to-day machine, but I don't recommend it.  This uses a LOT of disk space, and resources initially.. so it renders the machine virtually unusable during the installation process.

**IF YOU DO NOT HAVE A LAMP INSTALLATION FOLLOW THIS PART OTHERWISE GO TO STEP 2**

First, get apache2...
*** If you have APTURL, click [here]("apt://apache2") for apache2. ***

```

$ sudo apt-get install apache2

```

The apache2 installation is pretty straight forward, you shouldn't have to touch anything further.  However, if you have a firewall on the machine you'll need to open up port 80 to allow outside machines to connect to what will be your cache server.

Its also important to setup a static IP for the machine serving as a mirror.  If you need assistance with that, post a reply to this and I'll post it.  Otherwise I'm assuming you know how to setup a static IP.  For the example of this tutorial we'll assume your static IP is 192.168.0.100.

_**Step 2: Install APT-Mirror**_
This is again a simple process...

** If you have APTURL click [here]("apt://apt-mirror") for apt-mirror. **
```

$ sudo apt-get install apt-mirror

```

Quick install, but now we need to configure it.  So in nano we'll edit our apt-mirror source list...
```

$ sudo nano /etc/apt/mirror.list

```

This will look familiar if you've ever manually edited your sources.list.  Here you define which repositories you mirror, and you add in any ubuntu repo out there that you want.

Here is a sample mirror.list file...
```

############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  
set nthreads     20
set tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu

```

**_Step 3: Mirroring_**
After saving the mirror.list file, its time to create the local repository.
**!!!WARNING!!!**
*The following step will make your computer and internet connection virtually unuseable for a great deal of time.  On 3MB DSL with full bandwidth, it took me about 18 hours to download the entire repository.  Be ready to not have an internet connection for some time.*
```

$ sudo apt-mirror -c apt-mirror

```

This will create your repository in /var/spool/apt-mirror/

**_Step 4: Cleaning up**_
Its probably a new day at this point, and now we need to finish up the repository mirror with some fine polish.

Lets clean up the repository of things we don't need..
```

$ sudo ./var/spool/apt-mirror/var/clean.sh

```

**_Step 5: Setting up HTTP Access to the Repo**_
Now, we setup apache to use the mirror that we just created in its hosting directories.
```

sudo ln -s /var/spool/apt-mirror/mirror/(the repo site you mirrored from)/ubuntu /var/www/ubuntu

```

Lets test this out by opening up a web browser, and typing in "http://localhost/ubuntu/"  there you should see a directory tree that looks like a fairly standard apt-get repository.  If you don't post a reply to this, as it will require some troubleshooting on the apache side of things.

**_Step 6: Setting up Cron for updating daily_**
Depending on how you like to set up cron, this can either be easy or a pain.. the way I see most suggested is this...
```

$ sudo nano /etc/cron.d/apt-mirror

```

And then enter this...
```

0 4     * * *   apt-mirror      /usr/bin/apt-mirror > /var/spool/apt-mirror/var/cron.log

```

That will update your repo at 4pm every day.  I personally created this entry in my crontab with the same settings, but thats me.  For the sake of simplicity, I suggest this method.

**_Setting your clients to use your repo_**
On your client machine, we need to add in the following source (assuming that these machines are on your network)...
```

$ sudo nano /etc/apt/sources.list

```

**OR**

Just add them in through the System > Administration > Software Sources > Third Party.

```

deb http://192.168.0.100/ubuntu main restricted universe multiverse
deb-src http://192.168.0.100/ubuntu main restricted universe multiverse

```

Now, open Synaptic, and reload your sources.  If you don't get an error, you're good to go.

If you do, post it here and I'll help you out.

---

