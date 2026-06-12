---
title: "Totem Plugins"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-08-02
I stuck a DVD in the Movie Player and got the response:

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it. Please install the necessary plugins and restart Totem to be able to play this media.

I wnet to Synaptic and uninstalled everything Totem -- then reinstalled everything Totem. Got the same response. Where are the Totem plugins for playing DVDs?

---

### Post by atomkarinca on 2007-08-02
this should work: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

well, i just noticed that you're using edgy: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability)

---

### Post by lwalper on 2007-08-02
So I ran
```

sudo apt-get install libdvdread3
``` 
and receivedthe following
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3

```
Also looked in Synaptic for the package - - no joy.

---

### Post by atomkarinca on 2007-08-02
did you enable extra repositories?

system > administration > system sources

check all four of them and then try again.

---

### Post by lwalper on 2007-08-02
OK, Thanks! That worked.

Now, when I run the movie player I get the message:

"An error occurred; the source seems encrypted, and can't be read,  Are you trying to play an encrypted DVD without libdvdcss?"

It's a commercial DVD and I'm certain it's encrypted I think I already installed libdvdcss somewhere??

---

### Post by lwalper on 2007-08-02
I found and installed libdvdcss3 from Synaptic. Still the same error message.

---

### Post by atomkarinca on 2007-08-02
i think it's no harm re-installing it :)

---

### Post by SilverDragon on 2007-08-02
I was having the same problem and after following your advice I can watch commercial DVDs that are encrypted. Thanks for the advice.

For the person still struggling did you type 

sudo apt-get install libdvdcss2

in the terminal?

---

### Post by lwalper on 2007-08-02
So I installed gxine. Same response: "encrypted or faulty DVD"

I know it's not a faulty DVD since it plays in other hardware without a problem.

---

### Post by atomkarinca on 2007-08-02
i found this:

```
wget http://www.videolan.org/pub/videolan/libd vdcss/1.2.9/libdvdcss-1.2.9.tar.gz
tar -xzf lib*.tar.gz
rm lib*.gz
cd lib*
./configure
make
sudo make install
```

edit: hit tab button where it says *

---

### Post by lwalper on 2007-08-02
Oops, got a 404 error on that wget request -- must be a bad or obsolete link.

---

### Post by atomkarinca on 2007-08-02
alright, first line should've been:

```
wget http://www.videolan.org/pub/videolan/libdvdcss/1.2.9/libdvdcss-1.2.9.tar.gz
```

---

### Post by lwalper on 2007-08-02
OK, that worked. The file downloaded -- to somewhere -- not the desktop. Where's the default download folder?

In the meantime, I did a *complete* un-install of everything relating to libdvdcss and then re-installed. Following install the machine did an automatic restart and PRESTO, the movie thingy works.

Whatever happened, it works now. Thanks for all your help!! I really appreciate it. Now, to get my printer working. Maybe tomorrow?

---

### Post by lwalper on 2007-08-02
I may have quit too soon. The FBI warning played, but then when the movie should start, the same encrypted problem stuck it's little nose in there again.

---

### Post by atomkarinca on 2007-08-02
i don't if this could be solution but did you try to skip to next chapter? you can do it by hitting n button or go > next chapter.

---

### Post by lwalper on 2007-08-02
Yep, tried that. I think the disk is made so you can't skip that first little FBI thing.

Anyway, back to where we were. I did locate that downloaded file, moved it to my desktop (where I'd know where it was) did the tar thing -- all seems to go OK -- until I run make install, then I get 
```
Making install in src
make[1]: Entering directory `/home/lwalper/Desktop/libdvdcss-1.2.9/src'
Making install in dvdcss
make[2]: Entering directory `/home/lwalper/Desktop/libdvdcss-1.2.9/src/dvdcss'
make[3]: Entering directory `/home/lwalper/Desktop/libdvdcss-1.2.9/src/dvdcss'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dvdcss" || mkdir -p -- "/usr/local/include/dvdcss"
mkdir: cannot create directory `/usr/local/include/dvdcss': Permission denied
make[3]: *** [install-pkgincludeHEADERS] Error 1
make[3]: Leaving directory `/home/lwalper/Desktop/libdvdcss-1.2.9/src/dvdcss'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/lwalper/Desktop/libdvdcss-1.2.9/src/dvdcss'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/lwalper/Desktop/libdvdcss-1.2.9/src'
make: *** [install-recursive] Error 1
```
something about permission denied -- do I need to run sudo with that?

Tried it, didn't like it.

The make command too seemed to generate errors ( I may be reading the information incorrectly ) 
```
Making install in test
make[1]: Entering directory `/home/lwalper/Desktop/libdvdcss-1.2.9/test'
make[2]: Entering directory `/home/lwalper/Desktop/libdvdcss-1.2.9/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/lwalper/Desktop/libdvdcss-1.2.9/test'
make[1]: Leaving directory `/home/lwalper/Desktop/libdvdcss-1.2.9/test'
```

---

### Post by atomkarinca on 2007-08-02
you should run make install like this:

```
sudo make install
```

---

### Post by lwalper on 2007-08-02
OK, did that. I also noticed your "edit" --

hit tab button where it says *

Is that something I'm supposed to do? -- hit the tab button -- where the * is?

---

### Post by lwalper on 2007-08-02
So, since Movie Player doesn't seem to want to play nice, I went to Synaptic and installed Ogle. Everything seemed to go OK, but when I look for it in the applications list, it's not there. Where did it go?

---

