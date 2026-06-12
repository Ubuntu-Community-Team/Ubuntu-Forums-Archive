---
title: "What path sudo use?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by B-Con on 2007-09-20
I like to keep custom scripts I've written in my own folder: /home/b-con/bin. However, sudo seems unable to ever find them.

```
b-con@beacon:~$ echo $PATH
/home/b-con/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
```
b-con@beacon:~$ sudo echo $PATH
/home/b-con/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

I don't get it, why can't sudo ever find any of the scripts in /home/b-con/bin?

---

### Post by jordanmthomas on 2007-09-20
Hate to ask the dumb question, but are yor scripts executable?
if not, chmod +x them.

**edit** also, it might be a good idea to put your custom directories at the *end* of your path so somebody can't put a malicious ls script in your personal bin folder and have it run.

---

### Post by jordanmthomas on 2007-09-20
Oh, also your path is not done correctly:
```
/home/b-con/bin:
```
You need a colon between con/ and bin

---

### Post by bodhi.zazen on 2007-09-20
As you can see, that echo command does not give you root's (sudo) path.

Try this :

> **sudo /bin/bash -c "echo $"PATH""**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

You can either add the directory to root's path or specify a path in your command (you can use an alias).

sudo sh /home/b-con/bin/<script>

---

### Post by B-Con on 2007-09-20
> **jordanmthomas said:**
> Oh, also your path is not done correctly:
```
/home/b-con/bin:
```
You need a colon between con/ and bin
Um, /home/b-con/bin is the full path I want to use.

> **bodhi.zazen said:**
> You can either add the directory to root's path or specify a path in your command (you can use an alias).
I already have 
```
export PATH=/home/b-con/bin:"${PATH}"
```
in /etc/profile. If I "$ sudo su" into root and "# echo $PATH" then it shows the path with /home/b-con/bin added to it. How else could I add my path to root's PATH?

---

### Post by bodhi.zazen on 2007-09-20
I am not an expert on sudo, so bear with me.

You can *try* adding the path you want to /root/.bashrc as well as /root/profile.

However, I believe sudo is compiled in Ubuntu with the --with-secure-path option, meaning, in english, you can not change the path sudo uses without recompiling sudo.

A work around is to add a link to your apps on the path.

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797)

I have told you more then I know, perhaps someone with more knowledge will pipe in.

---

### Post by jordanmthomas on 2007-09-20
> **B-Con said:**
> Um, /home/b-con/bin is the full path I want to use.


Woops, it was late and there were many slashes.  My bad.  :|

Also, it seems bodhi.zazen might be right about Ubuntu's sudo just being off a little bit.  Here on arch, sudo uses my own PATH and it works as expected with my personal bin directory.

```
[FONT="Courier New"]
&#9484;&#9472;(**jordan@ttyfscker:pts/0**)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~/projects/jshell)&#9472;&#9488;
&#9492;&#9472;(22:23:%)&#9472;&#9472; sudo echo $PATH                                                                                                                                                                       &#9472;&#9472;(Thu,Sep20)&#9472;&#9496;
/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/usr/local/bin:/opt/java/bin:/opt/java/jre/bin:/opt/kde/bin:/opt/mozilla/bin:/opt/qt/bin:[COLOR="Red"]/home/jordan/bin[/COLOR]
&#9484;&#9472;(**jordan@ttyfscker:pts/0**)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~/projects/jshell)&#9472;&#9488;
&#9492;&#9472;(22:25:%)&#9472;&#9472; su -                                                                                                                                                                                  &#9472;&#9472;(Thu,Sep20)&#9472;&#9496;
Password: 

[**root@ttyfscker ~**]# echo $PATH
/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/usr/local/bin:/opt/java/bin:/opt/java/jre/bin:/opt/kde/bin:/opt/mozilla/bin:/opt/qt/bin
[root@ttyfscker ~]#[/FONT]
```

---

### Post by crazee64 on 2007-09-20
you could add symlinks in /usr/local/bin to your ~/bin scripts.
so: ln -s /home/b-con/bin/blah.sh /usr/local/bin/blah.sh
That way you can have all the scripts you want to keep and maintain in ~/bin but only "install" certain ones?

---

### Post by B-Con on 2007-11-24
> **crazee64 said:**
> you could add symlinks in /usr/local/bin to your ~/bin scripts.
so: ln -s /home/b-con/bin/blah.sh /usr/local/bin/blah.sh
That way you can have all the scripts you want to keep and maintain in ~/bin but only "install" certain ones?
(Forgot to say...)

Hey, that's an interesting idea. Thanks. :)

---

