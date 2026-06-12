---
title: "Looking for a Newsgroup Reader"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Jim Hill on 2006-05-14
I've checked the Ununtu desktop and Firefox browser, and can't find a newsgroup reader. Where should I look?
Jim

---

### Post by nolan- on 2006-05-14
Hi

If it's binary download you are after either PAN or one I use is Klibido, it's a KDE based app but works fine in gnome.

Nol

PAN :  [http://pan.rebelbase.com/](http://pan.rebelbase.com/)
Klibido :  [http://klibido.sourceforge.net/](http://klibido.sourceforge.net/)

Both in repositories.

---

### Post by cgjones on 2006-05-14
Try looking [here](http://packages.ubuntu.com/).

---

### Post by DSn0wMan on 2006-05-14
If you mostly use newsgroups for binary, you might look into using ninan.

[http://ninan.sourceforge.net/](http://ninan.sourceforge.net/)

This one is fun because it runs as a server, and you can que downloads from anywhere. It's also very easy to install. The only problem I found is that it wont run on Ubuntu, or Debian without jre1.5.0_06

---

### Post by nolan- on 2006-05-14
Seems cool dsnowman , i'll give it a try....you should try everything once ;) 

One thing I miss about NBPro is that when you load a NZB it has a scratch list where all the PARS go so you can easily access them if needed. Whereas in Klibido you have to initially deselect the PAR files then download and check it and then reload the NZB and only select the PAR files you need.
I guess Its only a minor hassle.

A GUI for par2 would be nice, OK stop me i'm rambling hehe

---

### Post by Jim Hill on 2006-05-14
Hi: I followed cajones' suggestion and went to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), selected breezy (for Breezy Badger, I assume) then to Newsgroups. I like the descriptions this site provides.  Pan looked like a good choice, so I selected a download site, selected i386 since I have a PC and downloaded this application using Save to disk.

No problems so far - file pan_0.14.2.97-2ubuntu3_i386.deb appeared on the desktop. However, when I double clicked the icon the Archive Manager window appeared, saying Archive type not supported.

What's my next step?
Jim

---

### Post by nolan- on 2006-05-14
[QUOTE=Jim Hill]

*snip*

No problems so far - file pan_0.14.2.97-2ubuntu3_i386.deb 

What's my next step?
Jim[/QUOTE]


Hi Jim, Open a terminal wherever the file is and do this :

```
sudo dpkg -i pan_0.14.2.97-2ubuntu3_i386.deb 
```

Or you could install through synaptic if you wanted !

NoL

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=nolan-]Seems cool dsnowman , i'll give it a try....you should try everything once ;) 

One thing I miss about NBPro is that when you load a NZB it has a scratch list where all the PARS go so you can easily access them if needed. Whereas in Klibido you have to initially deselect the PAR files then download and check it and then reload the NZB and only select the PAR files you need.
I guess Its only a minor hassle.

A GUI for par2 would be nice, OK stop me i'm rambling hehe[/QUOTE]

ninan will auto-magically make parchecks, then unrar the files for you. You will probably need apt-get unrar, if you dont allready have it.

If you want you can just stick NZB files in the nzb folder, and it downloads them, but it's designed to be even easyer than that if you subscribe to newzbin.

Newzbin just varifies posts, categorizes them, and makes nzb files. It's a minimal cost, like 25 or 50 cents a week. This saves me hours of searching.

---

### Post by Jim Hill on 2006-05-14
Hi Nolan.  You said to "Open a terminal wherever the file is"
How do I select where I open the Terminal? In this case, the file is on the desktop. The only place where I can find to convert to the terminal mode is through Applications > Accessories > terminal.

Unfortunately, I don't know anything about Synaptic

---

### Post by nolan- on 2006-05-14
Yeah dsnowman I got subscription to Newzbin :D 

I got unrar and par2 installed too and honestly don't mind commandline tools but automated sounds like heaven...

Right now wheres that download !

---

### Post by nolan- on 2006-05-14
[QUOTE=Jim Hill]Hi Nolan.  You said to "Open a terminal wherever the file is"
How do I select where I open the Terminal? In this case, the file is on the desktop. The only place where I can find to convert to the terminal mode is through Applications > Accessories > terminal.

Unfortunately, I don't know anything about Synaptic[/QUOTE]

Hi Jim,
I'm in Kubuntu now so bear with me ;)
If you just click that link to the terminal that you quoted in Applications i'm almost sure it will open for you on the desktop anyhows.
When I open one in Kubuntu from the menu I get :

```
nol@nol-desktop:~$
```

Then just follow the  "sudo dpkg -i  etc etc etc"

Synaptic is a very useful tool and saves you doing all this commandline stuff, I think it's in the system menu somewhere in Gnome. Just click it and search for pan then select it and request install.

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=nolan-]Yeah dsnowman I got subscription to Newzbin :D 

I got unrar and par2 installed too and honestly don't mind commandline tools but automated sounds like heaven...

Right now wheres that download ![/QUOTE]

[http://ninan.sourceforge.net/](http://ninan.sourceforge.net/)

just download then uzip. The command to get it going is 

nohup ./ninancore.sh &

You just need to be in the ninan-x.x.x (ninan-1.0.2 in my case) directory thats made when you extract it.

dont use sudo, because the app is smart enough to know it shouldn't run as root.

---

### Post by nolan- on 2006-05-14
Hi snowman,

OK I done the command you said and it gave me this :
```
nol@nol-desktop:~/ninan-1.0.2$ nohup: appending output to `nohup.out'
nohup: cannot run command `./ninancore.sh': Permission denied
```
So I went to website and it said I had to do this :
```
chmod 755 ninancore.sh
```
So I did then I ran the previous command and it just seems to hang :
```
nol@nol-desktop:~/ninan-1.0.2$ nohup ./ninancore.sh &
[2] 6558
nol@nol-desktop:~/ninan-1.0.2$ nohup: appending output to `nohup.out'
```

It also says to export java "If you have installed java at /usr/local/java1.4 then this line will do the trick: export JAVA_HOME=/usr/local/java1.4"

The only place I find Java so far in /usr is at /usr/share/java now i'm pretty much certain that this is the wrong place to export but I done this anyways :
```
export JAVA_HOME=/usr/share/java
``` 

And no surprises, it still hangs ](*,)   hehe

>>>>EDIT<<<<<

Getting jre-1_5_0_06-linux-i586.bin now, then I guess it *should* work.......

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=nolan-]Hi snowman,

OK I done the command you said and it gave me this :
```
nol@nol-desktop:~/ninan-1.0.2$ nohup: appending output to `nohup.out'
nohup: cannot run command `./ninancore.sh': Permission denied
```
So I went to website and it said I had to do this :
```
chmod 755 ninancore.sh
```
So I did then I ran the previous command and it just seems to hang :
```
nol@nol-desktop:~/ninan-1.0.2$ nohup ./ninancore.sh &
[2] 6558
nol@nol-desktop:~/ninan-1.0.2$ nohup: appending output to `nohup.out'
```

It also says to export java "If you have installed java at /usr/local/java1.4 then this line will do the trick: export JAVA_HOME=/usr/local/java1.4"

The only place I find Java so far in /usr is at /usr/share/java now i'm pretty much certain that this is the wrong place to export but I done this anyways :
```
export JAVA_HOME=/usr/share/java
``` 

And no surprises, it still hangs ](*,)   hehe

Any help welcome :D[/QUOTE]

type in terminal

java --version

the output should say something like jre1.5.0_06

If it dosn't then you need to be sure to install jre1.5.0_06 or set that version as your default.

let me go find a usefull command for that.

---

### Post by DSn0wMan on 2006-05-14
sudo update-alternatives --config java

will allow you to select the version of java you are using.

if java15 isn't there then you need to install it.

try this wikki [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

Thats the one that helped me get all things java working.

---

### Post by Jim Hill on 2006-05-14
Hi Nolan:
Apparently, ubuntu does not start at the desktop when starting in the Terminal

jim@ubuntu:~$

I tried to move to desktop without success, then tried your commands:

jim@ubuntu:~$ -desktop
bash: -desktop: command not found
jim@ubuntu:~$ desktop
bash: desktop: command not found
jim@ubuntu:~$
jim@ubuntu:~$ sudo dpkg -i pan_0.14.2.97-2ubuntu3_i386.de
Password:
dpkg: error processing pan_0.14.2.97-2ubuntu3_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pan_0.14.2.97-2ubuntu3_i386.de
jim@ubuntu:~$


Jim

---

### Post by nolan- on 2006-05-14
Hi dsnowman,
Thanks for all the help so far man.
OK I went to the Java Wiki and followed it so now I get :
```
nol@nol-desktop:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
```
I also done :
```
export JAVA_HOME=/usr/local/jre1.5.0_06/
```
(finally the right place, DOH!)
BUT, I still get this :
```
nol@nol-desktop:~/ninan-1.0.2$ nohup ./ninancore.sh &
[1] 6687
nol@nol-desktop:~/ninan-1.0.2$ nohup: appending output to `nohup.out'
```
It hangs there, if I press enter I get :
```
[1]+  Done                    nohup ./ninancore.sh
```
If I enter the command again it doesn't hang but returns this:
```
nol@nol-desktop:~/ninan-1.0.2$ nohup ./ninancore.sh &
[2] 6735
[1]   Done                    nohup ./ninancore.sh
nohup: appending output to `nohup.out'
```


Does this command "nohup ./ninancore.sh &" just fire up ninan when things are working or is there another command?
The install guide is a bit vague......

OK pal it's bedtime for me i've been up 20 hours now :( 
I'll check back tomorrow, again thanks for the help!

NoL

---

### Post by sophtpaw on 2006-05-14
[QUOTE=Jim Hill]I've checked the Ununtu desktop and Firefox browser, and can't find a newsgroup reader. Where should I look?
Jim[/QUOTE]
Opera offers a non-fuss all-in-one integrated browser/email/newsgroup-reader/chat client.

Otherwise, Thuderbird great email client aswell has integrated newsgroup reader. Two clicks away in Synaptics. System/Administration/Synaptic Package Manager

sophtpaw

---

### Post by nolan- on 2006-05-14
[QUOTE=Jim Hill]Hi Nolan:
Apparently, ubuntu does not start at the desktop when starting in the Terminal

jim@ubuntu:~$

I tried to move to desktop without success, then tried your commands:

jim@ubuntu:~$ -desktop
bash: -desktop: command not found
jim@ubuntu:~$ desktop
bash: desktop: command not found
jim@ubuntu:~$
jim@ubuntu:~$ sudo dpkg -i pan_0.14.2.97-2ubuntu3_i386.de
Password:
dpkg: error processing pan_0.14.2.97-2ubuntu3_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pan_0.14.2.97-2ubuntu3_i386.de
jim@ubuntu:~$


Jim[/QUOTE]


Hi Jim, Did you just miss the "b" off the end of the filename?
dpkg: error processing pan_0.14.2.97-2ubuntu3_i386.de[COLOR="Red"]b[/COLOR]

When using the commandline pressing TAB autocompletes most things like available filenames and directories etc....

So if you do this:
 ```
sudo dpkg -i pan[COLOR="Red"]<PRESS TAB HERE[/COLOR]
```

It should autocomplete the line for you...

Hope this helps, OK man bedtime :D

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=nolan-]Does this command "nohup ./ninancore.sh &" just fire up ninan when things are working or is there another command?
The install guide is a bit vague......

OK pal it's bedtime for me i've been up 20 hours now :( 
I'll check back tomorrow, again thanks for the help!

NoL[/QUOTE]

./ninancore.sh just gets it going. 

to use it point you browser to:

[http://127.0.0.1:9090/ninan](http://127.0.0.1:9090/ninan)

---

### Post by Jim Hill on 2006-05-14
Hi Nolan:
Entering the command correctly still gives problems

jim@ubuntu:~$ sudo dpkg -i pan_0.14.2.97-2ubuntu3_i386.deb
dpkg: error processing pan_0.14.2.97-2ubuntu3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pan_0.14.2.97-2ubuntu3_i386.deb
jim@ubuntu:~$

I tried the Tab key as you suggested.  I hear a beep from inside the computer, but that's it. No autocorrect.  I didn't know computers still had internal speakers.

jim@ubuntu:~$ -1 pan
bash: -1: command not found

How do you generate the boxes around code?

---

### Post by DSn0wMan on 2006-05-14
```
 some code 
```


Looks like you just use the work code in square to start, and then close with a slash. Hopefully this shows up.

'['code] your code [/code] only leave out the quotes

---

### Post by nolan- on 2006-05-15
Hello again,
Got Ninan going, it's a neat little program!
Be great for alternative to remote access if you ever needed it eh?

Cheers for showing me it dsnowman.......and for the help :p

---

### Post by nolan- on 2006-05-15
[QUOTE=Jim Hill]Hi Nolan:
Entering the command correctly still gives problems[/QUOTE]

Hi Jim,
Seriously, use synaptic it's in the system menu. Just find it and click on it and then search for pan. Find the package called Pan and right click on it and mark for installation. Then click Apply button at top. It will then install.
It's really easy. 

Following install start it by typing pan in a terminal or clicking the icon that should now be in one of the menus in top left corner. As I said before i'm on Kubuntu so I don't know exactly where it will be but it will be easy to find !!

Good Luck

---

### Post by DSn0wMan on 2006-05-15
[QUOTE=nolan-]Hello again,
Got Ninan going, it's a neat little program!
Be great for alternative to remote access if you ever needed it eh?

Cheers for showing me it dsnowman.......and for the help :p[/QUOTE]

Now if you are really lazy like me, just add greasemonkey, and ninan oneclick to firefox, and you dont even have to cut and paste post ID's. Ninan oneclick will put little links next to the posts that will add it to the download queue.

One other thing that I thought was cool. In ninan 1.0.2 it finds the par file first, then downloads the rar files, runs the parcheck as the files download, and if everything is ok it skips downloading the other par files.

---

### Post by Darrena on 2006-05-17
I have never seen Ninan before but it looks really nice.  I will definetly take a look at that tonight.

As others have pointed out Pan is a great traditional newsreader and the author  is now releasing (almost weekly) new versions working towards a stable 1.0 release.  These new versions have all the features you could want in a standard Newsreader especially if you are used to Agent.  You can download these weekly beta's from [http://pan.rebelbase.com](http://pan.rebelbase.com)   If you are running Breezy the deb's posted do not currently work on Breezy but a fixed version should be uploaded soon or I can send it to you directly.

---

### Post by gurgle on 2006-06-25
1 vote for Sabnzbd

---

### Post by FredB on 2006-06-25
[QUOTE=Darrena]I have never seen Ninan before but it looks really nice.  I will definetly take a look at that tonight.[/QUOTE]

So will I. I've never heard of it before !

> 
As others have pointed out Pan is a great traditional newsreader and the author  is now releasing (almost weekly) new versions working towards a stable 1.0 release.

Yes almost. Pan 0.101 is out. I hope 1.0 final will be out before end of this year. I let my computer built it.

> 
  These new versions have all the features you could want in a standard Newsreader especially if you are used to Agent.  You can download these weekly beta's from [http://pan.rebelbase.com](http://pan.rebelbase.com)   If you are running Breezy the deb's posted do not currently work on Breezy but a fixed version should be uploaded soon or I can send it to you directly.

It is still a work in progress, so expects annoying and / or crashing bugs.

---

### Post by kopolee11 on 2006-06-25
[QUOTE=Jim Hill]Hi Nolan:
Apparently, ubuntu does not start at the desktop when starting in the Terminal

jim@ubuntu:~$

I tried to move to desktop without success, then tried your commands:

jim@ubuntu:~$ -desktop
bash: -desktop: command not found
jim@ubuntu:~$ desktop
bash: desktop: command not found
jim@ubuntu:~$
jim@ubuntu:~$ sudo dpkg -i pan_0.14.2.97-2ubuntu3_i386.de
Password:
dpkg: error processing pan_0.14.2.97-2ubuntu3_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pan_0.14.2.97-2ubuntu3_i386.de
jim@ubuntu:~$


Jim[/QUOTE]

I don't really know any good newreaders, but I can help you out with the terminal. When you start the terminal you always start in your home directory. To see what your contents in your home directory are type ```
ls
```

You should then see a blue directory marked Desktop. To go into the Desktop, type ```
cd Desktop
``` 

Then press ```
ls
``` again, and see if you see pan_0.14.2.97-2ubuntu3_i386.deb. 

I hoped that helped you, and if you want more help on the terminal, go right [here.]("http://linuxcommand.org/")

---

### Post by fnandocc on 2006-08-07
> **nolan- said:**
> 

A GUI for par2 would be nice, OK stop me i'm rambling hehe

Get gpar if you want a par2 GUI. 
[http://sourceforge.net/project/showfiles.php?group_id=30568&package_id=171020](http://sourceforge.net/project/showfiles.php?group_id=30568&package_id=171020)
you will need the libpar library
[http://sourceforge.net/project/showfiles.php?group_id=30568&package_id=171019](http://sourceforge.net/project/showfiles.php?group_id=30568&package_id=171019)
Get the .deb and you are done.

---

### Post by yeehawjared on 2006-09-25
nice... that gui is awesome.  thanks for listing the .deb's

---

