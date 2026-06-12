---
title: "I need help installing Apache"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by AndrewEsther on 2008-04-05
Why can't installs be simple with this damned OS!?

I have tried, unsuccessfully, for the last 9 1/2 hours to install Apache on Ubuntu 7.1. I cannot waste anymore time on this, as I need to get this server up and running. I have never used Ubuntu, or any OS besides a MS product, to run anything. I thought I would give this a chance. I am now regretting it.

Why. In. The. World. is this so hard? Don't give me the speech that it isn't, because I have read about 50 tutorials that I google'd on how to do this, none of them make any sense, I don't understand why this "Synaptic" program won't just effing download and install what I am asking it to!?

Yes, I've downloaded every package I can find that has the word Apache in it, I've tried running the ./compile command, and it gives me the big middle finger every time. I even tried downloading the apache .tar.gz file directly from the apache website, and still nothing. whatever happened to double-clicking an icon and clicking yes and next a few times?

Please, I am begging you, help me. I am about to take a baseball bat to my computer and wholeheartedly embrace the soul-sucking power of microsoft once again just for the sheer ease of use.

:mad:

---

### Post by tamoneya on 2008-04-05
```
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```

place all of your html files or what have you in /var/www

---

### Post by JoshuaRL on 2008-04-05
And if you need to compile, you'll need the build essentials package:
```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by AndrewEsther on 2008-04-05
Alright, I ran all those commands... I still have 2 problems: where is the apache icon so I can actually run the program? and why won't Debian STAY selected to show in the Applications menu? I've heard that inside the Debian menu is where the elusive program icons reside... when I check it, I get nothing..... it sits there, checked, staring at me for a minute, then returns back to its un-checked state, as if to say HAHAHA! betch!

---

### Post by JoshuaRL on 2008-04-05
> **AndrewEsther said:**
> Alright, I ran all those commands... I still have 2 problems: where is the apache icon so I can actually run the program? and why won't Debian STAY selected to show in the Applications menu? I've heard that inside the Debian menu is where the elusive program icons reside... when I check it, I get nothing..... it sits there, checked, staring at me for a minute, then returns back to its un-checked state, as if to say HAHAHA! betch!

What are you talking about with the Debian menu?  Are you on Debian or Ubuntu?  If you want programs then go to the little Ubuntu Icon (if you're on normal Ubuntu and not Kubuntu or Xubuntu) in the top left and the applications are there.

Could you go through the basics of how you got your system up and running?  Did you install server first, or regular Ubuntu?  Did you do a minimal install or anything special?

---

### Post by AndrewEsther on 2008-04-05
I got the Ubuntu 7.10 desktop edition iso file, burned the image to a cdrw, hit restart with the cd in the drive, and followed all the install procedures as included in the ubuntu image.

And I read somewhere that I have to enable the Debian menu by right-clicking applications menu, selecting edit menus, and making it visible.

also, when I attempted to ./configure my downloaded apache files, I got:

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 1.2.12
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr


which I'm assuming means "get lost, idiot" in linux-speak

---

### Post by Ocxic on 2008-04-05
there is no icon for apache it's a server not a program, i would suggest that you install webmin to manage your server, it gives you a nice gui to work with.

---

### Post by AndrewEsther on 2008-04-05
Hmmm... probably... I've done this all before on my XP pro machine, and it all seemed to go so smooth... I installed apache, a server admin program, and an ftp program, and it was up and accessible in an hour or less...

Where can I find webmin? Should I search for it in Synaptic?

---

### Post by Doorslammer on 2008-04-05
```
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```

**place all of your html files or what have you in /var/www**
if you installed it this way then it's running 
open your browser  & [http://localhost](http://localhost)   or  [http://127.0.0.1/apache2-default/](http://127.0.0.1/apache2-default/) 
will bring up the default page

---

### Post by Doorslammer on 2008-04-05
> **AndrewEsther said:**
> I got the Ubuntu 7.10 desktop edition iso file, burned the image to a cdrw, hit restart with the cd in the drive, and followed all the install procedures as included in the ubuntu image.

And I read somewhere that I have to enable the Debian menu by right-clicking applications menu, selecting edit menus, and making it visible.

also, when I attempted to ./configure my downloaded apache files, I got:

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 1.2.12
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr


which I'm assuming means "get lost, idiot" in linux-speak
Debian menu ? sorry this is ubuntu not Debian
ubuntu is based on Debian  but ubuntu is it's own distro..

also, when I attempted to ./configure my downloaded apache files
why are you trying to /config ?  if you ran the  sudo apt-get install apache2  commands then it's already installed along with php . 
stop trying to built  it

---

### Post by tamoneya on 2008-04-05
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_Install_Webmin](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_Install_Webmin)

---

### Post by AndrewEsther on 2008-04-05
oh... alright then.... I just kept trying to do what all the tutorials told me to do and every time got no noticeable result or change... no asking for a restart, no icon, no "install successful" message... just endless lines of code that make little sense to me.

so, let's assume that apache did install correctly. where can I find other programs that I will inevitably need for my server?

---

### Post by Doorslammer on 2008-04-05
like what ? 
mysql stuff like that  synaptic package manager 
google is your friend 
did you go to the [http://localhost/apache2-default/](http://localhost/apache2-default/)

click on that link  if the page comes up with "it works" then apache is running

---

### Post by Doorslammer on 2008-04-05
> **AndrewEsther said:**
> oh... alright then.... I just kept trying to do what all the tutorials told me to do and every time got no noticeable result or change... no asking for a restart, no icon, no "install successful" message... just endless lines of code that make little sense to me.

so, let's assume that apache did install correctly. where can I find other programs that I will inevitably need for my server?

LOL first of all this is linux not windows ! with windows anything you install you have to restart ! linux is not that way !  everything in linux does not have an icon .
take your time  linux get some getting used to but once you get a handle on it you will not return to windows

---

### Post by azurepancake on 2008-04-06
I just setup Apache and I personally found it quite simple to install and configure. Here is what I did, step-by-step:

Open terminal: 
Applications - Accessories - Terminal

Type into the terminal, one line at a time:
[I]sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart[/I]

Alternative from terminal, you can use the "Synaptic Packet Manager" (System-Administration-Synaptic Packet Manager), search for Apache, right click on "Apache2" and click install then apply. Viola.

Apache is now installed and running. You should be able to type in your loop back address ([http://127.0.0.1](http://127.0.0.1)) into your browser and a page will appear saying "It works!".

Now, simply move all your HTML, style sheets, etc. into the "/var/www" directory. I had to change ownership and permissions for the "www" directory and it's contents. I'm not sure if this is normal, but if you get a permission error when attempting to load your website, then this is most likely the problem. You can fix this in just a few steps through terminal:

Load up terminal
Navigate to the /var directory
Type: sudo chown username /var
Type: sudo chmod ugo+rwx /var
Navigate into the /var/www directory
Type: sudo chown username *
Type: sudo chmod ugo+rwx *

I am sure there is a much faster way to do this and I am sure some of it is unnecessary, but I am new to Linux my self and this is the only way I know how to do it. You can configure Apache through terminal by typing into terminal: sudo nano /etc/apache2/httpd.conf which will bring up a text editor inside of the terminal.

---

