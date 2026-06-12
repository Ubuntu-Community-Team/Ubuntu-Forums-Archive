---
title: "Does Alien have an icon?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-12-04
hi, i installed Alien eariler today, after the install i refreshed the panel but i still had to use SMEG to put it in the menu. the only "alien" icon i could find was from Gaim's smiley folder so i used that. does it have an icon?

also, do you use Privoxy? because if you do can you answer the question below? thanks
[http://www.ubuntuforums.org/showthread.php?t=98748](http://www.ubuntuforums.org/showthread.php?t=98748)

---

### Post by 23meg on 2005-12-04
If you mean the package conversion utility alien, it's meant to be used from the command line so it doesn't come with an icon. ```
man alien
``` will give you info on how to use it.

---

### Post by aysiu on 2005-12-04
alien can't run by itself. It needs other arguments. If you try to run alien by itself you get this: ```
alien
You must specify a file to convert.

Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch            Do not use patches.
       --anypatch           Use even old version os patches.
       --single             Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Unpack, but do not generate a new package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.  -k, --keep-version        Do not change version of generated package.
  -h, --help                Display this help message.
  -V, --version             Display alien's version number.

```

---

### Post by xmastree on 2005-12-04
And also, if you try to run it from the menu, you won't even see what aysiu shows, since there will be no window to display it.

basically, you use a terminal, navigate to where your .rpm is and type```
sudo alien foobar.rpm
```

---

### Post by Danielle on 2005-12-04
thanks for all the help, i used it to install Frostwire, it's really good :) but, i'm still really new to Ubuntu so what i was worried about is forgetting about it being on the system, so i need something to remind me i have it. how do you remember your command line programs? are they all in the same directory? thanks

---

### Post by xmastree on 2005-12-04
Typically they're all in **/usr/bin** 

The best command you can ever use is **apropos**

For example, you're looking for something connected with mp3 files.
```
$ apropos mp3
cdda2mp3 (1)         - extract audio CD audio tracks and encode them
lame (1)             - create mp3 audio files
mp3-decoder (1)      - Free clone of mpg123, a command-line mp3 player
mpg123 (1)           - Free clone of mpg123, a command-line mp3 player
mpg321 (1)           - Free clone of mpg123, a command-line mp3 player

```or id3 tags```
~$ apropos id3
id3 (1)              - an ID3 tag editor.
id3ed (1)            - edit id3 description tags in mpeg3 files
```
If you forget the spelling, apr<tab> is enough

---

### Post by Danielle on 2005-12-04
thanks, xmastree. i've still got loads to learn before i can understand how things work with Unix/Ubuntu

---

### Post by xmastree on 2005-12-04
You're certainly not alone there. I'll gladly share what I do know, but there is a whole heap of stuff I've yet to learn.

The nice thing about linux is that you can make a test account for yourself and mess around in there to your heart's content safe in the knowledge that whatever you do can only affect that user, and you can't cripple the system. Even better, don't allow that user to access shared partitions, then your data's safe.

---

