---
title: "Firefox Update"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-08
Just downloaded newest version (1.5) of Firefox for Linux.  Used the following in terminal:

sudo apt-get install firefox

When I run Firefox, still get the old version (v 1.07).  Do I need to uninstall old version first?

---

### Post by mostwanted on 2006-04-08
sudo apt-get install appname just installs the version of Firefox that is in the Ubuntu repositories, it's not a magical command that can install *any* application from *anywhere* on your harddisk :)

I suggest you download Automatix for installing Firefox 1.5. Try searching in this forum's search box for Automatix.

---

### Post by ncappel1 on 2006-04-08
I'm not positive if it is necessary to uninstall the old firefox, if you do it doesn't hurt anything.

Automatix is your best bet to get it done quickly and correctly. 

If you are really stubborn though, you can install it from source:
1) download the file from here: [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

2)cd to the directory where it is (or navigate to it with the file browser), then depackage it (extract the files into the directory). the command line for this would be ```
 $ cd /directory_the_tar_file_is_in
$ tar zxvf name_of_tar_file.tar.gz
```

3) then ```
cd /directory_where_the_files_are
./configure
make
make install
```

and that should be that, again, with automatix it is much easier, but both results will be the same. 

let us know how it turns out!

---

### Post by ncappel1 on 2006-04-08
i just remembered, for more detailed info on installing packages, I always refer people to these excellent guides: [http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

and in general: [http://www.linuxnewbieguide.org/](http://www.linuxnewbieguide.org/)

but of course, as always, the best help is in these forums ;)

---

### Post by Sef on 2006-04-08
Here's how to correctly install firefox 1.5 (from command line.)

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29")

Automatix is another solution if you have Breezy 5.10.

[http://ubuntuforums.org/showthread.php?t=138405]("http://ubuntuforums.org/showthread.php?t=138405")


> Do I need to uninstall old version first?

Do **NOT** uninstall firefox 1.07.  It will break numerous applications.

---

### Post by take_one on 2006-04-08
> 
3) then ```
cd /directory_where_the_files_are
./configure
make
make install
```


I was reading this and thought might be nice to update my firefox too and followed your instruction... my konsole however stuck on 
```

$ ./configure
bash: ./configure: No such file or directory

```

can you tell my why?

---

### Post by Sef on 2006-04-08
> can you tell my why?

Have you installed build-essential? If not, you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by aysiu on 2006-04-08
I don't think you ./configure Firefox.
It's a .tar.gz, but it's not built from source.

If you want a quick script to install it for you (and not a ton of other stuff), go here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

If you want a script that installs Firefox and a whole bunch of other stuff, use Automatix.

If you prefer to copy and paste commands, go here:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by landsg on 2006-04-08
Thanks.  I downloaded Automatix and that took care of Firefox.  One thing though.  Automatix hung up on installing one of the packages, so I canceled out and it disappeared.  Should I try to re-run it again to finish installing everything??

---

### Post by aysiu on 2006-04-08
[QUOTE=landsg]Should I try to re-run it again to finish installing everything??[/QUOTE] Couldn't hurt. When you try to install something that's already installed, it just tells you it's "the newest version already."

---

### Post by ncappel1 on 2006-04-09
sorry for the bogus info, ill try to explain myself better next time. :(

---

