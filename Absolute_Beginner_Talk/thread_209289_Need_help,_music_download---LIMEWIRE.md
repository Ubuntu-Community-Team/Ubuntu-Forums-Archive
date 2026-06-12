---
title: "Need help, music download---LIMEWIRE??"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-04
i am looking to install Limewire here on ubuntu linux and when i download the limewirelinux.rpm should i save to disk or open with archive manager. 
Then it says the archive is not supported

Cany sumone please tell me how to install Limewire?

---

### Post by scxtt on 2006-07-04
rpm files are for Red Hat based distros (RHEL, RH, Whitebox, Fedora, etc.) ... ubuntu is debian based, as in .deb instead of .rpm ...

---

### Post by IrishGangsta on 2006-07-04
Thank you! now i understand a little bit more here
So can anyone please tell me where i can go to download limewirelinux for ubuntu
Limewire.com is only offering it for the RPM package

---

### Post by user1397 on 2006-07-04
[quote=IrishGangsta]i am looking to install Limewire here on ubuntu linux and when i download the limewirelinux.rpm should i save to disk or open with archive manager. 
Then it says the archive is not supported

Cany sumone please tell me how to install Limewire?[/quote]i would recommend frostwire, its the exact same thing but its made for ubuntu.  download it from [here]("http://www.frostwire.com/")
then just double click on it, and select "install package".  then paste this into a terminal (applications > accessories > terminal): ```
sudo update-alternatives --config java
``` and select sun's java.  if you haven't installed sun java yet, go to synaptic package manager (system > administration > synaptic) and just search and install.

For trouble shooting, look here: [https://help.ubuntu.com/community/FrostWire]("https://help.ubuntu.com/community/FrostWire")

---

### Post by taurus on 2006-07-04
Or if you ever want to install files with .rpm extension, use alien to convert them to .deb first before you install it as
```

sudo apt-get install alien <-- installing alien on your system if you don't have it
alien <filename>.rpm <-- converting the .rpm to .deb
sudo dpkg -i <filename>.deb <-- installing the program

```

---

### Post by bodycoach2 on 2006-07-04
Use FrostWire instead:

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Actually works better than LimeWire.

---

### Post by IrishGangsta on 2006-07-04
Alrite thanx to everyone for helping
But i have a problem
I installed Frostwire and its located under the Internet Menu
But when i click to open nothing happens....
If anyone would like to help me with this 
Thanx

---

### Post by user1397 on 2006-07-04
[FONT=Verdana]you need to add extra repositories, by going [here]("http://www.psychocats.net/ubuntu/sources.php")
then you need to install java by pasting this command in a terminal:
```
sudo aptitude update && sudo aptitude install sun-java5-jre sun-java5-plugin
```[/FONT][LIST]
[*][FONT=Verdana]When asked, agree with DLJ license terms.[/FONT][/LIST][LIST]
[*][FONT=Verdana]To configure J2SE as the default JVM (necessary for programs such as Frostwire, RSSOwl and as a plugin for Mozilla Firefox):[/FONT][/LIST][FONT=Verdana]```
sudo update-alternatives --config java
``` Then choose the option that corresponds to J2SE (sun java). 
[/FONT]

---

### Post by taurus on 2006-07-04
If you click on a program that it just closes on you, you need to run it from a terminal (Applications -> Accessories -> Terminal) to see what the error is...

---

### Post by IrishGangsta on 2006-07-04
Erik - u said i need to go to that link to add extra repositories but i dont get where to go to find these "repositories" can u give me any detail? please

---

### Post by user1397 on 2006-07-05
[quote=IrishGangsta]Erik - u said i need to go to that link to add extra repositories but i dont get where to go to find these "repositories" can u give me any detail? please[/quote]just follow what it says in that guide and you'll be fine, you don't need to do anything outside that guide to add the repositories

---

### Post by user1397 on 2006-07-05
i've edited my last post on the first page.

btw, repositories are just online websites that have downloadable packages availabble to you.  they are the sources from which you can download and install more than 18,000 packages in ubuntu.  anything can be a repository, for example, the website where you would download updates for your windows xp computer (if u had one), thats a repository.  it just so happens that the ubuntu people are smart, and nice, so they have conviniently put all or almost all the packages you'll ever need in several "repos" that you can download from, either using the terminal (applications > accessories > terminal), or a package manager, like synaptic (system > administration > synaptic)

---

