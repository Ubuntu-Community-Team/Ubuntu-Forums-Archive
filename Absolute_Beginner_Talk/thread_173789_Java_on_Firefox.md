---
title: "Java on Firefox"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-05-10
Some applets on Firefox need Java. How do I get Java for Firefox? Thanks!

---

### Post by Sef on 2006-05-10
> Some applets on Firefox need Java. How do I get Java for Firefox? Thanks!

Read the java section of restricted formats.  It's towards the bottom of the page.  Don't forget to add the repositories. (at the top.)

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by 23meg on 2006-05-10
[https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8](https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8)

---

### Post by amitroy5 on 2006-05-10
sudo apt-get install j2re1.4
Password:
Reading package lists... Done
Building dependency tree... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate



What should I do? Thanks!

---

### Post by joshrobinson on 2006-05-10
download java jre1.5.0_06 from the sun website

rename it as java.bin for ease
in terminal type sudo nautilus
go to /usr
create a folder named java

place the java.bin in that folder
now go into the java folder with the terminal
type
sudo chmod +x java.bin
then
sudo ./java.bin

hit q to get past the terms of use, then type yes and hit enter
do java -version to see if it comes back as 1.5.0

if it doesnt come back as 1.5.0 then you have to make a sym link

go into /usr/bin with terminal
rename the old java file java2
sudo mv java java2

create the symlink 

sudo ln -s /usr/java/jre1.5.0_06/bin/java
do java -version again

---

### Post by joshrobinson on 2006-05-10
oh yeah and you might have to install the plugin into the firefox plugins directory also.. sometimes you dont have to.. alot of the times you do

go into /usr/share/firefox/plugins

do the following

ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so

and make sure java is enabled in firefox, in edit preferences content.. click enable java and restart the browsser

---

### Post by catlett on 2006-05-11
Go here for the download. You can install it yourself. [https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=2159D311AE31372D5035470DC5609B27](https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=2159D311AE31372D5035470DC5609B27)> Installation of Self-Extracting Binary
Use these instructions if you want to use the self-extracting binary file to install the J2SE Runtime Environment. If you want to install RPM packages instead, see Installation of RPM File.

1. Download and check the download file size to ensure that you have downloaded the full, uncorrupted software bundle.

    You can download to any directory you choose; it does not have to be the directory where you want to install the J2SE Runtime Environment.

    Before you download the file, notice its byte size provided on the download page on the web site. Once the download has completed, compare that file size to the size of the downloaded file to make sure they are equal. 

2. Make sure that execute permissions are set on the self-extracting binary.

    Run this command:
    chmod +x jre-1_5_0_<version>-linux-i586.bin 

3. Change directory to the location where you would like the files to be installed.

    The next step installs the J2SE Runtime Environment into the current directory. 

4. Run the self-extracting binary.

    Execute the downloaded file, prepended by the path to it. For example, if the file is in the current directory, prepend it with "./" (necessary if "." is not in the PATH environment variable):

    ./jre-1_5_0_<version>-linux-i586.bin

    The binary code license is displayed, and you are prompted to agree to its terms.

    The J2SE Runtime Environment files are installed in a directory called jre1.5.0_<version> in the current directory. Follow this link to see its directory structure. 



This is the link [http://java.sun.com/j2se/1.5.0/jre/install-linux.html](http://java.sun.com/j2se/1.5.0/jre/install-linux.html)  and those  are their instructions but it can be even easier.
1. Download the file. It will be put on your desktop by Firefox. Open your home folder and drag it in.
2.Open the terminal and type```
 chmod +x jre-1_5_0_<version>-linux-i586.bin 
```
3. Open your home folder. Double click on the jre-1.5 file. It will have a prompt with choices. Choose "RUN IN TERMINAL". This will start the installation. Follow the prompts and your done.
4. This is how I did it. If my way has problems you can follow the Sun directions exactly.

---

### Post by joshrobinson on 2006-05-11
[QUOTE=catlett]
1. download the file. It will be put on yourr desktop by Firefox but open your home folder and drag it in.
[/QUOTE]

same instructions as i listed, except id put it in /usr/java

i dont want to have that java folder installed into my home directory just sitting there annoying me.. so i stash it in /usr/java

also you have to do what i said for the firefox plugin

---

### Post by catlett on 2006-05-11
That was how I installed Java for firefox. One command and one double click. Your way might be technically correct but alot of people just want to get it to work. I didn't post until he came up with an error. 
My concept of linux is to get people's computers so they can run their everyday things. Once they have things running and they don't leave linux they will be more apt to learn the correct paths, commands etc. Say what you want but my way works. It may not be pretty but it doesn't give errors.

---

### Post by joshrobinson on 2006-05-11
[QUOTE=catlett]That was how I installed Java for firefox. One command and one double click. Your way might be technically correct but alot of people just want to get it to work. I didn't post until he came up with an error. 
My concept of linux is to get people's computers so they can run their everyday things. Once they have things running and they don't leave linux they will be more apt to learn the correct paths, commands etc. Say what you want but my way works. It may not be pretty but it doesn't give errors.[/QUOTE]

im just saying, i installed java 1.5.0 and it worked for applications but it didnt install a plugin for firefox.. without that symlink in the plugins directory firefox wont use java at all

i wasnt bashing your way of how to do it at all.. but it is good for people to start learning commands
also if he already had 1.4.2 installed, and you install 1.5.0 on top of it, it wont use 1.5.0 without a symlink in /usr/bin

---

### Post by amitroy5 on 2006-05-11
I still don't quite understand how to install the Java plugin for Firefox. It says to navigate to /usr/share/firefox/plugins. However, this directory does not exist. I have the version of Firefox included from the browser. What should I do? Thanks!

---

### Post by angrykeyboarder on 2006-05-16
Y'all are going about this the wrong way.  It's really best to use Debian packages whenever possible. They are much easier to manage.

1. Point your browser to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

2. Scroll down the page (about 1/3 of the way) to where it says " JRE 5.0 Update 6" and click on the "Download Sun JRE Update X" (6 at the time of this writing).

3 . About halfway down the page check the "Accept License Agreement" radio button.

4. Scroll down farther to where it says "Linux Platform ..."

5. Click on "Linux Self Extracting file" (Do NOT click on the RPM file).

6. The download will begin. Once you've downloaded it, open a terminal and cd to the directory that contains the file you just downloaded (unless of course it's your home directory, in which case you're already there).

7. type ```
chmod +x jre-1_5_0_06-linux-i586.bin
```
         (replace the "06" with whatever version you downloaded. This applies to anyone reading this 6 months from now...).

8. [Make sure the Ubuntu Universe repository is enabled in your sources.list file]("http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse").

9. Enter ```
$ sudo apt-get install java-package fakeroot 
```

10 To install enter ```
$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin 
```

11.Then enter ```
$ sudo dpkg -i sun-jre*.deb
```

Tada! You've now installed Sun's Java Runtime Environment.

If Firefox was running when you did this you'll need to restart it.

If you'd like to verity that the Firefox plugin is installed enter the following in the location bar in Firefox:  ```
about:plugins
```

If you've got a lot of Firefox plugins you may have to scroll down to find this.  You're looking for a heading that reads "Java(TM) Plug-in 1.5...." followed by a large table with umpteen listings in it.

That's the Sun Java Runtime Environment Plugin.

If you don't see that but see something else pertaining to Java (like java-gcj), read on.

Ubuntu comes with a GNU version of Java (I like to think of it as "Java in training" because it's not as "robust" as Sun Java as it's still in development).  It works fine with some apps and not-so fine (or not at all) with others.

So, if you've got any other apps that rely on Java (e.g. [Jedit]("http://www.jedit.org"), [Azureus]("http://azureus.sf.net")) and you'd rather have them use Sun's Java, then open a Terminal and enter the following:

```
$ sudo update-alternatives --config java
```

You should see something like (or similar to) this:
```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/j2re1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java
Press enter to keep the default[*], or type selection number:

```

Select the number that represents the Sun JRE (in this case it's #1) and enter.

That's it. You're done.

If you ever need to reinstall Java, hold on to that deb you just built. It will save you time later.

---

### Post by nalmeth on 2006-05-16
wow, everyone likes to do java in their own way
it's good, but must be a little confusing for OP

I used [automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")

Got to be the simplest way around

---

### Post by learning on 2006-07-06
Thanks angrykeyboarder!

I just used your instructions to update to version 7.

Worked great!

---

