---
title: "A Problem With Any Package Intstallation..."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-06-29
Something keeps happening when I install things off of the Add/Remove, Update Software, And Synaptics...

> Setting up sun-java5-doc (1.5.0-11-1ubuntu2) ...
This package is an installer package, it does not actually contain the
J2SDK documentation. You will need to go download one of the archives :

     jdk-1_5_0-doc.zip  jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

           [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download. The file should be owned by root.root and be copied to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

Now, I've tried to install these archives through the site, but I don't fully understand how to do it. I've followed the intructions given to me by the installation guide, but when I follow them, terminal states that whatever folder I'm trying to install to, does not exist.

Is there anyone who can possibly direct me in the right direction? I've finally foresworn Windows, and deleted the partition holding the windows recovery, so I can't turn back now. :( Save me.

---

### Post by tcoffeep on 2007-06-29
I'm guessing noone else had this problem?

---

### Post by robertc36 on 2007-06-29
Its all in synpatic.
System/administration/synpatic
just search in there

---

### Post by mlentink on 2007-06-29
Isn't Java in the repositories?

It would help if you could tell what kind of a package you're trying to install. Are they .deb?

Also, what happens when you create the necessary direcories manually before installing?

EDIT: I've checked: Sun Java 5 is in the repo's. Open up Synaptic, search for java 5. Good luck!

---

### Post by tcoffeep on 2007-06-29
I have all the Java installation packages installed.

I tried to download education-laptop, and it had said something about Java. I did the update for today. And downloaded a game. Every single on of them came up with that.

It's making me scream inside.

---

### Post by tcoffeep on 2007-06-29
Also, (I've never had this happen before, until I used the alternate install cd) every so often it asks me to insert the Ubuntu CD. (any ideas on that?)

---

### Post by mlentink on 2007-06-29
> **tcoffeep said:**
> Every single on of them came up with that.

Every single one of them came up with what?
Have you installed Java form the repo's? What error messages are you getting?

---

### Post by tcoffeep on 2007-06-29
> Setting up sun-java5-doc (1.5.0-11-1ubuntu2) ...
This package is an installer package, it does not actually contain the
J2SDK documentation. You will need to go download one of the archives :

jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download. The file should be owned by root.root and be copied to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

This is what comes up even when I attempt to install java through Synaptics.

At first, I thought there was a small problem with how I was installing it. Then it continued happening.
I'm feel like I'm on the comic skit by Three Dead Trolls in a Baggie ("internet help desk")

---

### Post by mlentink on 2007-06-29
OK.

So what happens if you type 'no' and then hit return? I find it a bit awkward if the software would require for you to download the docs as well.

---

### Post by tcoffeep on 2007-06-29
It'll continue. I was trying to get Frostwire to run, but I had to delete EVERY SINGLE java version, and install only 5 and 6. And that's when all went to Hell.

But it just bugs me that it continually says this to me.
I don't know what to do. :( I downloaded all the docs ahead of time.

---

### Post by robertc36 on 2007-06-29
regarding cd remove from software sources
Also i searched for JDK as oppposed to java

---

### Post by sawjew on 2007-06-29
You are trying to install the sun java development documentation, I presume this is what you wish to do?  If it is not what you want  you should do ```
sudo apt-get remove --purge sun-java5-doc
```

If you do want the sun JDK documentation read on, I have just been through this myself so I may be able to help.

go to the link in the terminal [http://java.sun.com/j2se/1.5.0/download.html]("http://java.sun.com/j2se/1.5.0/download.html") and download the file jdk-1_5_0-doc.zip

When you have downloaded the file to wherever you chose to download it to, copy it to /tmp

you can do this using nautilus or the terminal.

then open a terminal and issue the commands as follows
```
cd /tmp
sudo chown root:root jdk-1_5_0-doc.zip
sudo apt-get install sun-java5-doc
```

and this should complete the installation of the java documentation

---

### Post by mlentink on 2007-06-29
I've got to go now, but I'm thinking you might try to give it just what it wants: download those docs to, say, your desktop, and then change ownership of the files to root and copy it to the /tmp directory

Will that work?

---

### Post by Mung the Wicked on 2008-03-02
The post by sawjew solves this problem.  I had the same exact problem, but it was listing the documentation for java sdk 1.4.  I installed JDK 5 and 6 as well, and that's when this problem started happening.  Since then I removed Java JDK 5 and 6, and installed java sdk 1.5, yet the problem still persisted with the 1.4 documentation.  This problem happens nearly every time you add/remove an app.  Anyway, thanks.  This problem was really irritating.

---

