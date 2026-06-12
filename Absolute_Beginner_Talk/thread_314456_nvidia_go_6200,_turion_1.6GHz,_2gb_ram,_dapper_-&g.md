---
title: "nvidia go 6200, turion 1.6GHz, 2gb ram, dapper -&gt; Beryl - Which How To?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-07
I am using Dapper and would like to install Beryl to get some more eye-candy and effects.

My graphics card is an Nvidia Go 6200, I have 2GB of ram, an AMD Turion 1.6GHz processor.

Using Automatix2 I installed the Nvidia drivers several weeks ago.

Some questions:

1. Can I use the drivers I currently have to use Beryl?

2. Which 'How To' should I follow to install Beryl? (Is there an official method for Dapper and Nvidia cards?).

3. What files do I need to backup in case something doesn't work out during all the setup and installation?

Thanks in advance.

---

### Post by PartisanEntity on 2006-12-07
bump

---

### Post by PartisanEntity on 2006-12-08
So I tried this How To:
[http://doc.gwos.org/index.php/BerylXglOnDapper](http://doc.gwos.org/index.php/BerylXglOnDapper)

However I got stuck where it says to do this:

```
This will open your sources.list in a gnome friendly editor, scroll to the bottom and add the following
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
```

```
Save the file, go back to your terminal and type this:
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - 
```

```
sudo apt-get update
```

This is where I am getting stuck because it appears the link to compiz is not working.

Has anyone managed to install Beryl for Dapper recently, if yes, how did you do it?

---

### Post by PartisanEntity on 2006-12-08
I also tried [this How To]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX") and got this:

```
me@ubuntunb:~$ wget http://ubuntu.beryl-project.org/quinn.key.asc -O - | sudo apt-key add -
--11:05:37--  http://ubuntu.beryl-project.org/quinn.key.asc
           => `-'
Resolving ubuntu.beryl-project.org... 80.77.247.17, 82.140.42.54
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:05:38 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.
```

---

### Post by ingo on 2006-12-08
nice monologue :)

you tried this?

[http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu)

---

### Post by PartisanEntity on 2006-12-09
Thanks :)

Yes, I tried that, its linked to in my post above yours.

---

### Post by 23meg on 2006-12-09
Note that if you have a Go6200 you'll almost certainly have to run beryl with the --force-aiglx option due to the black window bug.

---

### Post by PartisanEntity on 2006-12-09
Thanks for the info that's also what I was told at the Beryl forum.

Going back to one of my original questions:


3. What files do I need to backup in case something doesn't work out during all the setup and installation?

TIA.

---

### Post by ingo on 2006-12-09
at the risk of telling you something which you know already:

/etc/X11/xorg.conf

is the one and only - i usually do a backup straight after the install and another one after nvidia installation

---

### Post by PartisanEntity on 2006-12-09
Okay, so if I mess up the Beryl install, or if for some reason Beryl crashes my system, I can import the backed up xorg.conf and everything should work as before the Beryl install?

---

### Post by ingo on 2006-12-09
Yeah, you appear handy enough on the command line. It happened to me plenty of times :)

If X doesn't come up it is down to your xorg.conf all you have to do is reinstate your backup (via command line or midnight commander) and type startx or reboot.

You can do a dry run by screwing up your xorg.conf on purpose.

---

### Post by PartisanEntity on 2006-12-09
quick question, what does 'sudo apt-get dist-upgrade' do?

---

### Post by ingo on 2006-12-09
here is the man page
> dist-upgrade
              dist-upgrade in addition to performing the function of upgrade, also intelligently handles  changing  dependencies  with  new
              versions  of  packages;  apt-get  has a "smart" conflict resolution system, and it will attempt to upgrade the most important
              packages at the expense of less important ones if necessary. The /etc/apt/sources.list file contains a list of locations from
              which  to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for
              individual packages.


---

### Post by PartisanEntity on 2006-12-09
So if I were to enter this command into the terminal dapper would upgrade to edgy? (sorry if this is a silly question).

---

