---
title: "Deb Files"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-22
I know how to open Deb files.  I know to right click it and save it somewhere.  When I right click the deb file I do not have the option to save it anywhere.  
What should I do?

---

### Post by mlissner on 2007-03-22
If you're looking at a deb file online, download it. If it's already on your computer, double-click it to install it.

---

### Post by zeroo on 2007-03-22
How Do i Download it? When I just click it a source file comes up.

---

### Post by cowlip on 2007-03-22
Can you show us the URL you're trying to download it from?

---

### Post by zeroo on 2007-03-22
Its just envy

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by bodhi.zazen on 2007-03-22
May I ask what are you installing ?

First, if at all possible install from the repositories.

If you can not find the package you want, you may need to enable a few repositories.

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

If that does not do the trick, 

What I do is make a directory in your home directory src (for source)

The a directory in src <name_of_program>

Then save the .deb in /home/user_name/src/name_of_package

Then go to /home/user_name/src/name_of_package and either click on the deb file or in a terminal type :```
dpkg -i *.deb
```

Careful, if the deb is not specifically for Ubuntu you may get breakage ;)

---

### Post by cowlip on 2007-03-22
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb)

What happens when you right click -> Save target as, or just click on it?  You can't save to your desktop?  Can you take a screenshot of what happens and upload it to [http://imageshack.us](http://imageshack.us) ?

---

### Post by zeroo on 2007-03-22
When I click it I just get all this code.  And thats what I'm saying, I do not have that option when I right click it to save or copy it onto my desktop.

---

### Post by bodhi.zazen on 2007-03-22
You can di it all from the CLI :

```
mkdir -p ~/src/envy
cd ~/src/envy
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb
sudo dpkg -i envy*
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```

---

### Post by cowlip on 2007-03-22
> **zeroo said:**
> When I click it I just get all this code.  And thats what I'm saying, I do not have that option when I right click it to save or copy it onto my desktop.

sounds like a MIME type configuration issue on the server that's sending it as plain text?  After the code finishes downloading, you could go to file->save as and save it as a .deb file.

---

### Post by zeroo on 2007-03-22
When I use:
sudo apt-get install -f
To install dependencies nothing happens and It continues to ask for things like python and build-essential.

---

### Post by cowlip on 2007-03-22
"It continues to ask for things like python and build-essential"

Do you mean "sudo apt-get install -f" or envy itself is saying this when you try to run it?

If it's apt saying that, try to install all the dependancies it asks for (python, build-essential, maybe even ubuntu-desktop b/c I thought python was installed by default)

---

### Post by zeroo on 2007-03-22
Here's what I get when trying to Install from terminal. 


zero@snuggles:~/src/envy$ sudo dpkg -i envy*
Selecting previously deselected package envy.
(Reading database ... 79110 files and directories currently installed.)
Unpacking envy (from envy_0.9.1-0ubuntu3_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on python-gtk2; however:
  Package python-gtk2 is not installed.
 envy depends on python-glade2; however:
  Package python-glade2 is not installed.
 envy depends on python-vte; however:
  Package python-vte is not installed.
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on gksu; however:
  Package gksu is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

---

### Post by bodhi.zazen on 2007-03-22
Sorry, updated my post.

Look up, or continue with :

```
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```

Yes, I know there is a duplicate of commands, but that is what it takes :p

---

### Post by cowlip on 2007-03-22
can you try, (make sure all repositories in synaptic are enabled, and maybe even "non-free" ones)

sudo apt-get install gksu build-essential python-gtk2 python-glade2 python-vte fakeroot dh-make xserver-xorg-dev debhelper module-assistant

---

### Post by zeroo on 2007-03-22
[QUOTE=
```
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```
[/QUOTE]

When I do apt-get install nothing happens, it says that all the dependencies are installed.  When I try sudo dpkg -i envy* nothing happens.  Also Sudo envy -t, ..nothing happens.

---

### Post by bodhi.zazen on 2007-03-22
first, what directory are you in ? you should be in ~/src/envy

If not, 

cd ~/src/envy

Then use the -f flag :

sudo apt-get install **-f**
sudo dpkg -i envy*
sudo envy -t

Otherwise, what do you mean "nothing happens" ?

---

### Post by zeroo on 2007-03-22
> **bodhi.zazen said:**
> first, what directory are you in ? you should be in ~/src/envy

If not, 

cd ~/src/envy

Then use the -f flag :

sudo apt-get install **-f**
sudo dpkg -i envy*
sudo envy -t



I do sudo apt-get install and this is what comes up:

zero@snuggles:~/src/envy$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by bodhi.zazen on 2007-03-23
Looks good ....

Now what happens if you 

sudo dpkg -i envy*

??

You can also use tab completion :

sudo dpkg -i envy<tab>

---

### Post by zeroo on 2007-03-23
Finally I got sudo apt-get install -f after installing some updates.
The one thing that I still cant get though is module-assistant
I tried sudo apt-get install module-assistant
Yet had no luck.

Does anyone have a place to download Module-assistant or know how to?

---

### Post by cowlip on 2007-03-23
module-assistant is in universe

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=module-assistant&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=module-assistant&searchon=name&subword=1&version=all&release=all)

---

