---
title: "Read E-Books on Ubuntu?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by da5id on 2006-04-11
I have quite a library of e-books in the format of Microsoft Reader -- the books are encrypted in the sense that they are tied to the Microsoft Reader installed on my Microsoft OS.  I would like to be able to read these books in Ubuntu.  Does anyone have any ideas?  A place, like a newsgroup, would this subject might be more appropriately addressed?

I am not trying to rip off the publishers or authors -- I paid for these books, they are mine.  I have read the End-Users License Agreement and I don't see any prohibition against reading them via an operating system other than Microsoft Windows.  I am an absolute beginner, so please do not assume that I know anything about WINE should that be a solution and, perhaps, the only possible one.  Thanks in advance.

In the future, I can purchase these books in any format, including Adobe PDF encrypted.  It is not my favorite format, but I would consider it if it worked well with the Ubuntu.  I searched the Adobe web site for Adobe Reader for Linux, but the results unclear.  Has anyone used Adobe reader for encrypted e-books on Ubuntu?

-- Gene

---

### Post by cleverselfreferentialname on 2006-04-11
You mean .lit files, right? You can convert them with [http://www.kyz.uklinux.net/convlit.php](http://www.kyz.uklinux.net/convlit.php)

---

### Post by Ob1 on 2006-04-11
just install xCHM

---

### Post by da5id on 2006-04-11
Yes, I most definitely do mean .lit files.  Thanks very much.  I sure hope it works.  Getting answers on this forum is very much like IM.  :-)

---

### Post by da5id on 2006-04-15
I DL'd a pkg I need to read *my* MS Reader ebooks in my shiny *new* OS, Ubuntu, from [http://www.kyz.uklinux.net/convlit.php](http://www.kyz.uklinux.net/convlit.php)

The directions say: 

"To compile and install the program goes *something* like this [emphasis added]:

$ gzip -cd < open_c-lit.tar.gz | tar xf -
$ cd cl?t14src/lib
$ make
$ cd ../cl?t14
$ make
# install cl?t /usr/local/bin

The final command is executed as root. The question marks are wildcards, purely for keeping this web-page available to everybody. You can put the letter i in their place, should it amuse you."


A copy of my term results, all errors, is attached as a text file.  Any suggestions will be appreciated.

--Gene

PS I tried to copy term text to Open Office Writer so colors would be visible, but "paste" into Writer did nothing -- just a blank page.  Is a copy and paste from Terminal special -- eg, you can only paste to a plain txt program?

NB  I am an ABSOLUTE BEGINNER still working on my bash tutorials.  So "Just ./configure, make, makeinstall the regular way," responses will be less than helpful.;)

---

### Post by user1397 on 2006-04-15
Adobe Reader is very ubuntu compatible.
If you got to applications-->add applications, it'll be under office.
of course you can also do this through synaptic if you prefer

---

### Post by da5id on 2006-04-15
I know, but Adobe Reader will not open the .lit (MS Reader) titles I own.  I have used Add Applications, it's foolproof, but I thought it *was* synaptic untill I just clicked its About.  Where is synaptic?

Thanks, Gene

---

### Post by macdo on 2006-04-15
synaptic is in System->Administration.

On a more general note, anytime you want to open an application that you can't find in the menus, just click on the "run application" icon in the bar and type the name of the app.
For applications that need root access, you can do the same thing in a terminal using sudo. Just don't close the terminal before you close the app:) .

---

### Post by da5id on 2006-04-15
[QUOTE=macdo]synaptic is in System->Administration.

On a more general note, anytime you want to open an application that you can't find in the menus, just click on the "run application" icon in the bar and type the name of the app.
For applications that need root access, you can do the same thing in a terminal using sudo. Just don't close the terminal before you close the app:) .[/QUOTE]

I am embarrassed.  I thought I had clicked on *everything* in the default set-up before  my first post. :rolleyes:   Thanks for the heads up.  I have already closed a terminal (I think I had several open at once) and Ubuntu was not pleased.);)  

--Gene

---

### Post by da5id on 2006-04-18
[QUOTE=erik1397]Adobe Reader is very ubuntu compatible.
If you got to applications-->add applications, it'll be under office.
of course you can also do this through synaptic if you prefer[/QUOTE]

OK, I bought a Adobe ebook from amazon, it would not DL. That can happen with DRM reader to bind it to.  I followed instructions to DL Adobe Reader -- no go, bad hardware (AMD 64?). Is reading an exotic activity in Linux.  I'm certainly not close to a solution in this thread.  Any ideas? --Gene

---

### Post by da5id on 2006-04-20
[QUOTE=erik1397]Adobe Reader is very ubuntu compatible.
If you got to applications-->add applications, it'll be under office.
of course you can also do this through synaptic if you prefer[/QUOTE]

Thanks.  Greyed out -- will not install through Synaptic either.  So far with Ubuntu I can browse the web with no Java, Flash, video (no online classes on Real).  Is it Unubuntu to use Firefox with broadband/multimedia?  Can't install plugin through Firefox, even though Linux is supported.  Not working in "Add Applications."  Ditto for Macrmedia webbsite and Linux.  What else...thats about it, surf web with 'Install Plugin" in yellow at the top of every other site.

---

### Post by verbalshadow on 2006-04-20
My understanding is that all of the thing you mention are compiled only for x86. If you are use an AMD64 install the 386/586 kernel and boot using it or search the forums on howto setup a chroot.

---

### Post by da5id on 2006-04-21
[QUOTE=verbalshadow]My understanding is that all of the thing you mention are compiled only for x86. If you are use an AMD64 install the 386/586 kernel and boot using it or search the forums on howto setup a chroot.[/QUOTE]

WTF, you want an AB to install a new kernel.  You want me to write it too?  And what the hell is a chroot?  The only post I saw was by an experienced admin saying he didn't have the patience to "bugger about" with chroot.  Freaking hit and run advice.](*,)

---

### Post by verbalshadow on 2006-04-21
sorry about the "hit and run advice" that a new kernel is not hard as they are pre-compiled and available in synaptics for easy install ( search linux-image-386 in synaptic). but you may not have to do a chroot. as for the web stuff try this page [http://ubuntuforums.org/showthread.php?t=90106](http://ubuntuforums.org/showthread.php?t=90106)

---

### Post by da5id on 2006-04-21
[QUOTE=verbalshadow]sorry about the "hit and run advice" that a new kernel is not hard as they are pre-compiled and available in synaptics for easy install ( search linux-image-386 in synaptic). but you may not have to do a chroot. as for the web stuff try this page [http://ubuntuforums.org/showthread.php?t=90106](http://ubuntuforums.org/showthread.php?t=90106)[/QUOTE]


Install this: systemimager-booti-386? 
[COLOR="RoyalBlue"]
"SystemImager boot binaries for i386 client nodes
SystemImager is a set of utilities for installing GNU/Linux disk images to
client machines over the network.  Images are stored in flat
files on the server, making updates easy.  The rsync protocol is used for
transfers, making updates efficient.

This provides an optional ssh component for the image server, which
adds the ability to do secure, automated installs."[/COLOR]

Why do I think this won't work?  Is this considered AB help -- throw out some search terms and say install search results.  If I were giving advice I would do the search myself (10 seconds), identify a unique file name, and provide an overview of what to do, why, how, and expcted results (5--6 minutes).  This just goes on with no end in sight.

---

### Post by verbalshadow on 2006-04-22
Acrobat and other programs are compiled to run on 32bit systems and not compiled to run on 64bit systems (i.e. AMD64 ) there are a few ways around this in linux.

1.  Install the linux 32bit kernel. 
```
sudo apt-get install linux-image-386
```
then reboot and at the grub menu select the 386 version to boot to.

This gives you a 32bit system instead of a 64bit one and you should be able install acrobat reader with out any issues.

2. Build a chroot - this is a 32bit linux running in a 64bit linux kind of.
this is covered in this thread [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

3. use the ia32libs, i just found this so i don't know if it works
found in the post here [http://www.ubuntuforums.org/showpost.php?p=548789&postcount=8](http://www.ubuntuforums.org/showpost.php?p=548789&postcount=8)

---

### Post by futz on 2006-04-22
[QUOTE=da5id]OK, I bought a Adobe ebook from amazon, it would not DL. That can happen with DRM reader to bind it to.  I followed instructions to DL Adobe Reader -- no go, bad hardware (AMD 64?). Is reading an exotic activity in Linux.  I'm certainly not close to a solution in this thread.  Any ideas? --Gene[/QUOTE]
Linux badly needs a Lit reader program. If I was a better programmer I'd tackle the project... 

I just don't feel like converting them all. I just wanna read em! :rolleyes: 

I have a large collection of lit books. I like the format and the MS reader. I've tried to install it under Wine, but it's a tough one to get working. I've had no luck with it at all.

---

### Post by da5id on 2006-04-22
[QUOTE=verbalshadow]Acrobat and other programs are compiled to run on 32bit systems and not compiled to run on 64bit systems (i.e. AMD64 ) there are a few ways around this in linux.

1.  Install the linux 32bit kernel. 
```
sudo apt-get install linux-image-386
```
then reboot and at the grub menu select the 386 version to boot to.

This gives you a 32bit system instead of a 64bit one and you should be able install acrobat reader with out any issues.

2. Build a chroot - this is a 32bit linux running in a 64bit linux kind of.
this is covered in this thread [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

3. use the ia32libs, i just found this so i don't know if it works
found in the post here [http://www.ubuntuforums.org/showpost.php?p=548789&postcount=8](http://www.ubuntuforums.org/showpost.php?p=548789&postcount=8)[/QUOTE]

I got "E. Couldn't find linux-image-386"

I kinda get what chroot is -- not feasible for AB.  I would rather use a 32-bit OS and upgrade to 64 bit when it is seamlewssly backwards compatible with 32  bit apps or I get more experience in Terminal. Am reading bash tutorials but I haven't got to chroot level stuff yet.

---

### Post by da5id on 2006-04-22
[QUOTE=futz]Linux badly needs a Lit reader program. If I was a better programmer I'd tackle the project... 

I just don't feel like converting them all. I just wanna read em! :rolleyes: 

I have a large collection of lit books. I like the format and the MS reader. I've tried to install it under Wine, but it's a tough one to get working. I've had no luck with it at all.[/QUOTE]

Were you sucessfull  in converting *any *of them.  My error messages installing c-lit can be found in this thread.  Then I read an extensive post on how to convert Wiindows users to Ubuntu. It suggested not try to  make something work that doesn't, but rather, use what does.  So I bought an Adobe book and hit another brick wall.  Crappy advice!](*,)  -- Gene

---

### Post by futz on 2006-04-22
[QUOTE=da5id]Were you sucessfull  in converting *any *of them.[/quote]
Yes.

> My error messages installing c-lit can be found in this thread.
In this thread I answered your questions and showed how to do it: [http://ubuntuforums.org/showthread.php?t=159331](http://ubuntuforums.org/showthread.php?t=159331)

---

### Post by futz on 2006-04-22
[QUOTE=da5id]My error messages installing c-lit can be found in this thread.[/QUOTE]
I just read your error messages more closely. So here we go...

```
da5id@ubuntu:~$ cd home/da5id
bash: cd: home/da5id: No such file or directory
```
Won't work. You would have to do this instead. Note the / in front of home:
```
cd /home/da5id
```
Another way to get to your home directory is this:
```
cd ~
```

Another little thing is that when you were attempting to cd to your home dir, you were already there. You can tell by this line:
```
da5id@ubuntu:~$ cd home/da5id
```
You see the tilde (~) before the $ prompt? A tilde means home directory, and your home directory *is* /home/da5id. See? ~ is a shortcut for /home/da5id. For instance:
```
futz@ubuntu:~$
```
means I'm in my home dir, but
```
futz@ubuntu:/etc$
```
means I'm in the /etc dir

:::::::::::::::::::::::::::::::::::::::::::::::::::

Don't bother with this:
```
da5id@ubuntu:~/Desktop$ gzip -cd < open_c-lit.tar.gz | tar xf -
```
The easy way to do that is to just double click on open_c-lit.tar.gz in Nautilus. File Roller will start up and you can just click Extract a couple times to put the directory of files in the current directory. Or tell it where you want the files before extracting.

---

### Post by da5id on 2006-04-24
[QUOTE=futz]I just read your error messages more closely. So here we go...

```
da5id@ubuntu:~$ cd home/da5id
bash: cd: home/da5id: No such file or directory
```
Won't work. You would have to do this instead. Note the / in front of home:
```
cd /home/da5id
```
Another way to get to your home directory is this:
```
cd ~
```

Another little thing is that when you were attempting to cd to your home dir, you were already there. You can tell by this line:
```
da5id@ubuntu:~$ cd home/da5id
```
You see the tilde (~) before the $ prompt? A tilde means home directory, and your home directory *is* /home/da5id. See? ~ is a shortcut for /home/da5id. For instance:
```
futz@ubuntu:~$
```
means I'm in my home dir, but
```
futz@ubuntu:/etc$
```
means I'm in the /etc dir

:::::::::::::::::::::::::::::::::::::::::::::::::::

Don't bother with this:
```
da5id@ubuntu:~/Desktop$ gzip -cd < open_c-lit.tar.gz | tar xf -
```
The easy way to do that is to just double click on open_c-lit.tar.gz in Nautilus. File Roller will start up and you can just click Extract a couple times to put the directory of files in the current directory. Or tell it where you want the files before extracting.[/QUOTE]

Thanks.  This is just "Stupid Newbie Tricks."  I learn by trial and errors.  Thanks for your tips.  I just wish Adobe Reader would run on my AMD64 version of Ubuntu. :confused:

---

### Post by praxxus on 2006-05-30
Stumbled across this in my search for tools to make ebooks (.lit format) usable on my Ubuntu install... [http://www.rush.ws/win/programming/file-editors/abc-amber-lit-converter-1-07./]("http://www.rush.ws/win/programming/file-editors/abc-amber-lit-converter-1-07./")
I've tested it with several ebooks and seems to work well so far into several different formats. Haven't tried setting it up to work with Wine as of yet, just used under windows for the conversions I needed.

---

### Post by aj61779 on 2007-11-19
message removed

---

### Post by &#1050;&#1085;&#1077;&#1083;&#1077; on 2007-12-20
Greetings,

Possible solution for files with .lit extension:[HOWTO: Open files with .lit extension in Firefox]("http://ubuntuforums.org/showthread.php?t=633429")

---

