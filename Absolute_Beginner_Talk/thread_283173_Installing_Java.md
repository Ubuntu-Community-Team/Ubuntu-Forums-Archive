---
title: "Installing Java"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by kq6up on 2006-10-23
I'm sure this has been asked a million times, but does someone have a link detailing the installation of Sun's Java on Ubuntu?

---

### Post by crimesaucer on 2006-10-23
you might already know this page: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by susan on 2006-10-23
I don't mean to jump in this thread. Please let me know if I should have started a new one on this JAVA thing.  I just bought an MP3 Player(sandisk) and understand that I need Sun Java before I get Frostwire. I've been reading and most threads indicate that I should be able to access Sun Java through my package list. I (think) I followed the instructions given and this is the response I get when I identify my Java's and then try and get Sun Java from Apt. 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:
susan@susan-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
susan@susan-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre

I'm extremely new to this and I am just learning the basics. Why can other people get sun java from their package lists and I can't seem to find it or blackdown in my package manager list? ](*,) 
thanks-susan

---

### Post by susan on 2006-10-23
if it wasn't already obvious. I'm on Kubuntu. The person who turned me on to Kubuntu told me that your forum was more "beginner friendly". I hope he was right! :KS

---

### Post by hod139 on 2006-10-23
First, install the package: sun-java5-jre.

Next, make Sun's java the default. First,
     ```

     [LEFT] sudo update-java-alternatives -s java-1.5.0-sun[/LEFT]

```Next, edit the JVM configuration file
     ```

     [LEFT]sudo -b gedit /etc/jvm[/LEFT]

``` and move the line 
     ```

     [LEFT]/usr/lib/jvm/java-1.5.0-sun[/LEFT]

``` to the top.

---

### Post by mxc on 2006-10-24
I cant find the java entry for sun in synaptic. I have enabled all repositories :(

---

### Post by hod139 on 2006-10-24
Are you running dapper, it is not in the breezy repositories.

---

