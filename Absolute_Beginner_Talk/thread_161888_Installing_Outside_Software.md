---
title: "Installing Outside Software"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by gsail11 on 2006-04-17
Hi, I recently installed Ubuntu, and overall I have been quite impressed. I find it superior to windows in nearly every aspect, and I am very happy with the free software, and other handy features. One problem, however, has been driving me absolutely mad. Although I consider myself to be at least moderately computer savvy for a high school student, I have found myself completely incapable of installing a "linux" program that is not endorsed (or maybe recognised would be a better word) by Ubuntu. By this I mean that I have not been able to install a program that isn't in the "Synaptic" program list. Two examples of programs I have made weak attempts at installing are the "N" game at [http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html) and frostwire at [http://www.frostwire.com/static/downloads.html](http://www.frostwire.com/static/downloads.html). Both sites offer only a link with no instructions, and at Ubuntu resource areas (OS help, tutorials, wiki, etc.) all I have found are instructions for using synaptic, or comparable methods. I am fairly sure that these programs should work, because a friend of mine said he had "N" on his Ubuntu, and the frostwire link specifically says "Debian/Ubuntu". My question is if anyone knows how I can install this or other "outside" software. I am not sure if I am missing something that should be obvious, or if there is a complicated series of steps, or if Ubuntu is completely incapable of installing programs that haven't first been looked over by the Ubuntu staff. Any help in installing the two specific programs that I cited earlier is appreciated, because that should provide me with insight in installing other programs.

By the way. I am using Ubuntu version 5.10, if that makes a difference.

Thanks in advance! :D

---

### Post by aktiwers on 2006-04-18
You could try 
[http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://ubuntuforums.org/showthread.php?t=138405&highlight=automatix)
And
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

They both auto installs a lot of programs you pick from a list. I have seen Frostwire in one of these :)

And for the "N", just download the .tar.gz file and install it.

You can read here how to install a tarball.
[http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/](http://www.newlinuxuser.com/howto-install-deb-rpm-and-source-code-files/)

---

### Post by ncappel1 on 2006-04-18
There are slight differences between installing programs from source (ie not from synaptic) and I always tell people on the forums to visit these two clear guides. I give two because it's always good to have a second reading of the same amterial to reinforce what you learn, and get a different wording on the same subject, which hopefully will lead to a clearer concept.

[http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

[http://www.linuxnewbieguide.org/chap9.php](http://www.linuxnewbieguide.org/chap9.php)

let us know how it works out!

---

### Post by gsail11 on 2006-04-18
Thanks for the responses. That Automatix thing hooked me up with frostwire with no problem, but I am still struggling with the N game. Has anyone attempted to install it? Maybe I'm not the only one. I tried untarring (or whatever verb you'd use) the .tar.gz file both with the GUI and the terminal, neither of which worked. Any advice?

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

---

### Post by gsail11 on 2006-04-18
I finally got the windows version of the game working using Wing. It's good that I did it that way, because I was going to have to learn to use wine eventually. I think it ight have been an issue with N specifically, because I installed the firefox flash plugin from a .tar with no problems. Thanks for the help.

(If any of you are bored, try out that game, it's great.)

---

### Post by mostwanted on 2006-04-18
The Firefox flash plugin is available from the repositories, why did you install it via a tgz?

---

### Post by JoeMetal on 2006-04-18
Since it was a .tar.gz file, first you need to run ```
gzip -d *filename*.tar.gz
```or something like that.  That will give you a .tar file, then you can run ```
tar -xvf *filename*.tar
```  After that, you should be good to go with the rest of the install process.

---

### Post by angkor on 2006-04-18
[QUOTE=gsail11]I tried untarring (or whatever verb you'd use) the .tar.gz file both with the GUI and the terminal, neither of which worked. Any advice?
[/quote]

You don't need to *install* the game. Just extract the directory in the .tar.gz with the archive manager. Enter the directory with:

```
cd n_v1linux/
```

start the game with:

```
./n_v14
```

If you get an error about libstdc++-libc6.2-2.so.3 read [this]("http://metanet.2.forumer.com/index.php?act=Search&CODE=show&searchid=9d2a51e1f025fc856c1a1423e6567d09&search_in=posts&result_type=posts&highlite=ubuntu")

---

### Post by gsail11 on 2006-04-22
Om, I used the .tar file for the firefox thing because it wouldn't play videos for some reason when I tried the simpler ways. I don't think you guys understand the probkem I was having with the N game. I successfully untar the file with not problem using the GUI thing, then I have the folder on my desktop, and when I double click, it just won't open. Now I think that there is something wrong with the file or something, but at the time I thought I was untarring it wrong.

Anyways, I think we can close this thread, because the installing problem is sorta through for me, now I'm moving on to bigger and more frustrating issues. ;) 

Kidding of course, I'm realling enjoying Ubuntu.

---

### Post by Bernie01 on 2006-04-22
[QUOTE=ncappel1]There are slight differences between installing programs from source (ie not from synaptic) and I always tell people on the forums to visit these two clear guides. I give two because it's always good to have a second reading of the same amterial to reinforce what you learn, and get a different wording on the same subject, which hopefully will lead to a clearer concept.

[http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

[http://www.linuxnewbieguide.org/chap9.php](http://www.linuxnewbieguide.org/chap9.php)

let us know how it works out![/QUOTE]
Hi I have recent;y followed the instructions ncappel1 linked to to download Frostwire, however when I enter sudo dpkg Frostwire.deb (I changed the download name) I get an error message saying 
'dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].'

Where do I go from here?

---

### Post by 3rdalbum on 2006-04-23
Bernie: You'll find that you have to type ```
sudo dpkg -i Frostwire.deb
```.

The "-i" tells dpkg that you want to install the program - the error message was telling you (in a non-user-friendly way) that you hadn't told it what you wanted to do with the package.

For a description of all the options you can give the dpkg program, type man dpkg.

Also, to remove Frostwire, you can type:
```
sudo dpkg -r frostwire
```
Note that you just give the package name, not the filename, to remove.

Dapper Drake has a GUI utility for dealing with .deb files, so on June 1st you might want to upgrade.

---

### Post by Bernie01 on 2006-04-23
Thanks 3rdalbum. I guess I need to use that '-i' for all installs?

---

