---
title: "How do I run this java-based program?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by b9anders on 2007-01-23
A program I quite like in windows which is also available for Linux is the gurps character sheet (gcs) [found at [http://www.roleplayer.com/Welcome.html]](http://www.roleplayer.com/Welcome.html]), which requires runtime java 5. I have installed JRE 6 using the guidelines at ubuntuguide.org and unpacked the installation file for gcs. Only problem is now I don't quite know how to start up the program. The .exe file I am habituated to in windows obviously doesn't work and I don't think I should be emulating it with wine to run a program that is supposed to work in linux.

any takers?

---

### Post by stijn_pol on 2007-01-23
You should search for a .jar-file. You can compare this to a windows .exe file. To run it, type:

```
 sudo java -jar filename.jar
```

---

### Post by b9anders on 2007-01-23
thanks. I got this error message in the terminal when opening it though:

Failed to load Main-Class manifest attribute from itext.jar

Is that a problem with the package I downloaded or something I can fix?

---

### Post by stijn_pol on 2007-01-23
The manifest is a part of the jar-file so I think the jar may be corrupted.
Maybe download it again...

---

### Post by b9anders on 2007-01-23
I tried it with different versions of the download now and they say the same thing. Too bad, I thought this was one program I am used to that would run just fine on linux.

---

### Post by b9anders on 2007-01-23
I get the exact same error message typing in the same command but with bogus names for the file so it might be that it simply doesn't recognise the filename(?).

---

### Post by compmodder26 on 2007-01-23
I just downloaded and tested it and it works fine for me.  After you extract the archive and open the gcs folder, you just need to execute the "gcs" file.  This can be done graphically by double clicking the file and choosing "Run" from the resulting dialog, or by typing

```
./gcs
```

At the command line.

---

### Post by phossal on 2007-01-23
itext is an extension, too. I don't know the program in question, but if other solutions don't work, you may have to add itext to your <path>/jre/lib/ext folder.

---

### Post by meng on 2007-01-23
Thanks for the link! I thought SJG had been jealously guarding their "copyright" to GURPS character creation, hence the lack of character generators (except the ones you pay for) but this looks good.

---

### Post by stijn_pol on 2007-01-23
Just remember, never give up! (If it does work already)
I should also have checked it out to better help you out. 
Anyway, now you know how to run jar's...:)

---

### Post by b9anders on 2007-01-23
> **compmodder26 said:**
> I just downloaded and tested it and it works fine for me.  After you extract the archive and open the gcs folder, you just need to execute the "gcs" file.  This can be done graphically by double clicking the file and choosing "Run" from the resulting dialog, or by typing

```
./gcs
```

At the command line.

I tried this, but it said:

The currently installed version of Java is 1.4.2.
This software requires Java version 1.5 or greater.

Which I con't understand. I've downloaded java 1.5 via automatix2 so unless that failed without me realising it, I just don't understand how this could happen.

---

### Post by b9anders on 2007-01-23
> **meng said:**
> Thanks for the link! I thought SJG had been jealously guarding their "copyright" to GURPS character creation, hence the lack of character generators (except the ones you pay for) but this looks good.

SGJ generally have a pretty generous web policy. They even link to free programs like this from their own website.

---

### Post by meng on 2007-01-23
> **b9anders said:**
> I tried this, but it said:

The currently installed version of Java is 1.4.2.
This software requires Java version 1.5 or greater.

Which I con't understand. I've downloaded java 1.5 via automatix2 so unless that failed without me realising it, I just don't understand how this could happen.

Probably your system is using another Java rather than Sun's. Try this:
sudo update-alternatives --config java

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by phossal on 2007-01-23
If you find your new Java isn't being found, you can install it. I recommend downloading JDK 6, too. Anyway, [basic instructions for handling the JDK/JRE and adding them to update-alternatives]("http://ubuntuforums.org/showthread.php?t=332674")

---

### Post by b9anders on 2007-01-26
So, I re-installed xubuntu because of the java and a few other installation issues and decided to give this another go.

> **compmodder26 said:**
> I just downloaded and tested it and it works fine for me.  After you extract the archive and open the gcs folder, you just need to execute the "gcs" file.  This can be done graphically by double clicking the file and choosing "Run" from the resulting dialog, or by typing

```
./gcs
```

At the command line.

Now, instead of the former error message, I get:

```
./gcs: 42: java: not found
```

And it still won't load.:(

---

### Post by phossal on 2007-01-26
What is the output to the two following commands:

```
sudo update-alternatives --display java
```
```
echo $JAVA_HOME
```

---

### Post by b9anders on 2007-01-28
Hi phossal, sorry for the late reply. Anyway, here goes:

> **phossal said:**
> What is the output to the two following commands:

```
sudo update-alternatives --display java
```

"No alternatives for java."

> ```
echo $JAVA_HOME
```

Nothing. Just a blank line.

---

### Post by phossal on 2007-01-28
Here is what you want: 
```
sudo apt-get install sun-java6-jdk
```

I can't understand why, but there is no Java configured for your system. You'll need to download it using the command above. With the package installed, please post the output to the previous commands.

---

### Post by b9anders on 2007-01-28
> **phossal said:**
> Here is what you want: 
```
sudo apt-get install sun-java6-jdk
```

I can't understand why, but there is no Java configured for your system. You'll need to download it using the command above. With the package installed, please post the output to the previous commands.

I got the following use the command above (I use a Danish version):

```
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Reading state information... Færdig
E: Kunne ikke finde pakken sun-java6-jdk
```

I can't be sure of the exact wording, but it would translate to something along the lines of:

```
Reading packagelists... done.
Building dependencytree
Reading state information... done
E: Could't find package sun-java6-jdk
```

The output of the former commands is still the same.

---

### Post by phossal on 2007-01-28
[SIZE="1"]**[COLOR="#248"]1. Download Java Right to your *Desktop*[/COLOR]**[/SIZE]
Download the 32Bit JDK right from SUN.
You want this: [jdk-6-linux-i586.bin]("http://java.sun.com/javase/downloads/index.jsp")

Once it's downloaded, open a terminal window and:
```
cd ~/Desktop
sh jdk-6*.bin
```

Agree to the terms in the licensing agreement. The script will produce a file. Rename that file Java6.

---

### Post by b9anders on 2007-01-28
> **phossal said:**
> [SIZE="1"]**[COLOR="#248"]1. Download Java Right to your *Desktop*[/COLOR]**[/SIZE]
Download the 32Bit JDK right from SUN.
You want this: [jdk-6-linux-i586.bin]("http://java.sun.com/javase/downloads/index.jsp")

Once it's downloaded, open a terminal window and:
```
cd ~/Desktop
sh jdk-6*.bin
```

Agree to the terms in the licensing agreement. The script will produce a file. Rename that file Java6.

it produced a folder on the desktop. Is that the file you mean? And where to go from there?

---

### Post by phossal on 2007-01-28
Yep, the file it produced. Rename it Java6.

Then, do this:
```
sudo nautilus
```
Using the file browser, cut Java6, and place it in /usr/lib. That will give you /usr/lib/Java6.

Then do this:
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6/bin/java 300
```

Then tell me the output to the two commands we used before:
```
sudo update-alternatives --display java
java -version
```

---

### Post by b9anders on 2007-01-28
> **phossal said:**
> Yep. The file it produced. Rename it Java6.

Then, do this:
```
sudo nautilus
```
Using the file browser, cut Java6, and place it in /usr/lib. That will give you /usr/lib/Java6.

Then do this:
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6/bin/java 300
```

Then tell me the output to the two commands we used before:
```
sudo update-alternatives --display java
java -version
```

On the first, I got:

```
java - status is auto.
 link currently points to /usr/lib/Java6/bin/java
/usr/lib/Java6/bin/java - priority 300
Current `best' version is /usr/lib/Java6/bin/java.
```

and the second:

```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
b9anders@b9anders:~$ 
```

And the program is now running. :D 

Thanks a million. :mrgreen:

---

### Post by phossal on 2007-01-28
[COLOR="SlateGray"]**Awesome!** [/COLOR]Congrats! Have a good day! :D

---

