---
title: "Installing Lastfm"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by quinlo on 2008-04-09
So I downloaded lastfm for linux... and now have a folder of files... how do I install them?  I know Im a newbie and quite dumb when it comes to this.

thanks for your help...

---

### Post by chewit on 2008-04-09
Its very easy to do, depending on the file you donwloaded. You want to download the Ubuntu package file, called deb. Once downloaded, just click the package and follow on-screen instructions.

---

### Post by atomkarinca on 2008-04-09
You can install it through terminal without the package:

```
sudo apt-get install lastfm
```

---

### Post by quinlo on 2008-04-09
i understand most programs you can DL right through the terminal.... I just want to try to get better at utlizing ubuntu... I am not sure what download deb means... where do I download this... synaptics?  Im sorry at how bad I am at this... thanks for your help... everyone is always so helpful... even with the kid that just "spilt the beans"

---

### Post by atomkarinca on 2008-04-09
You can get .deb files from various sites. But I suggest downloading only from trusted sites. [Getdeb]("http://getdeb.net") and [gnomefiles]("http://www.gnomefiles.org") are two examples of these sites. Once you download the deb file, double-click it and you will be prompted for your password and you're done.

Another way is to compile from the source. These files are mostly archive files: tar.gz, tar.bz2 etc. Once you download them, right-click and select "Extract here". Then open up a terminal, browse into that directory and type these:

```
./configure
make
sudo make install
```

These are valid most of the time. You can always double-check it from the INSTALL file in that directory.

Another way is to install from the repositories. You can use Add/Remove, Synaptic Package Manager or command-line. First to are GUI's that you can search a specific application. For the last one you can search with

```
sudo apt-cache search packagename
```

and install with

```
sudo apt-get install packagename
```

Just replace "packagename" with the application's name you're trying to install.

---

