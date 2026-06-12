---
title: "Moving to Ubuntu, and some heavy questions"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by FritoDoom on 2008-04-11
Greetings everyone!

I'm looking at converting my computer to a dual-boot Windows XP/Ubuntu machine for some light programming work. Before I do this, I have some questions.

Can Ubuntu mount & access a FAT32 partition? My plan is to partition my HD three ways: XP, Ubuntu, and a small 'no-man's-land' partition to use for transferring data between the two. I'm leery of accessing the Windows partition with Ubuntu until I have a better idea of what I'm doing.

Will the current Java SDK run on Ubuntu? And can someone recommend a good Java IDE for Linux/Ubuntu?

My last question is a bit complicated. I have a Seagate USB external hard drive that I'm running off a PCI USB extension card. I'd like to be able to access the external via Ubuntu, but I have no idea how you'd go about doing that.

Apologies for the questions. It's a big plunge to make!

---

### Post by sancho panza on 2008-04-11
Ubuntu automatically detects and mounts NTFS and FAT partitions on bootup. Read more [here]("http://www.ntfs-3g.org/"). And if you wish, you could even have just two partitions, as ubuntu will read and write to your winxp partition without issues...

Why dont you go ahead and download the Hardy beta LiveCD, and try it out. It will help you answer questions 1 and 3 without making any changes on ur pc.

---

### Post by Ryadt on 2008-04-11
Hi welcome to ubuntu...
yes it will recognise your external hd..It will appear on your desktop as soon as u plugged it in..
am pretty sure the java will work but am no expert down there...
hope this helped...

---

### Post by bumanie on 2008-04-11
Can't answer your java query. But linux can read FAT32. With the latest ubuntu releases, ubuntu can read/write to ntfs, so FAT32 is less important than it once was. As far as seagate external drives go, most work, but there has been issues with seagate 'freeagent' not behaving too well with ubuntu - it's something to do with ubuntu not being to re-enable the drive following going into hibernation. Can't remember the full details, just remember reading about it somewhere, but as I don't have a 'freeagent' drive I was not personally too concened with all the ins and outs etc.

---

### Post by Bruce H. McCosar on 2008-04-11
> **FritoDoom said:**
> Will the current Java SDK run on Ubuntu? And can someone recommend a good Java IDE for Linux/Ubuntu?

...

Apologies for the questions. It's a big plunge to make!

The Java 6 SDK is available.  When you get your system installed, use the package manager (probably **Synaptic**) to add the sun-java6-* packages.  Here's my current stats:

```
mccosar (1) -> ~
$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
mccosar (1) -> ~
$ javac -version
javac 1.6.0_03
```

I know it seems like a big plunge, but give it time, and you'll be wondering why you didn't switch sooner.  I came to Linux via Cygwin and Perl programming; my first distro was Debian 2.0.  Nowadays I can hardly stand to do anything on Windows.

---

### Post by tango_ninja on 2008-04-11
Hi, welcome to the forum

Ubuntu can access your fat32 partition, shouldn't be a problem at all. You can also r/w files in your XP partition from Ubuntu...it's rather easy. Your other partition basically shows up as another drive much the same way your external will. *Most* external usb HD will automount in Ubuntu the same way as windows. However, if it is NTFS you may have to manually mount it.

Just plug it in and if an icon doesn't appear on the desktop we can help you to manually mount.

---

### Post by FritoDoom on 2008-04-11
I am truly impressed. I have useful and thorough answers in under an hour. That's much better than I got from, well, you-know-who.*

I will try the 8.04 live CD as soon as it finishes downloading and see if it can see my NTFS partitions and the external drive.

Thanks for the answers everyone.

*Incidentally, if you ever want to waste time and get a laugh, call their phone tech support.

---

### Post by stchman on 2008-04-11
> **FritoDoom said:**
> Greetings everyone!

I'm looking at converting my computer to a dual-boot Windows XP/Ubuntu machine for some light programming work. Before I do this, I have some questions.

Can Ubuntu mount & access a FAT32 partition? My plan is to partition my HD three ways: XP, Ubuntu, and a small 'no-man's-land' partition to use for transferring data between the two. I'm leery of accessing the Windows partition with Ubuntu until I have a better idea of what I'm doing.

Will the current Java SDK run on Ubuntu? And can someone recommend a good Java IDE for Linux/Ubuntu?

My last question is a bit complicated. I have a Seagate USB external hard drive that I'm running off a PCI USB extension card. I'd like to be able to access the external via Ubuntu, but I have no idea how you'd go about doing that.

Apologies for the questions. It's a big plunge to make!

Yes Ubuntu read/writes natively to FAT32 and NTFS with ntfs-3g package.  I have a tutorial on mounting partitions.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Yes you can install a Java JDK and JRE very easily.  Use this command.

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

I prefer the 1.5, but if you want the 1.6 then sub 6 for 5 in the above statement.

A good IDE for Java is Netbeans, I believe it is in the repos.

If the Seagate hdd is a USB model, plug it into your USB port in Ubuntu and it will be automounted on your desktop.

---

