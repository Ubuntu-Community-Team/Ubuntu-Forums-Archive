---
title: "You can break Ubuntu :O("
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-07-05
I might be fast approaching the end of my Ubuntu experiment.
It looks like I'm heading for a second re-install, both events caused by the same problem....It appears that the automatic updates system can be easily compromised by a fool.

My automatic updates no longer works.

The little orange icon showm that I have updates to install, but when I click on it, I get this.

E: dpkg was interrupted.. You must manually run dpkg –configure -a to correct the problem.

So I try.

Setting up linux-restricted-modules-2.6.15-28-amd64-generic (2.6.15.12-28.2) ...
Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)


and then I get lost or give up because the website above doesn't appear to have anything to do with my problem.....or does it.


I suspect that my problem was caused by simply trying to add multimedia features to Open Office presentations.

I did some of these things.....below Getting Movie and Sound to work with Linux.

Isn't there a way to get paid support? If so, how? where?

Thanks in advance
Phil

Getting Movie and Sound to work with Linux
You can embed movies and sounds in documents and presentations. On UNIX systems, the Media Player requires the Java Media Framework API (JMF). The documentation accompanying JMF includes a list of formats and codecs that JMF can play.

Install Java
You can get a copy of Sun Java from [http://www.java.com](http://www.java.com)

Install Java Media Framework
Download jmf-2_1_1e-linux-i586.bin from [http://java.sun.com/products/java-media/jmf/](http://java.sun.com/products/java-media/jmf/).
To install the JMF files you need to make the file executable. Open a console window and type
chmod u+x jmf-2_1_1e-linux-i586.bin
Change to the directory containing jmf-2_1_1e-linux-i586.bin and run it
./jmf-2_1_1e-linux-i586.bin
Follow the onscreen instructions. Type “Yes” to accept the license. If you are only going to use Java Media Framework with OpenOffice.org, you can answer “No” to the other two questions.
Set the java user environment to identify the location of the Java Media Framework files. In the console window, type
export JMFHOME=/path_to/JMF-2.1.1e
export CLASSPATH=$JMFHOME/lib/jmf.jar::$JMFHOME/lib/sound.jar:.:${CLASSPATH}
export LD_LIBRARY_PATH $JMFHOME/lib:${LD_LIBRARY_PATH}

---

### Post by Outrunner on 2007-07-05
```
sudo dpkg –configure -a 
```

You can get paid support yes. Not sure where, though, but you can search for it yourself.

---

### Post by az on 2007-07-05
Run Synaptic and click on Fix Broken Packages.

---

### Post by Raineer on 2007-07-05
To be honest you need to go a little more step by step.  There is a heck of a chance you just have *one* bug that's not letting any of your installtions succeed.  Lets get the sudo apt-get upgrade working first, then go about the rest of it.

The instructions on the java page are tricky but they do work (I've done that myself when I needed version 5 instead of the version 6)

---

### Post by groeswenphil on 2007-07-05
sudo apt-get upgrade gave me this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Is there a plan B?

Phil

---

### Post by Raineer on 2007-07-05
What happens when you run 
```
sudo dpkg --configure -a
```

---

### Post by groeswenphil on 2007-07-06
It does this.....but none of the links make any sense.

Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by joe.turion64x2 on 2007-07-06
Can you open Synaptic and refresh the list of available software?

---

### Post by Nythain on 2007-07-06
what happens if you run
sudo aptitude clean
sudo aptitude update
sudo apt-get upgrade

---

### Post by moredhel on 2007-07-06
You could fix it by going into synaptic and finding the package and unselect it to be installed...

---

### Post by insane_alien on 2007-07-06
okay, i'll give you a run through for the java problem.

1/open that link in firefox or any other browser
2/scroll dow till you see 'J2SE 5.0 Documentation'. click download
3/accept the license agreement
4/check the box for 'J2SE(TM) Development Kit Documentation 5.0, English'
5/ hit the orange bar(either of them) to download.
6/ hit Alt+F2 and type 'gksudo nautilus' and enter your password
7/navigate to where you downloaded the file (probably /home/<your user/Desktop
8/copy and paste the file to /tmp (you must paste in the window you opened with gksudo)
9/right click on the file and select properties and then permissions
10/where it says owner and group change those both to root. 
11/ close the window and run dpkg --configure -a again.

that should get you going. 

most people don't install the documentation as it is for the development kit.

---

### Post by Old Pink on 2007-07-06
```
sudo dpkg -P -a && sudo apt-get clean
```

Then try from the beginning :)

---

### Post by KIAaze on 2007-07-06
The java site is not clear at all, so I just googled for the files:
[https://sdlc5b.sun.com/ECom/EComActionServlet;jsessionid=D9334CA1AF7F291165DADAF5AC6885F8]("https://sdlc5b.sun.com/ECom/EComActionServlet;jsessionid=D9334CA1AF7F291165DADAF5AC6885F8")
[edit]Well, ok, they seem to be in the  'J2SE 5.0 Documentation' section...[/edit]

Download them and place them in /tmp with root as owner.
To do this, use the following commands:

```
cd <directory where you downloaded the files to>
sudo chown root jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip
sudo chgrp root jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip
sudo cp  jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip /tmp

```
And then try to run
```
sudo dpkg --configure -a
```
again.

I don't know if it will work, but that's how I understand the message you got.

---

### Post by groeswenphil on 2007-07-06
Nythain......I still get E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


That's for all three suggestions.
Thanks,
Phil

---

### Post by az on 2007-07-06
> **groeswenphil said:**
> Nythain......I still get E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.



So?  Run 

sudo dpkg --configure -a

then.

---

### Post by az on 2007-07-06
I filed a bug.  Whether or not this happened here, I think it's an issue.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/124443](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/124443)

Binary package hint: dpkg

"dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

That message is quite cryptic to a non-technical user. As well, it does not specify that sudo must be used to successfully run the command. When it fails because of inadequate priviledges, they are frustrated and may give up, thinking their system is irrepairable.

Can that message be changed to do the following?:
1. Specify the preferred GUI method of fixing broken packages.
2. Specify that sudo (or root priviledges) needs to be used if run from the command-line.

---

### Post by KIAaze on 2007-07-06
> **groeswenphil said:**
> Nythain......I still get E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


That's for all three suggestions.
Thanks,
Phil

So what happens when you run this command again?
```
sudo dpkg --configure -a
```

Do you get this message:
> /tmp/jdk-1_5_0-doc.zip has been unpacked and installed.
You can now delete it, if you wish.

Or this message?:
> A current version of the J2SDK documentation is already installed.

This version will be left in place.

If you get none of them, and are still asked to "dpkg --configure -a", then please post the output of ```
sudo dpkg --configure -a
```.

Normally, you get the error message you had because the installation process couldn't find this file:
```
/usr/share/doc/sun-java5-jdk/html/index.html
```
And you didn't have any of the specified java zip files in /tmp.

If you're still stuck, try installing the package separately:
0)Make sure you have at least one of the 2 zip files from the java site in your /tmp directory.
1)Download it [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmultiverse%2Fs%2Fsun-java5%2Fsun-java5-doc_1.5.0-11-1ubuntu2_all.deb&md5sum=c27a5dfa41acf48795dd5b697f6fa18d&arch=all&type=main")
2-a)Run:
```
sudo dpkg -i sun-java5-doc_1.5.0-11-1ubuntu2_all.deb
```

2-b)If that doesn't work, try this:
(Make sure you have "unzip" installed, if not download the .deb package from packages.ubuntu.com and install it with "dpkg -i unzip_5.52-9ubuntu3_i386.deb".)
```
dpkg-deb --control sun-java5-doc_1.5.0-11-1ubuntu2_all.deb .
sudo ./postinst

```
And if this gives you any error messages post them here.

Note that this is not an optimal solution, but hopefully it will help you get past this problem.
In the worst case try:
```
sudo touch /usr/share/doc/sun-java5-jdk/html/index.html
```

Otherwise, I really don't know...

---

### Post by groeswenphil on 2007-07-07
Thanks.
I've bookmarked all of the above........................thing is, I think I've fixed it.
At least, last night all of my updates appeared to come through.

I think I did it by 'fix broken packages' in Synaptic
I'm pretty sure that I did this before and it didn't work, but this time it did.

Sometimes its as if things fix themselves given enough time.
Ubuntu gnomes at work in the background.

Thanks everybody.
Phil

---

### Post by groeswenphil on 2007-07-15
*You could fix it by going into synaptic and finding the package and unselect it to be installed.*

THAT appears to have done the trick.

Thing is though, now I haven't got java installed.

Now, should I try to install it again and if so, where from?
Phil

---

### Post by joe.turion64x2 on 2007-07-15
An easy way to  break Ubuntu (at least fo me) was to install the 2.6.20-16-generic kernel.

Joe.

---

