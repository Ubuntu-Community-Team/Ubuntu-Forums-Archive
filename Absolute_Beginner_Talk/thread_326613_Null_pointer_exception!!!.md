---
title: "Null pointer exception???!!!"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Janahan on 2006-12-27
I have recently configured a dual boot with Windows XP Professional and Kubuntu. Everything was going great but when I download anything from azureus I get an error message saying there is a Null pointer exception.

Any help would be greatly appreciated

(btw. im a complete noob, try to keep language basic)

---

### Post by solarwind on 2006-12-27
> **Janahan said:**
> I have recently configured a dual boot with Windows XP Professional and Kubuntu. Everything was going great but when I download anything from azureus I get an error message saying there is a Null pointer exception.

Any help would be greatly appreciated

(btw. im a complete noob, try to keep language basic)


Hmmm. What do you mean when you download anything from asureus? You download stuff from their site? Or how? What were the steps you took?
Did you try to run it? If so, how did you try to run it?

---

### Post by Janahan on 2006-12-27
First i download a .torrent file from a website

Then i drag the torrent into the window and the download starts

Just after it starts i get a message saying 
[COLOR="Red"]Error Disk Read: Null pointer Exception[/COLOR]

---

### Post by solarwind on 2006-12-27
> **Janahan said:**
> First i download a .torrent file from a website

Then i drag the torrent into the window and the download starts

Just after it starts i get a message saying 
[COLOR="Red"]Error Disk Read: Null pointer Exception[/COLOR]


KK do this...

Open up a terminal

```
azureus
```
Or whatever the command is for your BT client. If you don't know the exact spelling, type the first few letters of it and hit tab a few times. It'll try to complete the command for you or list possible commands with those letters.

Copy and paste the output of the text in the terminal (when it's running and it gives you the error).

---

### Post by enopepsoo on 2006-12-27
You've gotta love those helpful error messages, eh?

---

### Post by wulfhound on 2007-03-13
> **Janahan said:**
> I have recently configured a dual boot with Windows XP Professional and Kubuntu. Everything was going great but when I download anything from azureus I get an error message saying there is a Null pointer exception.

Any help would be greatly appreciated

(btw. im a complete noob, try to keep language basic)

I think that means that there's something wrong with the torrent file or tracker itself and not with Azureus. Restart Azureus and the torrent and see how far you get.

Sand

---

### Post by vester on 2007-04-02
I'm not sure if this is a tracker problem, i tried on my windows machine and same tracker worked. I'll try to install by hand and see if it still happens.

---

### Post by justin whitaker on 2007-04-02
I remember seeing a bunch of errors related to Java in the bug lists on Launchpad....maybe this is one of them?

---

### Post by thawkth on 2007-04-09
I can say it's definitely not a tracker issue and I get the same error.

I've tried it with several different torrents.

The message azureus gives is Null Pointer Exception/Disk read Error.

Usually I end up having to force quit azureus to make it actually go away.

I'll try to paste the error message if I can...

---

### Post by richaoj on 2007-05-04
i had a similar problem.  i don't think azureus plays to well with eclipse (=open source java).  I installed sun-java 5 and have not had a problem since.  i've also found downloads alot faster after having installed sun-java.

---

### Post by alecthunder on 2007-05-09
I have the same problem. I attached a JPG to show you how it looks (my Azureus is german btw.) This has nothing to do with Eclipse, which is a IDE for developers. Right now I'm installing sun java 6 and I hope it'll fix this.

PS: NullPointerEx is weak ;)

edit: I finished installing sun java 6, everything looks fine so far. I had to uninstall the 'gij' packages, because when I entered 'java -version' into the terminal, gij reported java 1.4.2. After a fresh restart, 'java -version' reports:

> alex@****:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


Uninstalling gij also forced me to uninstall Eclipse, which sucks, but that is another topic.

---

### Post by Sarteck on 2007-05-25
> **alecthunder said:**
> I have the same problem. I attached a JPG to show you how it looks (my Azureus is german btw.) This has nothing to do with Eclipse, which is a IDE for developers. Right now I'm installing sun java 6 and I hope it'll fix this.

PS: NullPointerEx is weak ;)

edit: I finished installing sun java 6, everything looks fine so far. I had to uninstall the 'gij' packages, because when I entered 'java -version' into the terminal, gij reported java 1.4.2. After a fresh restart, 'java -version' reports:



Uninstalling gij also forced me to uninstall Eclipse, which sucks, but that is another topic.

I would also like to report that installing sun java 6 over gij worked for me, so far (three days, no errors).

---

### Post by colsandurz on 2007-07-01
So if this is aproblem with azureus are there any other good bit torrent clients out there?  I can't stand bit tornado or the original bit torrent...

---

### Post by WinterWeaver on 2007-07-01
I' use Azureus in the past, and I confirm 2 things.

1 - installing Java helps a lot
2 - Azureus is a most extremely irritating program to use.

Now I'm using KTorrent, and I suggest you give it a go. It's not as Advanced as Azureus, but it works super good!

WW

---

### Post by colsandurz on 2007-07-01
but you can't use KTorrent if you use GNOME right?

---

### Post by Auria on 2007-07-01
> **colsandurz said:**
> but you can't use KTorrent if you use GNOME right?

yes you can, it will only be longer to open and not look like other apps, but it should work anyway

---

### Post by dixelpixel on 2007-07-07
Hi,

Thanks for all help so far in the thread. I have the same problem with Azureus. However, looking trough Synaptic it seems I already have all packages associated with Sun Java 6.

Could someone suggest what I need to do next?

Thanks,

..dxp...

---

### Post by viciousvex on 2007-08-30
Hi!

If you want to run Azureus with the sun-java-6 packages (which can coexist with the free java implementation in Ubuntu) then edit the file

/usr/bin/azureus

Change the last exec statement from:

exec **java** -Djava.library.path=/usr/lib/jni:/usr/lib \
        -Dgnu.gcj.runtime.VMClassLoader.library_control=never \
        -Dazureus.install.path=$dir \
        -classpath /usr/share/java/Azureus2.jar:$CP \
        org.gudy.azureus2.ui.swt.Main "$@"

to

exec **/usr/lib/jvm/java-6-sun/jre/bin/java** -Djava.library.path=/usr/lib/jni:/usr/lib \
        -Dgnu.gcj.runtime.VMClassLoader.library_control=never \
        -Dazureus.install.path=$dir \
        -classpath /usr/share/java/Azureus2.jar:$CP \
        org.gudy.azureus2.ui.swt.Main "$@"

where /usr/lib/jvm/java-6-sun/jre/bin/java is the path to your installed Sun Java VM.
You're then using the Sun Java Runtime Environment and things go a lot faster.

I tried this on Ubuntu Feisty 7.04.

Regards
vex

---

### Post by wormser on 2007-08-30
I had a lot of problems with Azureus until I follow the directions in this [post]("http://ubuntuforums.org/showpost.php?p=1680674&postcount=13").  The problem is that the Ubuntu Repository does not have the latest version.  This might have changed or will soon.

> Here is what solved it for me.

Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

---

### Post by aitorcalero on 2007-08-30
> **viciousvex said:**
> Hi!

If you want to run Azureus with the sun-java-6 packages (which can coexist with the free java implementation in Ubuntu) then edit the file

/usr/bin/azureus

...
vex

This is a very complex way to make Azureus work :-?. It is far more easier to properly configure java through "alternatives" or its GUI partner GAlternatives (which can be installed through Synaptic). Here you can choose which is the default java version;
```

 sudo update-alternatives --config java 

```
Then simply follow instructions and select java version.

---

### Post by mckryptyk on 2007-08-30
colsandurz :

You should try Ktorrent. I have hear a lot of good things about it on the forums.

I don't know anything more about it but people have said that it has the same features as azureus but without the bloated memory consumption.

The downside I can see to using it might be that it will install some kde libraries and some people don't like to mix their libraries together :confused:

---

### Post by viciousvex on 2007-08-30
> **aitorcalero said:**
> 
```

 sudo update-alternatives --config java 

```
Then simply follow instructions and select java version.

Nice hint!

The only negative impact is that these settings affect all installed java applications. But you're right, it's a bit more easy.

Regards
vex

---

