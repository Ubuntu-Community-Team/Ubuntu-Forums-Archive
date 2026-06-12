---
title: "Java"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Brainless on 2005-12-15
How do I install Java? :confused:

---

### Post by lilrockerboy on 2005-12-15
I'm not sure if it helps, but the Automatrix program installed it for me!

[I got it from here!]("http://www.ubuntuforums.org/showthread.php?t=66563")

---

### Post by Mustard on 2005-12-15
Sun Java debs packaged for breezy are at [http://www.giannaros.org/public/breezydebs/](http://www.giannaros.org/public/breezydebs/) 

Look for the jre1.5+updates package.

To install these, open a terminal, cd to the directory you downloaded them to, and type "sudo dpkg -i filename.deb"

Alternatively go to this wikiguide and read the instructions on setting up java.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Brainless on 2005-12-16
What do I do with "jre-1_5_0_06-linux-i586.rpm"? :oops:

---

### Post by J_P on 2005-12-16
I installed java through Applications-Add applications no problems at all

---

### Post by Rackerz on 2005-12-16
Use this tutorial to install Java;

[http://ubuntuforums.org/showthread.php?t=76702&highlight=installing+java](http://ubuntuforums.org/showthread.php?t=76702&highlight=installing+java)

---

### Post by Brainless on 2005-12-16
I couldn't find Java under "Add Applications". ](*,)

---

### Post by J_P on 2005-12-16
Add aplications-Internet-More programmes

Its there java webstart

---

### Post by Mustard on 2005-12-16
[QUOTE=Brainless]I couldn't find Java under "Add Applications". ](*,)[/QUOTE]

I would suggest you read the guides above and choose one to attempt.  If you have questions on how to do certain steps on the guides then you should post specific questions about those steps you are not sure of.

The rpm you downloaded is not going to be a good way of installing java.  If you look at the first link in my post, and read the instructions in my post on which package to download from that link, then you shouldn't have too much trouble.  Installing a .deb package is pretty simple really.

Do you know how to use the terminal yet?

---

### Post by hod139 on 2005-12-16
As Mustard already wrote, the ubuntu wiki has a good turorial on how to install java:
[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249")
You will need to[ enable the multiverse repository]("https://wiki.ubuntu.com/AddingRepositoriesHowto") before using the j2re1.4 package.

---

### Post by Mustard on 2005-12-16
[QUOTE=J_P]Add aplications-Internet-More programmes

Its there java webstart[/QUOTE]

I think it might be worth mentioning that the version of Java you are telling him to install is Blackdown 1.4, which is not as up to date as the sun java jre1.5+updates.

---

### Post by Brainless on 2005-12-16
[QUOTE=Mustard]Do you know how to use the terminal yet?[/QUOTE]

No, not really. What do I do with files that end in .bin? :?

---

### Post by Brainless on 2005-12-16
[QUOTE=Mustard]Sun Java debs packaged for breezy are at [http://www.giannaros.org/public/breezydebs/](http://www.giannaros.org/public/breezydebs/)[/QUOTE]

I just now noticed this. #-o

---

### Post by Mustard on 2005-12-16
[QUOTE=Brainless]No, not really. What do I do with files that end in .bin? :?[/QUOTE]

The terminal can be opened by going to your Applications>>Accessories menu and clicking on 'Terminal'.  You will be presented with a command line and a prompt.  From there you can enter different commands to do useful functions on your linux installation.

Before you start getting into installing different things I would suggest you familiarise yourself with a few basic functions of the terminal.

Try looking over these links to get a feel for how things work.

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org](http://www.tuxfiles.org)

Once you have a feel for how the terminal works I would suggest you go back to the first post I made and attempt to install java.  It will make more sense after you have read through those links above and become familiar with how the terminal works.

---

### Post by Mustard on 2005-12-16
[QUOTE=Brainless]I just now noticed this. #-o[/QUOTE]

Open that link in your browser and look for the package that contains the words jre1.5+updates.  Download that package to your HOME directory.  The terminal opens up by default pointing at your HOME directory, so if you download the java .deb package to that directory you won't need to worry about how to use the cd command to change directories in terminal.  All you will need to do then is the second part of the instructions which involves entering this command into the terminal....

```
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
```

I'm assuming that the .deb package name is the same as the one I downloaded, so you shouldnt have much trouble just copying and pasting the command above into your terminal and hitting enter.  You will be asked for a password when you hit enter.  Put in your user password.  Please note that as you type the password in, you won't see any letters or even asterisks appearing on the screen, but what you type in is being registered.  Hit enter when you finish typing your password and it will start installing.  When its finished as long as there are no error messages, it should be successfully installed.

---

### Post by Brainless on 2005-12-16
[QUOTE=Mustard]When its finished as long as there are no error messages, it should be successfully installed.[/QUOTE]

It worked! \\:D/

---

### Post by Mustard on 2005-12-16
Well done. :)

---

### Post by Leif on 2005-12-16
there's also this method : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by Mustard on 2005-12-16
[QUOTE=Leif]there's also this method : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)[/QUOTE]

Heh..there's always more than one way to skin a cat in linux. :)

I hadnt seen this one before.

---

