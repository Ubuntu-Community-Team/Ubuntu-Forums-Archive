---
title: "Why can't my Ubuntu find any packages?!"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-10
First of all, Hi! ^^
 I'm a total Linux N00b and I am currently using the "Hoary Hedgehog" release of Ubuntu ( just ordered the "dapper drake" CD ).
And I am having EXTREME trouble installing the files I downloaded!

almost all programs except one or two just won't install....
And I installed them with the terminal...
reason is, I try to use synaptic to instal packages. I have this downloaded file in one of my desktop folders which I also extracted there. Now 89% of the time it won't install with the terminal ( though I also look at the documents inside to see if they have any special instructions. ), but when I use Synaptic and it's "search" feature, it never finds the files/packages!
Why? what am I doing wrong?! :confused:   :( 

I have usually have .tar.gz or .rpm files I try to install.

Any help greatly appreciated!

---

### Post by bodhi.zazen on 2006-10-10
> **Ryupower said:**
> First of all, Hi! ^^
 I'm a total Linux N00b and I am currently using the "Hoary Hedgehog" release of Ubuntu ( just ordered the "dapper drake" CD ).
And I am having EXTREME trouble installing the files I downloaded!

almost all programs except one or two just won't install....
And I installed them with the terminal...
reason is, I try to use synaptic to instal packages. I have this downloaded file in one of my desktop folders which I also extracted there. Now 89% of the time it won't install with the terminal ( though I also look at the documents inside to see if they have any special instructions. ), but when I use Synaptic and it's "search" feature, it never finds the files/packages!
Why? what am I doing wrong?! :confused:   :( 

I have usually have .tar.gz or .rpm files I try to install.

Any help greatly appreciated!


LOL :lol:

You will need alien for rpm packages:

[Alien](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

For your source code:```
cd
mkdir src
```

Move your .tar.gz to ~/src

Now extract the files.

cd into the new directory (cd ~/src/name_of_program)

```
aptitude update && aptitude install checkinstall
./configure
make
sudo checkinstall
```

---

### Post by CatKiller on 2006-10-10
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Ryupower on 2006-10-10
> LOL

You will need alien for rpm packages:

Alien

For your source code:
Code:

cd mkdir src

Move your .tar.gz to ~/src

Now extract the files.

cd into the new directory (cd ~/src/name_of_program)

Code:

aptitude update && aptitude install checkinstall ./configure make sudo checkinstall

Thanks! I got more questions:

1. I got Alien, but why doesn't it turn the .rpm file into a .deb file? Or atleast it looks like that, since all it seems to do is open the archive...( the last time I tried, forgot how the code went...)
is there any code I'm missing?

2.It never seems to "make" anything, it always says that there is no target file specified, or that there is no directory by the ./configure.  

> How to install ANYTHING in Ubuntu.
2. Thank you for the user guide,:)
 but I already found that a few days ago,the first thing I found on this whole issue. :)
But the tar.gz thing never works.
And the install instructions haven't worked yet either. maybe I'm missing a sepcial program or something?


:confused:  :(

---

### Post by bodhi.zazen on 2006-10-10
~ is short hand for /home/user_name

When I install from source, I keep the origional code in ~/src.

I would keep the .rpm and .tar.gz both in ~/src for future referance.

As far you other questions we would have to take them one at a time.

With the rpm/alien coyp (from the terminal) the output of:```
ls
sudo alien -k name-of-rpm-file.rpm
```

With the .tar.gz can you provide an output ls```
cd name_or_tar
ls
```

---

### Post by Ryupower on 2006-10-10
OK, this time, it actually did something with ./configure:

[email]root@DURONubuntu:/home/claudia/Desktop/programs/bochs-2.3.tar.gz[/email]_FILES/bochs-2.3 # ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking if you are configuring for another platform... no
checking for standard CFLAGS on this platform...
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
[email]root@DURONubuntu:/home/claudia/Desktop/programs/bochs-2.3.tar.gz[/email]_FILES/bochs-2.3 #

HUH?! O_o;;

---

### Post by Ryupower on 2006-10-10
> **bodhi.zazen said:**
> ~ is short hand for /home/user_name

When I install from source, I keep the origional code in ~/src.

I would keep the .rpm and .tar.gz both in ~/src for future referance.

As far you other questions we would have to take them one at a time.

With the rpm/alien coyp (from the terminal) the output of:```
ls
sudo alien -k name-of-rpm-file.rpm
```

With the .tar.gz can you provide an output ls```
cd name_or_tar
ls
```

WOW. it says it generated a .deb file!


root@DURONubuntu:/home/claudia # sudo alien -k /home/claudia/Desktop/programs/bochs-2.3-1.i586.rpm
bochs_2.3-1_i386.deb generated

I turned tried the Package manager but it still won't find it. :'(
is there anything I have to add to the above code? What am I doing wrong now?

---

### Post by mssever on 2006-10-10
You need the package build-essential before you can compile. Configure says you don't have gcc, the compiler. build-essential will provide that, as well as make and other essential tools.

---

### Post by mssever on 2006-10-10
> **Ryupower said:**
> I turned tried the Package manager but it still won't find it. :'(
is there anything I have to add to the above code? What am I doing wrong now?

The package manager isn't for locally-generated files. Either: doubleclick the deb's icon, or type ```
sudo dpkg -i deb_file_name.deb
```

---

### Post by CatKiller on 2006-10-10
> **Ryupower said:**
> WOW. it says it generated a .deb file!

I turned tried the Package manager but it still won't find it. :'(
is there anything I have to add to the above code? What am I doing wrong now?

You can just double-click on it to install it, or use ```
sudo dpkg -i <*packagename.deb*>
``` as it says in that guide.

> **Ryupower said:**
> But the tar.gz thing never works.
And the install instructions haven't worked yet either. maybe I'm missing a sepcial program or something?

Yes. You'll need some essential build tools. They are called build-essential. You can install them through Synaptic. As it says in that guide.

> **Ryupower said:**
> checking for gcc... no

See above.

---

### Post by Delkster on 2006-10-10
Generally, it would be a good idea to search for the packages in the Ubuntu [repositories](https://wiki.ubuntu.com/Repositories) (accessible via Add/Remove Applications and Synaptic) before trying to get them directly from the websites of each individual project.

In Linux in general, and even more so in Ubuntu, most of the software you'll need is supplied by the OS distributor. It's just not installed by default. You can find most stuff you'll want in Synaptic and its friends. Only a small part of all that software is officially supported by Ubuntu, though, and in order to install the unofficial, community-maintained packages, you'll need the [universe repository enabled](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096).

For example Bochs is available in the repositories (in `universe'), so if you want to install it, a good way of doing that would be:

1. Enable the universe repository
2. Search for `bochs' in Synaptic

If, for some specific reason, you need a different version than what's available in the Ubuntu repositories, that's another matter, but usually that's the way to go.

---

### Post by dannyboy79 on 2006-10-10
> **Ryupower said:**
> WOW. it says it generated a .deb file!


root@DURONubuntu:/home/claudia # sudo alien -k /home/claudia/Desktop/programs/bochs-2.3-1.i586.rpm
bochs_2.3-1_i386.deb generated

I turned tried the Package manager but it still won't find it. :'(
is there anything I have to add to the above code? What am I doing wrong now?


after you create the .deb you don't need to go to synaptic and try to find the package! it seems as though you are confussed and must not have read over the "Install anything in Ubuntu" page very well. WHen you use synaptic it goes online and looks within the repos that are in your sources.list and if it finds the package there on the repos website then it''ll donwload it and install it. if you can't find what you want in synaptic, then you can either use .deb's that you downlaod or in your case downlaod a .rpm and change it to a .deb and install it from there. NOTE: sometimes changing rpm's to deb's doesn't work! If you want to install a .deb, all you have to do is simply double click on it from within nautilus or you can do dpkg -i filename.deb  from the terminal. or if you want to install from .tar.gz if the previous options aren't available you can do
For a GZipped tarball: tar –zxvf filename.tar.gz (or filename.tgz) 
For a BZipped tarball: tar jzvf filename.tar.bz (or filename.tbz) 
./configure 
make 
(as root) make install 
from a terminal. I just don't think you have a great understanding on how you install stuff in linux. I would strongly suggest you read this link and you'll learn whole lot! Also if you read some peoples commments at that link, you'll find more great links explaining stuff. 

.deb or .rpm and from source: [http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/](http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/)

good luck! i have been using linux for about 6 months and until I read a lot of website about linux basics I was lost like you are!


wow, 4 posts before i could get this off, you guys are quick!

---

### Post by Ryupower on 2006-10-10
> **mssever said:**
> The package manager isn't for locally-generated files. Either: doubleclick the deb's icon, or type ```
sudo dpkg -i deb_file_name.deb
```

WOW!!! O_O
it's actually doing something!

root@DURONubuntu:/home/claudia # sudo dpkg -i /home/claudia/Desktop/programs/bochs_2.3-1_i386.deb
Selecting previously deselected package bochs.
(Reading database ... 58378 files and directories currently installed.)
Unpacking bochs (from .../programs/bochs_2.3-1_i386.deb) ...
Setting up bochs (2.3-1) ...

root@DURONubuntu:/home/claudia #


now what?

> You need the package build-essential before you can compile. Configure says you don't have gcc, the compiler. build-essential will provide that, as well as make and other essential tools.
ah thanks! and where can one find this?

---

### Post by dannyboy79 on 2006-10-10
> **Ryupower said:**
> WOW!!! O_O
it's actually doing something!

root@DURONubuntu:/home/claudia # sudo dpkg -i /home/claudia/Desktop/programs/bochs_2.3-1_i386.deb
Selecting previously deselected package bochs.
(Reading database ... 58378 files and directories currently installed.)
Unpacking bochs (from .../programs/bochs_2.3-1_i386.deb) ...
Setting up bochs (2.3-1) ...



root@DURONubuntu:/home/claudia #


now what?


ah thanks! and where can one find this?


sudo aptitude install build-essential 

if that's not it, go to synaptic and search for build or essential and you should find it and install it

what do you mean now what, it's installed. if it's not in your menu you can envoke it by typing in bochs in a terminal.

---

### Post by bodhi.zazen on 2006-10-10
Nice.

You generally need to log-out and then back in to see changes in the menu.

---

### Post by Ryupower on 2006-10-10
Thank y'all! For having such patience with me! ( now THAT must take some effort. ) :D 
Now I can be happy. :D 
God bless. :)

---

### Post by dannyboy79 on 2006-10-10
> **Ryupower said:**
> Thank y'all! For having such patience with me! ( now THAT must take some effort. ) :D 
Now I can be happy. :D 
God bless. :)

just because you have this issue solved doesn't mean you don't have to read the links i posted. your homework will be to read the entire post and there'll be a quiz tomorrow! HA HA I am glad you got it worked out. I seriously hope you read some of that about installing the different things and how Linux works.

---

### Post by Ryupower on 2006-10-10
> **dannyboy79 said:**
> just because you have this issue solved doesn't mean you don't have to read the links i posted. your homework will be to read the entire post and there'll be a quiz tomorrow! HA HA I am glad you got it worked out. I seriously hope you read some of that about installing the different things and how Linux works.
AAAAAAAAAAAAAAAH!! HOMEWORK! XD
Yeah, I printed it out before and have on my dest most of the time. 
thankie

---

