---
title: "Java in Firefox wont work"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by pakora on 2007-08-18
How do I get Java to work on Firefox?
I have Ubuntu Version 7.04




Background
Hi I have been using computers for nearly half my life. I have wanted to move over to linux for a really long time however I was rather partial to Gentoo and it took me a long time to get to know linux in and out, build a kernel and then install the x manager and all that stuff. Since I knew how to do things in windows faster I stuck with it. I acquired a laptop with no home so I spraypainted it black, installed Ubuntu and here I am!!! Whoo hooo!!!

LInux rules, this forum rules and hellz yeah!

---

### Post by taurus on 2007-08-18
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```
Now, restart firefox again and see if you have java plugins.

---

### Post by pakora on 2007-08-18
Thank you for your prompt response.

It worked however logmein.com didnt work and when i went to java.com to test if had java i was told this

Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0. Please click the button below to get the recommended Java for your computer.  

Version 6 Update 2 <--- What Java.com reccomends I get.

Any help would be highly appreciated. Thank you

---

### Post by taurus on 2007-08-18
Looks like it wants you to use the latest version.  In that case, you need to download it by hand from Sun's site and install it.  First, you need to remove the one that you have just installed so there won't be two versions on your machine.

```
sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-fonts
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by pakora on 2007-08-18
Thank you again for your help however I am facing a problem.

I thought you could only install .deb files

On the site they dont have any deb files and I dont know which one to download. Furthermore I dont even know the procedure to install a program other than the ones in Add/Remove.

:(

---

### Post by taurus on 2007-08-18
Just download the .bin (_not_ the rpm one) to your computer from Sun's site.  Change permissions so you can execute/run it.  Then, install it.

```
cd ~/Desktop
chmod 755 **filename**.bin
sudo ./**filename**.bin
sudo update-alternatives --config java
java -version
```
Replace **filename** with the actual filename of the Java version that you download.

---

### Post by capink on 2007-08-18
Try this and see if it solves your problems:

[http://ubuntuforums.org/showthread.php?t=522008]("http://ubuntuforums.org/showthread.php?t=522008")

---

### Post by aeronori on 2007-08-19
Hi all,

I have also started using Ubuntu just 2 days ago...

I have installed the Sun version 1.6 and also checked in the firefox by typing about:plugins in the browser. It seems to be updated there. I have also made the "Sun" as the default browser. I also have the IBM Blackdown 1.4.2. 

Inspite of this, I am unable to run two windows with Java script. I generally listen to songs online and in some sites we can make our own  playlist and then we "play", "stop", "pause" , "skip one song back" or "skip on song forward" . So the problem is that even though these buttons are visible in the java-window, some of the buttons are not operational.  I did not find any issues with this website in windows...

can you help me in fixing this problem.?

For eg...you can take the website [http://www.raaga.com/channels/worldmusic/movie/WM00037.html](http://www.raaga.com/channels/worldmusic/movie/WM00037.html) and select all the songs and play it. then u get a player which starts playing the songs but we cannot skip a song either backward or forward ....

thanks for ur help...

---

