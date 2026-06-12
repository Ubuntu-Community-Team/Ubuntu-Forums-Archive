---
title: "JRE 6.0 Install Problem on Edgy"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by harryc on 2007-02-20
I've been folowing the Ubuntu install guide for edgy. How would I make the below work for JRE 6.0?

 > How to install JRE v5.0 Update 10

Note: Program included in Automatix2. If you have already used Automatix2, this program may have been installed

    * Read #General Notes
    * Read #How to add extra repositories 

    * Navigate to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) 

Choose "Java Runtime Environment (JRE) 5.0 Update 10" and click on "Download"
Accept License Agreement 
Download the "Linux self-extracting file"

    * Install the required tool : 

sudo aptitude install java-package

    * Create the Ubuntu package : 

fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin

    * Install the resulting package : 

sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb


    * Restart Mozilla Firefox
    * If you get an error, try changing the 10's in the filenames to the appropriate version number.  I get to this part -
 sudo dpkg -i sun-j2re1.5_1.5.0+update10_i386.deb

and I get this message- 

dpkg: error processing sun-j2re1.5_1.5.0+update10_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update10_i386.deb


Obviously I need the correct file name for 6.0. How do I find it

---

### Post by phossal on 2007-02-20
Harry, if you want to run JRE 6, consider getting it from SUN? You can follow the guide in my signature and be up and running in six steps. It isn't the *Ubuntu Way* like using a package, but consider it? If you would rather install a package, someone has packaged the .bin file and put it in the backports repository. Enable the backports and pull it down: *sun-java6-jdk*.

---

### Post by rbprogrammer on 2007-02-20
> **phossal said:**
> Harry, if you want to run JRE 6, consider getting it from SUN? You can follow the guide in my signature and be up and running in six steps. It isn't the *Ubuntu Way* like using a package, but consider it? If you would rather install a package, someone has packaged the .bin file and put it in the backports repository. Enable the backports and pull it down: *sun-java6-jdk*.

i would agree, it definitely worked out much better for me getting the JRE from SUN :lol:  ...

---

### Post by harryc on 2007-02-20
Thanks for the advice. My goal is to be able to run frostwire on xubuntu. Will it run on top of JRE 6.0?

---

### Post by phossal on 2007-02-20
Yes. Why Frostwire and not Limewire?

---

### Post by harryc on 2007-02-21
I installed Limewire and got it working with the JRE 6 packages. I had to run;

sudo update-alternatives --config java

and select option 3. 

Thanks again.

---

