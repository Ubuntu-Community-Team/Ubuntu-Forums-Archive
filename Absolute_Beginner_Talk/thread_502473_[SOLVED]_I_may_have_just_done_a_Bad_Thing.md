---
title: "[SOLVED] I may have just done a Bad Thing"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-07-16
In the process of installing a program ([QtTube]("http://ubuntuforums.org/showthread.php?t=494812")) to download YouTube files, I think I may have deleted my /usr/local/bin directory and replaced it with a text file. I ran the command listed here:

[https://wiki.ubuntu.com/QtTube/Installation/Feisty](https://wiki.ubuntu.com/QtTube/Installation/Feisty)

Here is the output of that command:
```
adam@AUL:~$ sudo aptitude -y install python-qt4 && cd ~/Desktop && wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl && sudo mv ./youtube-dl /usr/local/bin && sudo chmod +x /usr/local/bin/youtube-dl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libmysqlclient15off libqt4-core libqt4-gui libqt4-qt3support libqt4-sql 
  libsqlite0 mysql-common python-elementtree python-sip4 qt4-qtconfig 
The following NEW packages will be installed:
  libmysqlclient15off libqt4-core libqt4-gui libqt4-qt3support libqt4-sql 
  libsqlite0 mysql-common python-elementtree python-qt4 python-sip4 
  qt4-qtconfig 
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 7456kB/13.6MB of archives. After unpacking 41.4MB will be used.
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com feisty/main libsqlite0 2.8.17-1build2 [179kB]
Get:2 http://us.archive.ubuntu.com feisty/main mysql-common 5.0.38-0ubuntu1 [53.7kB]
Get:3 http://us.archive.ubuntu.com feisty/main libmysqlclient15off 5.0.38-0ubuntu1 [1835kB]
Get:4 http://us.archive.ubuntu.com feisty/main libqt4-sql 4.2.3-0ubuntu3 [320kB]
Get:5 http://us.archive.ubuntu.com feisty/main libqt4-qt3support 4.2.3-0ubuntu3 [1273kB]
Get:6 http://us.archive.ubuntu.com feisty/universe python-elementtree 1.2.6-10ubuntu2 [30.2kB]
Get:7 http://us.archive.ubuntu.com feisty/main python-sip4 4.5-0ubuntu2 [132kB] 
Get:8 http://us.archive.ubuntu.com feisty/main python-qt4 4.1-0ubuntu6 [3535kB] 
Get:9 http://us.archive.ubuntu.com feisty/universe qt4-qtconfig 4.2.3-0ubuntu3 [98.8kB]
Fetched 7456kB in 35s (209kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package libsqlite0.
(Reading database ... 118786 files and directories currently installed.)
Unpacking libsqlite0 (from .../libsqlite0_2.8.17-1build2_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.38-0ubuntu1_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-core.
Unpacking libqt4-core (from .../libqt4-core_4.2.3-0ubuntu3_i386.deb) ...
Selecting previously deselected package libqt4-gui.
Unpacking libqt4-gui (from .../libqt4-gui_4.2.3-0ubuntu3_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.2.3-0ubuntu3_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.2.3-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-elementtree.
Unpacking python-elementtree (from .../python-elementtree_1.2.6-10ubuntu2_all.deb) ...
Selecting previously deselected package python-sip4.
Unpacking python-sip4 (from .../python-sip4_4.5-0ubuntu2_i386.deb) ...
Selecting previously deselected package python-qt4.
Unpacking python-qt4 (from .../python-qt4_4.1-0ubuntu6_i386.deb) ...
Selecting previously deselected package qt4-qtconfig.
Unpacking qt4-qtconfig (from .../qt4-qtconfig_4.2.3-0ubuntu3_i386.deb) ...
Setting up libsqlite0 (2.8.17-1build2) ...

Setting up mysql-common (5.0.38-0ubuntu1) ...
Setting up libmysqlclient15off (5.0.38-0ubuntu1) ...

Setting up libqt4-core (4.2.3-0ubuntu3) ...

Setting up libqt4-gui (4.2.3-0ubuntu3) ...

Setting up libqt4-sql (4.2.3-0ubuntu3) ...

Setting up libqt4-qt3support (4.2.3-0ubuntu3) ...

Setting up python-elementtree (1.2.6-10ubuntu2) ...

Setting up python-sip4 (4.5-0ubuntu2) ...

Setting up python-qt4 (4.1-0ubuntu6) ...

Setting up qt4-qtconfig (4.2.3-0ubuntu3) ...

--17:26:22--  http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl
           => `youtube-dl'
Resolving www.arrakis.es... 212.59.199.45
Connecting to www.arrakis.es|212.59.199.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,191 (15K) [text/plain]

100%[====================================>] 15,191        31.56K/s             

17:26:23 (31.49 KB/s) - `youtube-dl' saved [15191/15191]

chmod: cannot access `/usr/local/bin/youtube-dl': Not a directory
```

What did I do wrong? Is there a way to reverse it?

---

### Post by wolfen69 on 2007-07-16
i dont think anything serious happened. but you might want to try-downtube. it's a great youtube downloader. it's in synaptic.

---

### Post by wolfen69 on 2007-07-16
give downtube a try, and if you like it, just:
```
sudo apt-get remove qttube 
```

---

### Post by hackle577 on 2007-07-16
From what I understand, it was supposed to install the youtube-dl file into the directory /usr/local/bin/youtube-dl but somehow failed to create that directory and so overwrote /usr/local/bin. So now, for me, /usr/local/bin is not a directory, but a text file with the youtube-dl script in it. That can't be right? Right?

---

### Post by hackle577 on 2007-07-16
sudo apt-get remove qttube does nothing

---

### Post by pak33m on 2007-07-16
hackle577,

I copied (in a Feisty virtualbox image) and ran the command from the wiki just like you did but with no errors.

Did you look to see if the path to /usr/local/bin still exists either by browsing to it or in the Terminal? If it is there then you sould not have anything to worry about.  If you look and the youtube-dl file is not there then that would be your problem beacsue the command is trying to apply permissions on a file that in not there.

---

### Post by hackle577 on 2007-07-16
The directory /usr/local/bin does not exist. However, navigating to /usr/local reveals a *file* named "bin", the contents of which is the youtube-dl script. The youtube-dl script also exists in the /usr/bin directory, if that helps.

What I'm thinking happened is that, when the command tried to download the youtube-dl file, it tried to put it in the /usr/local/bin/youtube-dl directory, but since there was no "youtube-dl" folder in /usr/local/bin, it overwrote that entire directory (/usr/local/bin) with the youtube-dl script renamed as "bin".

---

### Post by jasonlfunk on 2007-07-16
My guess is that you didn't have a /usr/local/bin directory for some reason so the command
```

sudo mv ./youtube-dl /usr/local/bin

```
worked and created a bin file in /usr/local. Then when you did
```

 sudo chmod +x /usr/local/bin/youtube-dl

```
it failed because the bin directory doesn't exist (and didn't to begin with).

The good news: If I'm right then you didn't lose anything at all because that directory wasn't there to begin with.

---

### Post by hackle577 on 2007-07-16
You may be right, but the directory /usr/local/bin sounds familiar and I suspect that I did have that directory beforehand. Is my theory plausible? That the youtube-dl script overwrote the entire /usr/local/bin directory? Can that even happen?

---

### Post by Majorix on 2007-07-16
You didn't delete /usr/local/bin directory. Its just that you created a FILE called bin under /usr/local. Please check if I am right.

---

### Post by hackle577 on 2007-07-16
Yes, Majorix, you are right. But I think maybe the command overwrote the /usr/local/bin *directory* and made it a *file*. I do not currently have a dir /usr/local/bin , but I'm about 60% sure I used to.

---

### Post by jasonlfunk on 2007-07-16
It may sound familiar because there are other bin directories such as /usr/bin/ and /bin/.   Nothing is installed there by Ubuntu by default. Whoever wrote that script forgot a backslash. 

And no, you cannot overwrite a directory with the mv command that you did.

---

### Post by hackle577 on 2007-07-16
OK, whew! That makes me feel a bit better. Damn do I need to brush up on my CLI or what... Ubuntu has spoiled me.

---

### Post by jasonlfunk on 2007-07-16
For Example:

```

jason@PC-3:/usr/local/bin$ ls                           #1
jason@PC-3:/usr/local/bin$ cd /
jason@PC-3:/$ sudo touch test                        #2
Password:
jason@PC-3:/$ sudo mv test /usr/local/bin    #3
jason@PC-3:/$ cd /usr/local/bin/
jason@PC-3:/usr/local/bin$ ls                           #4
test
jason@PC-3:/usr/local/bin$ 

```

1) My /usr/local/bin/ directory is empty. 
2) I create a file 
3) Move it to the /usr/local/bin (The same command that you did.)
4) It just moves the file, doesn't replace the directory.

---

### Post by hackle577 on 2007-07-16
Thanks :)

---

