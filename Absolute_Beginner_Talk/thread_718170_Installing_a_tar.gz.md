---
title: "Installing a tar.gz"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2008-03-07
I just downloaded Songbird as a tar.gz file. I downloaded it to my desktop but extracted it to my home. What do I do from here to finish the installation? Any help is appreciated

---

### Post by DSn0wMan on 2008-03-07
The following link is a high level guide to installing from source in Ubuntu

[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

---

### Post by Pap3r on 2008-03-07
The easiest way to install a tar.gz file is to go into the console, and cd to where it is.  You then type ```
tar **xzvf** nameofyourfile.tar.gz
```
The bold is the extract command, for tar.bz2 files it would be **xjf**.

This will create a folder for your file, cd to that folder, and type ```
./configure
```It will configure itself.  (NOTE:  Some files do not need to be configured, and only the next steps are necessary)

The last two steps are the easiest.  After ./configure has finished, type ```
make
``` Once make has finished, type ```
sudo make install
``` Sudo means that you will be given Super User privileges for this command, type your password and hit enter.  A Super User (su) is like a Windows administrator, or on linux, the root user.  

Once it finishes that, your file has been installed.  Sometimes other files, are necessary for a successful installation of a file, if this happens you will have to install those dependencies to make the file you want to install work.  Many times the necessary files are called libraries, and it's usually possible to find them in the Synaptic Package Manager (Located in the System Tab -> Administrator -> Synaptec)  If not, google or just look around the net for them, and repeat those steps above.

---

### Post by gustasonfrever on 2008-03-07
How do you "cd" to a file?

---

### Post by jken146 on 2008-03-07
cd stands for change directory.  You type ```
cd path/to/the/directory/you/wantToChange/to/
```

For example, ```
cd /usr/bin
```puts you in /usr/bin.

```
cd ~/
```puts you in your user's home directory.  If you're already in that directory, ```
cd .gnome
```puts you in the directory /home/yourUserName/.gnome

```
pwd
```tells you where you are.

---

### Post by bodhi.zazen on 2008-03-07
For a few suggestions see :

[http://ubuntuforums.org/showpost.php?p=4473168&postcount=5](http://ubuntuforums.org/showpost.php?p=4473168&postcount=5)

---

### Post by Pap3r on 2008-03-07
cd means change directory, you type that in the console, followed by the folder you want to go to.  I.e. if I wanted to change where I was in the console to the Desktop, I would type ```
cd Desktop
```cd is case sensitive, so make sure you have typed it correctly or you won't be able to change the working directory.  You can drag files into the console to get the paths to them, it's much easier than writing it out, just make sure you have cd before it when you hit enter, otherwise it won't work.

---

### Post by gustasonfrever on 2008-03-07
This is what I did
norgren@norgren-laptop:~$ tar xzvf Songbird_0.4_linux-i686.tar.gz
norgren@norgren-laptop:~$ cd Songbird
norgren@norgren-laptop:~/Songbird$ ./configure

Then I get this:

norgren@norgren-laptop:~$ cd Songbird
norgren@norgren-laptop:~/Songbird$ ./configure
bash: ./configure: No such file or directory
norgren@norgren-laptop:~/Songbird$ 

what am I doing wrong?

---

### Post by Pap3r on 2008-03-07
You are doing nothing wrong.  It seems as thought Songbird does not come with a ./configure file, try running ```
make
``` instead and see what that does.

---

### Post by gustasonfrever on 2008-03-07
norgren@norgren-laptop:~/Songbird$ make
make: *** No targets specified and no makefile found.  Stop.

I have no idea why this isn't working

---

### Post by Pap3r on 2008-03-07
Type ```
ls -a
``` and paste what comes up in here.

---

### Post by DSn0wMan on 2008-03-07
I used the script from the below url to install songbird. No fuss no muss.

[https://help.ubuntu.com/community/Songbird#head-25861b3066dba454799a78e77edbe7ccfe8978e1](https://help.ubuntu.com/community/Songbird#head-25861b3066dba454799a78e77edbe7ccfe8978e1)

---

### Post by gustasonfrever on 2008-03-07
I tried using this and it worked but it was only version .25 and i need the latest .40 build

wget -c [http://www.linuxmint.com/repository/cassandra/songbird_0.2.5.1_i386.deb](http://www.linuxmint.com/repository/cassandra/songbird_0.2.5.1_i386.deb) 
sudo dpkg -i songbird_0.2.5.1_i386.deb
sudo ln -s /usr/lib/songbird/Songbird /usr/bin/songbird

Is there anyway to modify this to work with the newest version?

---

### Post by PmDematagoda on 2008-03-07
I have used Songbird and the way of using is really simple, and there is no installation involved.

Just execute the songbird file with:-
```
sh songbird
```

---

### Post by Wylkar on 2008-03-07
When I installed the Songbird folder there was a executable file in it, and running that started Songbird. (I downloaded the Songbird folder from their site [http://www.songbirdnest.com/](http://www.songbirdnest.com/))

---

### Post by gustasonfrever on 2008-03-07
how do you execute the songbird file? do I need to cd the file first?

---

### Post by Wylkar on 2008-03-07
I had just downloaded the file to my desktop and opened it with my file browser and the executable was in it.

---

### Post by PmDematagoda on 2008-03-07
Yes, cd to the folder containing the file(it is in the main folder) and execute it.

---

### Post by gustasonfrever on 2008-03-07
Right, well its still not working

this is what I did

norgren@norgren-laptop:~$ cd Songbird
norgren@norgren-laptop:~/Songbird$ sh Songbird
sh: Can't open Songbird

Why is it telling me it can't open songbird?

---

### Post by Tatty on 2008-03-07
try ```
./Songbird
```

---

### Post by gustasonfrever on 2008-03-08
Thats not helping either, this is what I get:

norgren@norgren-laptop:~$ ./Songbird
bash: ./Songbird: is a directory
norgren@norgren-laptop:~$ cd Songbird
norgren@norgren-laptop:~/Songbird$ ./Songbird
bash: ./Songbird: No such file or directory

Anymore ideas?

---

### Post by lbarnes on 2008-03-08
guys, it's so friggin easy
all you do is open synaptic, click reload, and search for songbird
it's the latest 4.0 version and it installs it in 5 seconds

that's what i did, but it's still too buggy 
may wanna wait till it's version 1.0

---

### Post by lbarnes on 2008-03-08
btw, i make it a habit to always
use synaptic first for anything i'm looking for
just be sure to hit reload EVERY time you look for something

---

### Post by Shazaam on 2008-03-08
> **gustasonfrever said:**
> Thats not helping either, this is what I get:

norgren@norgren-laptop:~$ ./Songbird
bash: ./Songbird: is a directory
norgren@norgren-laptop:~$ cd Songbird
norgren@norgren-laptop:~/Songbird$ ./Songbird
bash: ./Songbird: No such file or directory

Anymore ideas?

You forgot the sh.

---

### Post by gustasonfrever on 2008-03-08
I just tried that and when I hit update and then searched for Songbird the only version present was 0.2.5

Then I tried putting the sh before the command and this is what I got

norgren@norgren-laptop:~$ cd Songbird
norgren@norgren-laptop:~/Songbird$ sh ./Songbird
sh: Can't open ./Songbird
norgren@norgren-laptop:~/Songbird$ sh ./Songbird
sh: Can't open ./Songbird
norgren@norgren-laptop:~/Songbird$

---

### Post by Pap3r on 2008-03-08
when you did sh, did you try both Songbird and songbird?  Case matters.

---

### Post by lbarnes on 2008-03-08
ok, here's the second easiest way

[http://www.getdeb.net/download/1894/0]("http://www.getdeb.net/download/1894/0")

---

### Post by gustasonfrever on 2008-03-08
Yes I tried both
I've also just tried clicking on the executable icon in the folder which opens Songbird and allows me to use it but doesn't install it. And Synaptec package manager does NOT have the latest Songbird.
This is fairly frustrating, I'm not quiet sure what to do

---

### Post by lbarnes on 2008-03-08
just click on the link above you and hit open

---

### Post by gustasonfrever on 2008-03-08
Well that did it. Thanks a lot

---

### Post by Ecclesia on 2008-03-08
If you just downloaded the standard package off the site it's a binary and doesn't need to be compiled.  Just unpack it and double click on "songbird" executable to run it (of course you can also add it to your application menu, if you choose).

I'd love to see this as an official package in the Ubuntu repositories.  Anyone know if there are problems associated with running binaries like this?

---

### Post by lbarnes on 2008-03-08
i do remember having to add a launcher icon to the applications menu
just right click on applications and select edit menus and choose sound & video
since it's a media player, and find your exe in usr/lib/songbird

---

### Post by lbarnes on 2008-03-08
you're welcome, keep in mind this is still total beta software
i had major problems with songbird, because of the 20,000+ songs
i loaded into it.  it may work better with a much smaller library

if you find the bugs too frustrating, i found banshee to be very good
albeit not as pretty

---

### Post by timjohn7 on 2008-03-10
As an almost converted noob, I am still missing something regarding tarball installations.  I have also searched numerous posts and other links and am happy with ./configure, make and install.

I have just downloaded Spicebird from their website.
Extracted the tar to a directory.
Run ./configure and received an error message "No such file or directory"
Run make and got a similar message.
The directory listing is

tim@tim-laptop:~/Downloads/Spicebird/spicebird-beta$ ls
application.ini     js              libprldap60.so          platform.ini
chrome              libfreebl3.chk  libsmime3.so            README.txt
components          libfreebl3.so   libsoftokn3.chk         removed-files
crashreporter       libldap60.so    libsoftokn3.so          res
crashreporter.ini   libldif60.so    libsqlite3.so           run-mozilla.sh
defaults            libmozjs.so     libssl3.so              spicebird
dependentlibs.list  libnspr4.so     libxpcom_core.so        spicebird-bin
dictionaries        libnss3.so      libxpcom.so             updater
extensions          libnssckbi.so   libxpistub.so           updater.ini
greprefs            libnssdbm3.so   license.html            updates
icons               libplc4.so      modules                 xpicleanup
isp                 libplds4.so     mozilla-xremote-client

Can someone please explain in humanspeak the steps I should take to install this app?

It's not available through Synaptic nor Add/Remove, which I am quite happy with using.and the README.TXT is not helpful at all.

Apologies for childlike question, and I'm sure the answer is quite simple, but a lack of knowledge and experience makes this frustrating.

Based on the number of queries regarding installation of downloaded software from ex-Windoze users, surely a small GUI app to automate the installation process (a la Add/Remove) but to use for downloaded files would make for a VERY popular utility and ease the Win-Ubuntu transition?

---

### Post by angry_johnnie on 2008-03-10
Regarding spicebird, did you take a look at this?

[http://www.spicebird.com/en-US/Install_Linux](http://www.spicebird.com/en-US/Install_Linux)

---

### Post by timjohn7 on 2008-03-10
> **angry_johnnie said:**
> Regarding spicebird, did you take a look at this?

[http://www.spicebird.com/en-US/Install_Linux](http://www.spicebird.com/en-US/Install_Linux)

Hi,
Yes I did and got Spicebird running that way.  This method doesn't add it to the Applications list though, which is what i meant by install.

Thanks for the pointer though.

---

### Post by angry_johnnie on 2008-03-11
right click on the menu and choose 'edit menus',   Then choose the submenu where you want spicebird to be, and click on the 'new item' button.   Then you can add spicebird manually.

---

### Post by timjohn7 on 2008-03-11
Thanks very much... boy, do I feel stupid!

---

