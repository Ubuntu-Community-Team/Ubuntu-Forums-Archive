---
title: "mbasses to do anything on this system"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by jwftm33 on 2008-03-12
omg why is it so hard. I need to know how to get java runtime enviroment install on this system. trying to play Yahoo spades need help.

---

### Post by firestormx37 on 2008-03-12
What have you tried so far?

Have you tried installing sun-java6-jre through synaptics?

---

### Post by jwftm33 on 2008-03-12
everthing that this damn system say to ubuntu restricted drivers and everthying. Jeez why can't it help

---

### Post by firestormx37 on 2008-03-12
You shouldn't need restricted drivers for getting java to work, unless you are having problems getting the video card working.

If you type
```
 java -version
```
 into the terminal what do you get?

If it doesn't give you  something like java version 1.6.0
then:

Make sure you have the multiverse repository enabled and run the following command at the terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Accept the license and that should get you working.  Try using the java -version listed above to test it out.

Also if you go into firefox and type about : plugins (no spaces)  in the address bar, the java plugin should be listed.

Lastly, this forum is a very helpful place if you look in the right places and ask NICELY.  Giving some more information about your problem would be helpful in the future.

---

### Post by jwftm33 on 2008-03-13
I did what u said and ran the terminal to install java6 but it asks me to put 7.04 feisty fawn disk in, which i do but the system doesn't see the disk. I used this disk to install 7.04 so not sure what is wrong any help would be greatly appreciated.

---

### Post by firestormx37 on 2008-03-13
Well to get it to stop asking for the CD, you should disable it in software sources.  Then your system will look on the internet to find what it needs.  So go into System > Administration > Software Sources:

Then go to the second tab and uncheck any of the cd options.  You may also want to consider checking universe, multiverse, and restricted on the first tab to give you more options of software to download.

Do that and see if the install works now.

Also, you did not answer my question.  What comes up when you type in java -version at the terminal?

---

