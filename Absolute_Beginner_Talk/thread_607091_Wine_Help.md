---
title: "Wine Help"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Veevose on 2007-11-08
Hello, can you please write me step by step how to install the latest version of Wine on my ubuntu, so i can play CSS,FIFA and other games.
Please just write step by step what do i have to do or write comands for terminal so i can install it. 
Thank you, mates, and sorry for i am such a bigginer with ubuntu.!

---

### Post by skymera on 2007-11-08
sudo apt-get install wine

but i suggest using the one from their site, 0.9.46 in older .deb archive.#

rather than the current 0/9/48

---

### Post by Veevose on 2007-11-08
hmm you know best. can you tell me why?

---

### Post by skymera on 2007-11-08
ive tried them, and none of my games worked in 0.9.48.

im sticking with 0.9.46 for now :)
works great

---

### Post by Veevose on 2007-11-08
ok, can you give the code for terminal for that version.? does it has doors also and .. it works good right? all i have to do is open the exe and it will open the file in wine right?

---

### Post by skymera on 2007-11-08
[www.winehq.org](www.winehq.org)

go to download > ubuntu > oldrer .deb archive

to open a file in wine

right click it, i prefer terminal

cd /directory/to/file

wine blah.exe

---

### Post by Veevose on 2007-11-09
hmm i got steam.msi.. but i dont know how to open it.. and i dont see the wine program anywhere.
Maybe i can do it from terminal but i dont know how:P

I got wine 0.9.44 i386 -Dev. ..

---

### Post by bithkits on 2007-11-09
Thank you so much skymera, this helped me too :)

---

### Post by Veevose on 2007-11-10
how can i install an msi. from terimal??
i need to install steam from treminal

---

### Post by Veevose on 2007-11-10
can you please help me out? i dont know how to install anything thru terminal. and i want to install 2 games..
pls help

---

### Post by voteforpedro36 on 2007-11-10
Go to the terminal. Find wherever your file is, and put this in the terminal:

cd /path/to/the/file 

So, if it was in /home/veevose, it would be:

cd /home/veevose

Then, once there, type in:

wine steam.msi

And post back the error messages if it gives one I suppose.

---

### Post by gigaferz on 2007-11-10
hello

what happens if you click on Applications, then Accesories?

Can you see any "wine" entry???

Also it should be right at the bottom once you click applications.

Lets assume you found it in accesories, you click on "wine File"
And youll have an "explorer " like window with  all your folders, just look for the exe you want to install, within that window....

---

### Post by gigaferz on 2007-11-10
what happened??

---

### Post by L Campbell on 2007-11-10
> **skymera said:**
> [www.winehq.org](www.winehq.org)

go to download > ubuntu > oldrer .deb archive

to open a file in wine

right click it, i prefer terminal

cd /directory/to/file

wine blah.exe

Hi, I saw your post here and tried to install WINE 

This is what I saw on their website:-

Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:-

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Gutsy (7.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.lis

OK, so it looks like a slam dunk but, unfortunately, after following these instructions and going back to Synaptic Package Manager, I still don't have WINE installed.

Am I missing something obvious here?

---

### Post by gigaferz on 2007-11-10
you only updated your repositories 

you did not install anything...you need to get a "deb" file...  wine.deb (or something like that)

then you just double click the "deb" file...
 and it will install .

look here... 

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by L Campbell on 2007-11-10
> **gigaferz said:**
> you only updated your repositories 

you did not install anything...you need to get a "deb" file...  wine.deb (or something like that)

then you just double click the "deb" file...
 and it will install .

look here... 

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Thanks very much, that looks like what I need.

Kind regards.

---

### Post by Veevose on 2007-11-13
> **voteforpedro36 said:**
> Go to the terminal. Find wherever your file is, and put this in the terminal:

cd /path/to/the/file 

So, if it was in /home/veevose, it would be:

cd /home/veevose

Then, once there, type in:

wine steam.msi

And post back the error messages if it gives one I suppose.

Ok. si the steaminstall.msi file is on my desktop.

now i go to terminal and type> cd/vivi/(my home folder)/desktop

and it gives me error messege: no such file or directory....
and i tried cd/vivi/desktop/steaminstall.msi >> and i dosent finds it .
I know i did something wroung but i dont know what...

---

### Post by PmDematagoda on 2007-11-13
> **Veevose said:**
> Ok. si the steaminstall.msi file is on my desktop.

now i go to terminal and type> cd/vivi/(my home folder)/desktop

and it gives me error messege: no such file or directory....
and i tried cd/vivi/desktop/steaminstall.msi >> and i dosent finds it .
I know i did something wroung but i dont know what...

First of all, the desktop folder's name starts with capital D, so the command would look like:-

```
cd /vivi/Desktop
```

And another thing, files such as .msi, .deb, .exe, .tar.gz, etc. cannot be navigated to using the cd(Change Directory) command, so if you used cd on File.deb then you will get the error you are talking about since it is **_not_** a directory.

---

### Post by meindian523 on 2007-11-13
you didn't give a space

cd /vivi/<your home folder>/Desktop

Then double click the Steam.msi file and it will open in Wine,if not,it will open up a Open With dialog,type this into the custom command section

```
wine
```

And for a complete guide to installing CSS,look here:
[URL="http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games"]
Installing CSS on Ubuntu with Wine[/URL]

edit: oops,sorry PmDematagoda,didn't mean to step on your toes....

---

### Post by PmDematagoda on 2007-11-13
> **meindian523 said:**
> 
edit: oops,sorry PmDematagoda,didn't mean to step on your toes....

No problem at all meindian523, the more help the merrier.:)

---

### Post by Veevose on 2007-11-13
allright pmd.. i added your msn to my contacts.. if you please talk to me for a second to solve this thing out.. cause i think something is missing here.. i mean what i am doing.. is not good..if you can please chat with me for like 2 minutes all will be ok and i would be very thankfull. thank you dude.. ( i am [email]eddysred@hotmail.com[/email])

---

