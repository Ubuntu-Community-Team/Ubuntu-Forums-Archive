---
title: "Simple install question"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by purebuilt on 2007-11-29
I've been searching everywhere and can't find out how to install tar ball programs that I download. I extract the files into their own folder from HOME but can't remember how to setup a launcher on the desktop. What's the simple method that doesn't involve a lot of terminal lines I don't understand?

Ubuntu is great. I'm using it all the time now so I'd like to get this launcher thing down.

Thanks

DB

---

### Post by Dr Small on 2007-11-29
If it is a tar ball file, then most usually you have to compile it from source, unless it is something like Firefox and has an executable in it.

Otherwise, it would be simpler to look for a .deb and install that.

Dr Small

---

### Post by purebuilt on 2007-11-29
It is Netscape 9 and someone showed me what to do but I don't remember now. :(

DB

---

### Post by bobyy on 2007-11-30
helloo ...right click on the pannel>new launcher  and put the all path to your executable( /home/netscape/netscape.exe)
enjoy.

---

### Post by vikramsharma on 2007-11-30
> **purebuilt said:**
> It is Netscape 9 and someone showed me what to do but I don't remember now. :(

DB

Here are some links that could help you out.

[http://ubuntuclips.org/videos/1](http://ubuntuclips.org/videos/1)

[http://ubuntuforums.org/archive/index.php/t-361110.html](http://ubuntuforums.org/archive/index.php/t-361110.html)

[http://www.extremetech.com/article2/0,1697,2126240,00.asp](http://www.extremetech.com/article2/0,1697,2126240,00.asp)

---

### Post by purebuilt on 2007-11-30
There is no exe file. I did it for my other Ubuntu desktop but forgot how. The launcher there has the path  /home/name/navigator/navigator

Where navigator is some kind of script file.

I'm sure this is simple but I don't know how so that makes it hard. I want to use Ubuntu for good now so I need to learn how to install from a tar ball.

Thanks

DB

---

### Post by bobyy on 2007-11-30
Maybee when you create the launcher .must be "Type..Application in terminal"

---

### Post by purebuilt on 2007-11-30
I've tried both. When I do IN TERMINAL it flashes on the screen and then quits.

HELP! :)

DB

---

### Post by bobyy on 2007-11-30
if its a script try to put > tail -f or > watch first will read and dont exit seccond will "watch " the procces

---

### Post by twiceasworn on 2007-11-30
Alright, if it needs to be compiled, then there should be either a configure or install.sh script in the programs directory you untarred.  If it is configure you need to do 

```
./configure
make
sudo make install
```

If its the install.sh :

```
sudo sh install.sh
```

Also, as someone previously mentioned, if it is like firefox and has an executable file in the directory, you can just right click on the panel, click add to panel and type the path to the executable.

---

### Post by purebuilt on 2007-11-30
This is the directory listing.

```
:~/navigator$ ls
browserconfig.properties  icons           libplc4.so          libxpcom_core.so                 plugins
chrome                    libfreebl3.chk  libplds4.so         libxpcom.so                      readme.txt
components                libfreebl3.so   libsmime3.so        libxpistub.so                    removed-files
defaults                  libmozjs.so     libsoftokn3.chk     mozilla-xremote-client           res
dictionaries              libnspr4.so     libsoftokn3.so      navigator                        run-mozilla.sh
extensions                libnss3.so      libssl3.so          navigator-bin                    searchplugins
greprefs                  libnssckbi.so   libxpcom_compat.so  old-homepage-default.properties  xpicleanup

```

---

