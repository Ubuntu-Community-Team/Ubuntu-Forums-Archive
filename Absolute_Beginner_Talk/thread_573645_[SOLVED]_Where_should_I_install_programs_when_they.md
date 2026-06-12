---
title: "[SOLVED] Where should I install programs when they are done manually?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-11
I am going to install BlueJ on my Dell notebook, but I was wondering where I should install it?  The installer suggests putting it in /home/BlueJ, is this a good idea?  I have never installed a program without the add remove program application before.

---

### Post by por100pre1 on 2007-10-11
/home/BlueJ doesn't sound to me like a good place. Put it in /opt/BlueJ.

---

### Post by elpichi on 2007-10-11
Is the opt folder there specially for manually installed programs?

---

### Post by iamthemicrowave on 2007-10-11
Thank you, exactly the answer I was looking for.

When I try to install bluej I receive an error message, saying I do not have permission to write to this directory.  Do I need to use sudo or gksudo or something?

---

### Post by jordanmthomas on 2007-10-11
> **elpichi said:**
> Is the opt folder there specially for manually installed programs?

Yes, usually extra, unnecessary (addon) software goes there.
[http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)

---

### Post by por100pre1 on 2007-10-11
> **elpichi said:**
> Is the opt folder there specially for manually installed programs?

The /opt folder is often used for folders that don't seem to fit anywhere else. Many people use it for applications that are completely installed in just one folder.

---

### Post by iamthemicrowave on 2007-10-11
How do I get permission to write to /opt?  When I run the GUI bluej installer, i choose /opt and it says I don't have permission.

---

### Post by om1 on 2007-10-11
> **iamthemicrowave said:**
> How do I get permission to write to /opt?  When I run the GUI bluej installer, i choose /opt and it says I don't have permission.
yes you will need to launch it with gksudo

---

### Post by jordanmthomas on 2007-10-11
I would like to point out that there's nothing *wrong* with installing it in your home directory, it's just abnormal.

---

### Post by iamthemicrowave on 2007-10-11
> **om1 said:**
> yes you will need to launch it with gksudo

When i run java -jar bluej-220.jar out of gksudo, nothing happens.  This is the install command given from the bluej website for unix, is there something else i should try?

---

### Post by om1 on 2007-10-11
> **iamthemicrowave said:**
> When i run java -jar bluej-220.jar out of gksudo, nothing happens.  This is the install command given from the bluej website for unix, is there something else i should try?
try running ```
gksudo nautilus
``` and launching the installer from there

---

### Post by iamthemicrowave on 2007-10-11
> **om1 said:**
> try running ```
gksudo nautilus
``` and launching the installer from there

That launches nautilus as the root user, but the jar installation file is on my home desktop.  How do I access it as through nautilus as the root user.

---

### Post by por100pre1 on 2007-10-11
In that specific case maybe the best alternative is to install that program in ~/BlueJ or /home/yourusername/BlueJ that is the same thing.

---

### Post by BrendanM on 2007-10-11
> **iamthemicrowave said:**
> That launches nautilus as the root user, but the jar installation file is on my home desktop.  How do I access it as through nautilus as the root user.

You can just browse to it in nautilus. Your home desktop is located at /home/username/Desktop/  Good luck with the install. What does BlueJ do?

---

### Post by om1 on 2007-10-11
press the up arrow to get to / then double click home double click your-user-name then double click Desktop....
then double click the installer

---

### Post by iamthemicrowave on 2007-10-11
ahh thank you very much! and bluej is a java editor I have to use in my CS class.

---

### Post by jordanmthomas on 2007-10-12
How do you like it so far?  A semester or two after I got done with Java my school started using BlueJ too.  It looked like something I would have a hard time using.

Just curious.

---

