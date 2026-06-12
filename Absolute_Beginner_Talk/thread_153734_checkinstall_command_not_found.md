---
title: "checkinstall command not found"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by xlib on 2006-04-01
xlib@splash:~/Desktop/gaim-1.5.0/gaim-1.5.0$ sudo checkinstall -D make install
sudo: checkinstall: command not found

I am trying to install gAIM and I got this error. I am following the instructions on [https://wiki.ubuntu.com/CompileGaim](https://wiki.ubuntu.com/CompileGaim)

---

### Post by Mustard on 2006-04-01
Checkinstall needs to be installed before you can use it...

```
sudo apt-get install checkinstall

#checkinstall is in the universe repository
#so make sure you have the universe repo enabled
#in your sources.list or via Synaptic repository settings.
```

The usage of checkinstall is normally just..

```
sudo checkinstall
```

not like below, although technically you are correct. :)

```
sudo checkinstall -D make install
```

as you have it shown above.  I suppose it is an option, but I am pretty sure the default setting is 'make install', so the extra bits you have on the end are not necessary.

---

### Post by xlib on 2006-04-01
xlib@splash:~$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall

---

### Post by Mustard on 2006-04-01
[QUOTE=xlib]xlib@splash:~$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall[/QUOTE]

You need to enable your 'extra repositories' known as the universe and multiverse.

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by xlib on 2006-04-01
I am having trouble following those directions.. What does it mean by, "Tick Show disabled software sources, then click Close."

;/

---

### Post by Mustard on 2006-04-01
This link has pictures. :)  It might make it easier to understand.

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

When it says to tick 'Show disabled software sources' it saying there is a little box with 'Show disabled softward sources' label next to it.  You would put a 'tick' in that box, by clicking on the box and then you would close that dialog, by clicking on 'Close'.

---

### Post by christhemonkey on 2006-04-01
The dialog in synaptic, check the box refering to "Show disabled software sources".
Then close the dialog box.

---

### Post by Mustard on 2006-04-01
This is another reminder to me how it is so much easier to tell someone how to do something via the command line, than it is to explain how to use a graphical interface. :)

---

### Post by xlib on 2006-04-01
alright i've done that now.

Can someone give me step by step instructions to install "checkinstall" now?
i've tried doing this one thing..

Going into the terminal and typing all of these in, seperately.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install libwww-perl
sudo apt-get install libgtk2.0-dev
sudo apt-get install checkinstall

---

### Post by taurus on 2006-04-01
[QUOTE=xlib]alright i've done that now.

Can someone give me step by step instructions to install "checkinstall" now?
i've tried doing this one thing..

Going into the terminal and typing all of these in, seperately.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install libwww-perl
sudo apt-get install libgtk2.0-dev
sudo apt-get install checkinstall[/QUOTE]
Yes, or you can install all the packages with one line...
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential libwww-perl libgtk2.0-dev checkinstall

```

---

### Post by xlib on 2006-04-01
Alright now I am stuck again.

xlib@splash:~$ sudo ./configure --enable-gnutls=yes --prefix=/opt/gaim-1.5.0
sudo: ./configure: command not found

I know that the command isn't there.. But where do I get it?

---

### Post by Mustard on 2006-04-01
[QUOTE=xlib]Alright now I am stuck again.

xlib@splash:~$ sudo ./configure --enable-gnutls=yes --prefix=/opt/gaim-1.5.0
sudo: ./configure: command not found

I know that the command isn't there.. But where do I get it?[/QUOTE]

Check to see if the configure file has executable permissions.

-edit-

I'm surprised the guide does not tell you to do this actually. :)

It should be something like

```
sudo chmod +x configure
```

-edit2-

Actually it looks like you might not have used cd to get into the right directory. What directory are you compiling all this in?  What is your current working directory?  Looking at your prompt you seem to be working in $HOME.

The guide says to set up a folder /tmp/gaim it seems.

/me read more of the guide...

Ah, I see it now..it says to cd to /tmp and then extract the contents, which will create a folder called gaim<version>.  You should be in that directory.

-edit3-

Personally I would compile it in user space in some working folder on desktop. :)  Is there any compelling reason why it needs to be compiled in /tmp?

---

### Post by xlib on 2006-04-01
Umm, what do you mean?

---

### Post by Mustard on 2006-04-01
[QUOTE=xlib]Umm, what do you mean?[/QUOTE]

Which part don't you understand?

From what I can see you have missed a step somewhere.  Where did you extract the contents of the file to? See the part in bold below..

[quote=from the guide]Getting the source

Download the latest source version from here:

[WWW] Downloads or [WWW] Downloads (for the current 2.0Beta download)

(remember, you will want the source package. These are the .tar.bz2 or .tar.gz files)

**Unpack this file into your /tmp folder using Archive Manager** [/quote]

---

### Post by stanz on 2006-04-05
Hi All... Hey Mustard- i don't mean to distract this lesson,
can i poke my nose in here a second & ask about checkinstall..?
[COLOR=#000000][B]
August 10th, 2005[/B]: **Checkinstall 1.6.0** has been released. This is the first major release in a while. Go [download]("http://asic-linux.com.mx/%7Eizto/checkinstall/download.php") it!.

[/COLOR] Debian binary package:                 [checkinstall_1.6.0-1_i386.deb]("http://asic-linux.com.mx/%7Eizto/checkinstall/files/deb/checkinstall_1.6.0-1_i386.deb")

This is a first for me, and also to use the "Archive Manager".
I'm wondering where this needs to be unpacked{extract to ?} too? I can't find where ubuntu's version is- to overwrite or just put in same folder?
Their resting in /usr/share, for now...but i'm thinking there's a folder- they **need** to be in.
I'm searching~not trying to start another thread...Thanks!!

---

### Post by htinn on 2006-04-05
To stanz, you don't unpack deb files, you install them:

```
sudo dpkg -i checkinstall_1.6.0-1_i386.deb
```

Then you can just use the checkinstall command in the console.

I unpack all my sources to "~/src" folder. For example, I just compiled the latest beta for audacity yesterday :D First, I unpacked it, then did this:

```
cd ~/src/audacity-src-1.3.0b-beta
./configure
make
sudo checkinstall -D make install
```

---

### Post by stanz on 2006-04-06
Hey htinn...Thanks !! It went well, and checked also... whew! This goes in my notes.
As for source- unpacking & ,/configure... I need to search again and READ MORE!!
Thanks again!

---

