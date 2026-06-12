---
title: "Firefox 2. 0 Installation"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by tombiz on 2006-10-24
I downloaded Firefox 2 to my desktop, but I don't know how to install it. Can someone help me?

---

### Post by George_S on 2006-10-24
Actually, if you are willing to wait for a couple of days, you will get the Firefox 2.0 update automatically with the new version of Ubuntu (6.10).

---

### Post by joplass on 2006-10-24
can't wait i heard a lot of good things about firefox 2.0

---

### Post by bodhi.zazen on 2006-10-24
Save such thing for the future in scr (for source):

[color=red]The how-to below is wrong. I have no clue how to install Firefox 2. I posted this because I assumed the tar ball was source.

The tar ball however is a BINARY.

This means no install required. Just extract and run.

See [Solution](http://ubuntuforums.org/showpost.php?p=1658990&postcount=12) [/color]**[size=2][color=blue]Thanks jetpeach**[/size][/color] 

Original post: Well, although wrong perhaps it is somewhat informative....

```
mkdir ~/src
mv ~/Desktop/firefox* ~/src
cd ~/src
tar xvzf firefox*
sudo aptitude install build-essential checkinstall
cd firefox2 (or whatever directory was created by the tar command)
./configure
make
sudo checkinstall
```

---

### Post by thornomad on 2006-10-24
what's this "checkinstall" ?  Is it different than regular "install" ?  

And: how would you "uninstall" ?  Is that why you keep the folder in "src" ?

---

### Post by ciscosurfer on 2006-10-24
checkinstall can be found in the unvierse repos and is defined like this:
CheckInstall keeps track of all the files created or modified by your installation script ("make install" "make install_modules", "setup", etc), builds a standard binary package and installs it in your system giving you the ability to uninstall it with your distribution's standard package management utilities.

---

### Post by underwater on 2006-10-24
> **thornomad said:**
> what's this "checkinstall" ?  Is it different than regular "install" ?  

And: how would you "uninstall" ?  Is that why you keep the folder in "src" ?

Actually the checkinstall makes it easier to uninstall.  It will generate a .deb and intall it.  In the most basic sense, you use it after "make" instead of "make install"

---

### Post by bodhi.zazen on 2006-10-24
[Checkinstall](https://help.ubuntu.com/community/CheckInstall)

To uninstall: ```
dpkg -r firefox2.deb
``` or whatever the firefox 2 .deb is called.

[How to checkinstall](http://ubuntuforums.org/showthread.php?t=2356)

---

### Post by bodhi.zazen on 2006-10-24
> **thornomad said:**
> what's this "checkinstall" ?  Is it different than regular "install" ?  

And: how would you "uninstall" ?  Is that why you keep the folder in "src" ?

Yes. You should ALWAYS keep anything you install outside of apt-get, aptitude, or synaptic somewhere.

---

### Post by thornomad on 2006-10-24
Thanks ... need to write all this down somewhere at times ... is a lot to remember.

And yet: it is still easier, better, and sexier than Windows.

---

### Post by bodhi.zazen on 2006-10-24
> **thornomad said:**
> Thanks ... need to write all this down somewhere at times ... is a lot to remember.

And yet: it is still easier, better, and sexier than Windows.

Just break Ubuntu a few times like I have. Then you will remember these things.

---

### Post by jetpeach on 2006-10-24
i downloaded from getfirefox.com and when i untarred, i found a firefox folder that didn't need to be compiled.  i just ran the firefox in there is it worked fine.  i made a shortcut to that firefox. 
this way, i still have the older 1.5 firefox for applications that might require it.  essentially, the 2.0 version is standing alone in it's own folder, though it does share the profile directory with 1.5 (so it would probably be a good idea to back that up first, /home/username/.mozilla

---

### Post by tombiz on 2006-10-24
OK. I'm still confused about what to do with the Tar-Ball file of Firefox 2.0 I got sitting on my desktop.:-k

---

### Post by andiii on 2006-10-24
> **tombiz said:**
> OK. I'm still confused about what to do with the Tar-Ball file of Firefox 2.0 I got sitting on my desktop.:-k

Why don't you read the last post on page 1?

---

### Post by bodhi.zazen on 2006-10-24
> **tombiz said:**
> OK. I'm still confused about what to do with the Tar-Ball file of Firefox 2.0 I got sitting on my desktop.:-k

LOL tombiz.

After reading the above I would:```
mv ~/Desktop/firefox* ~
tar xvzf firefox*
cd firefox
./firefox
```

Or whatever they are calling firefox...

---

### Post by dakini on 2006-10-24
Personally, I just extract it to my home directory and then make a desktop or panel link to /home/username/firefox/firefox.  It works perfectly fine without installing it.  Also I make a link to the firefox plugins directory so that takes care of everything.

---

### Post by aysiu on 2006-10-25
If you don't like waiting for Ubuntu's Firefox to update, take a look at this thread: [HowTo: A script to install the latest Firefox](http://ubuntuforums.org/showthread.php?t=151179)

---

### Post by tombiz on 2006-10-25
Thanks Everyone.

---

### Post by darrenrxm on 2006-10-25
Actually the simplest way to try out firefox 2 is to download the file and extract it to your desktop. Then all you have to do is open the folder and click on the file called "firefox". It will ask you if you want to run it. Say yes and you will be surfing with firefox 2.

---

### Post by Tobster on 2006-10-25
I know hard to belive but tomorrow Ubuntu gets even better when every one who  would like it can download Ubuntu 6.10 with the upgraded Fire Fox.

Toby

---

### Post by jaywatkins on 2006-10-25
> **bodhi.zazen said:**
> Save such thing for the future in scr (for source):

```
mkdir ~/src
mv ~/Desktop/firefox* ~/src
cd ~/src
tar xvzf firefox*
sudo aptitude install build-essential checkinstall
cd firefox2 (or whatever directory was created by the tar command)
./configure
make
sudo checkinstall
```

I lose it on the ./configure  Every time I try to install from source it always faile on ./configure with the error "No such file or directory".

I would rather install this way, believe it or not, but this process is very tedious, and always results in me having to post to the forums.

What am I doing wrong?  Thanks

---

### Post by bodhi.zazen on 2006-10-25
> **jaywatkins said:**
> I lose it on the ./configure  Every time I try to install from source it always faile on ./configure with the error "No such file or directory".

I would rather install this way, believe it or not, but this process is very tedious, and always results in me having to post to the forums.

What am I doing wrong?  Thanks

Nothing, it was me. So sorry.

Look up.. See post 12 and post 19.

10,000 apologies.

I edited my origional post....

---

### Post by aysiu on 2006-10-25
Why would you prefer to install from source?

---

### Post by motang on 2006-10-25
> **tombiz said:**
> I downloaded Firefox 2 to my desktop, but I don't know how to install it. Can someone help me?

Try this [thread]("http://ubuntuforums.org/showthread.php?t=248158") it will help you out.

---

### Post by andyrobo60 on 2006-10-25
Will firefox 2.0 be added to the apt-get updates for dapper??, if yes when??

---

### Post by trcook on 2006-10-25
if you just want a quick fix on firefox2 to hold you over until it comes through the repositories (the update programs -- for most people either synaptic or adept) then you can just extract the firefox folder from the tarball (the .tar.gz file from the firefox website), navigate to the folder and type "./firefox &" and the program should launch. So far as I understand it, this would be like running a program directly from a cd or floppy disk back in the before time, in the long long ago.

==someone correct me if running this script from w/in the firefox folder (w/out a proper install) would leave vestigal files on the system or something.

---

### Post by George_S on 2006-10-26
> **andyrobo60 said:**
> Will firefox 2.0 be added to the apt-get updates for dapper??, if yes when??

It's out. You can download it [here]("http://www.ubuntu.com/products/GetUbuntu/download?highlight=%286.10%29").

---

