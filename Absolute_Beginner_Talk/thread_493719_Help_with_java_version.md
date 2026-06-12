---
title: "Help with java version?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by RD4UBN2 on 2007-07-06
I tried to install java, as I like to pogo, but java.com gave me 4 choices to download. I didn't want to pick the wrong one so I searched the forums and decided to try:

           sudo apt-get install java

And what it tells me is:

           jeannie@jeannie-desktop:~$ sudo apt-get install java
           Password:
           Reading package lists... Done
           Building dependency tree       
           Reading state information... Done
           E: Couldn't find package java
           jeannie@jeannie-desktop:~$ 

Should I choose a version from java.com first  and then do the sudo apt-get? And if so which to choose? These are my choices:

        Linux RPM (self-extracting file) filesize: 17.67 MB
	Linux (self-extracting file) filesize: 18.15 MB 	Instructions
	Linux x64 * filesize: 17.15 MB 	Instructions
	Linux x64 RPM * filesize: 16.75 MB 	Instructions
        * Please use the 32-bit version for Java applet and Java Web Start support.

Appreciate any help!

Mad Love,
Jeannie

---

### Post by jackocleebrown on 2007-07-06
Halo,

This is something that I've always found confusing too. I can only advise you that I've always used the packages named "sun-java6-...." and they do the job for me. I think that the one you want is "sun-java6-jre" or similar. These are in the normal repositories (although I'm not sure if they are in universe or multiverse so you might need to enable these if you can't find them).

try:

sudo apt-get install sun-java6-jre


Jack.

---

### Post by Circus-Killer on 2007-07-06
try the following:
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin

or a simpler approach could me to go to your applications menu, click on "Add/Remove". in the add/remove window you will see a drop-down list in the top-right hand corner. make sure you select "All available packages" from the list. then in the list with the groups of applications, select other. then look for a package named "ubuntu restricted software" or something to that effect. this will install java, plus a whole bunch of other stuff such as mp3 support etc. etc.

---

### Post by jnorthr on 2007-07-06
Do i understand this correctly ? I thought java jre was pre-installed on ubuntu. Have not found out how to run it yet though, do we need a sym link to java jre ?

---

### Post by Circus-Killer on 2007-07-06
> **jnorthr said:**
> Do i understand this correctly ? I thought java jre was pre-installed on ubuntu. Have not found out how to run it yet though, do we need a sym link to java jre ?

you are semi-correct. java is pre-installed, but it's not the version created by sun microsystems. the version of java pre-installed is an open source implementation of java. naturally, the people who ONLY run FOSS on their boxes tend to stick with that one, but those of us who dont mind the occasional proprieatary product, go for the sun microsystem version.

---

### Post by RD4UBN2 on 2007-07-06
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin

This did the trick beautifully. I heart you!

And OMG why are people using anything else? Not only are the programs and the freeness fabulous... But YOU guys, the Linux community, are **[COLOR="DarkOrange"]amazing[/COLOR]**. THANK YOU!

---

### Post by drascus on 2007-07-08
Here is the easiest way I have found to install Java and get it running good. I have had tons of problems with Pogo games though no matter what it seems for me some games don't work. 
[https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b]("https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b")

Ok hope that helps

---

### Post by RD4UBN2 on 2007-07-08
That stinks... I love my pogo games! If you reinstall later you might consider doing:

*sudo apt-get install sun-java6-jre*

And when it's done then do:

*sudo apt-get install sun-java6-plugin*

Since I did that all of pogo is working beautifully for me. As a matter of fact, and not to jinx anything, everything has been working beautifully. Once I knew how to go get my plug-ins everything has been smooth. Every once in awhile Firefox will close unexpectedly, but it always restores to what I was doing, which I love. Even a room applet for a game I was in will restore, so I have no complaints! Ubuntu really does "just work".

---

### Post by forrestcupp on 2007-07-08
Yeah, we use the Sun version, and Pogo works for us.  My wife has a subscription and she's an addict.  Kind of like me and these forums.

---

### Post by ajmaske on 2007-07-09
> **RD4UBN2 said:**
> sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin

This did the trick beautifully. I heart you!

And OMG why are people using anything else? Not only are the programs and the freeness fabulous... But YOU guys, the Linux community, are **[COLOR="DarkOrange"]amazing[/COLOR]**. THANK YOU!

Okay, I tried the above and both came back ...

E: Couldn't find package sun-java6-jre


Any ideas?

---

### Post by Jimmy Joe on 2007-07-09
I also get the error message:

E: Couldn't find package sun-java6-plugin

Anyone have any advice on this one?

---

### Post by RD4UBN2 on 2007-07-09
Are you guys running the live cd or have you installed Ubuntu? I couldn't execute any terminal commands until after I installed. If you are still playing with the live cd this could be your problem.

---

### Post by AlexenderReez on 2007-07-09
> **ajmaske said:**
> Okay, I tried the above and both came back ...

E: Couldn't find package sun-java6-jre


Any ideas?

have you enable all repositories in source lists?i think not....enable first...then reload......after that you can install it.....

---

### Post by jackocleebrown on 2007-07-10
> **ajmaske said:**
> Okay, I tried the above and both came back ...

E: Couldn't find package sun-java6-jre


Any ideas?

Are you using Ubuntu 7.04? If not you might need to install an earlier version (sun-java5...)

Alternatively the problem might be that the sun-java packages are in the multiverse repository which you'll need to enable before trying to install.  Instructions on how to enable the multiverse repository here [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Hope this helps.

Jack.

---

### Post by Detonate on 2007-07-10
After you get the sun-java6-jre package installed, you should:

```
sudo update-alternatives --configure java
```

and select the java6 entry as the default to make it the system wide default.

---

### Post by mali2297 on 2007-07-10
Thanks for the tip, Detonate. I guess you meant
```

sudo update-alternatives --config java

```

---

### Post by Detonate on 2007-07-10
Yes, I know what I meant to type, but sometimes my fingers do a poor job or taking instructions from my brain:):)

---

