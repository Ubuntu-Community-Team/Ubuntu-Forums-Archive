---
title: "[SOLVED] How to install JAVA on Feisty?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-10-09
There is an exam I need to take on-line. It requires that I first view a "presentation". I went to the "presentation" website, and it says in order to do it, you have to have "Java" installed:

> Note: In order to view the presentations, you must have JAVA enabled on your browser. This is typically disabled by default on Microsoft Internet Explorer. Click the following link to visit the download page for the JAVA plugin: [http://www.java.com/en/download/windows_ie.jsp](http://www.java.com/en/download/windows_ie.jsp)

I went to the above website, and it does have an option in small writing there, for installing in "Linux". But when you click on the Linux option, it lists the OS's that are included-- I see Red Hat and Suse listed there, but Ubuntu is not listed there. Even though it doesn't say "ubuntu", is that still what I need to install? And is their way the best way to do it? Or should I instead do something like go to Add/Remove or Synaptic and install from there? Thanks!

---

### Post by RomeReactor on 2007-10-09
Hi. If you're on Feisty 32-bit, then:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by swarup on 2007-10-09
> **RomeReactor said:**
> Hi. If you're on Feisty 32-bit, then:
```
sudo apt-get install sun-java6-plugin
```

Thank you very much! Yes, I am on Feisty 32-bit. So I'll try now what you've given above and let you know how it goes.

---

### Post by Joeb454 on 2007-10-09
If that fails click Applications>Add/Remove

Then when that has loaded, make sure the list box at the top right of the window allows all packages to be installed.

Then search for restricted, and it should come up with Ubuntu Restricted Extras.

Download and install that :)

---

### Post by swarup on 2007-10-09
Please see below code. It appears that I already have that plug-in installed. Is this "sun-java6-plugin" all that should be needed? Because when I go to the website to open the above-mentioned "presentations", the window for opening them is blank. And the message I quoted in my opening post above, was given there. So it looks like for some reason this "sun-java6-plugin" may not be what is needed?

```
swarup@swarup-laptop:~$ sudo apt-get install sun-java6-plugin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  debhelper module-assistant intltool-debian mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-es-es po-debconf gettext thunderbird-locale-es-ar
  thunderbird-locale-es-es dpkg-dev myspell-es html2text wspanish
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
swarup@swarup-laptop:~$ 
```

---

### Post by swarup on 2007-10-09
> **Joeb454 said:**
> If that fails click Applications>Add/Remove

Then when that has loaded, make sure the list box at the top right of the window allows all packages to be installed.

Then search for restricted, and it should come up with Ubuntu Restricted Extras.

Download and install that :)

It didn't fail to load, no. Rather it seems it is already installed (see above). But despite being already installed, I cannot do what it is that I need to do (view the "presentations"). Is there something further, then, that I need to install through "Add/Remove"? If so, what exactly is it that I have to type and select when I go to Add/Remove?

---

### Post by forestpixie on 2007-10-09
if you open nautilus and show hidden files have you a java folder inside the .mozilla folder - that was how I ended up doing it 

I tried to install through apt-get and looked in synaptic and still I got the "you need to install java" message ... grrrrr

downloaded the file from sun - copied it into the mozilla folder and ran the install from there

maybe that'll help

---

### Post by Joeb454 on 2007-10-09
If you want to use Add/Remove then just type "restricted" (no quotes) into the search box of the Add/Remove window.

You should then be able to install the restricted extras tat Ubuntu has to offer, e.g. flash java etc.

---

### Post by swarup on 2007-10-09
> **Joeb454 said:**
> If you want to use Add/Remove then just type "restricted" (no quotes) into the search box of the Add/Remove window.

You should then be able to install the restricted extras tat Ubuntu has to offer, e.g. flash java etc.

Ok. I did it just now. But when I clicked on "details" to see what it is installing, it only seemed to be downloading and installing the "flash plugin". It looks like the other items (mp3, java, etc) are already installed (according to Ubuntu). And after doing the flash plugin install, I still can't see the presentations.

---

### Post by swarup on 2007-10-09
> **forestpixie said:**
> if you open nautilus and show hidden files have you a java folder inside the .mozilla folder - that was how I ended up doing it 

I went there-- you're right-- there is no java folder there.

> **forestpixie said:**
> I tried to install through apt-get and looked in synaptic and still I got the "you need to install java" message ... grrrrr

downloaded the file from sun - copied it into the mozilla folder and ran the install from there

maybe that'll help

Ok. I'll try this. But when I download the file from sun and copy it into the mozilla folder, then at that point what do I have to do to "run the install from there"?

---

### Post by Seisen on 2007-10-09
Did you happen to do this after you install Java

```
sudo update-alternatives --config java
``` and pick the latest version of Java that you installed.

---

### Post by swarup on 2007-10-09
> **Seisen said:**
> Did you happen to do this after you install Java

```
sudo update-alternatives --config java
``` and pick the latest version of Java that you installed.

No, I hadn't. But I just did so now-- see below. And it doesn't seem to have made any difference. I still can't see what it is I need to see (on the webpage I am trying to work with--see my 1st post).

```

swarup@swarup-laptop:~$ sudo update-alternatives --config java
Password:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
swarup@swarup-laptop:~$ 
```

I've just downloaded a file from sun:
```

/home/swarup/Desktop/jre-6u3-linux-i586.bin
```

Does that look like something I don't yet have on my computer? The sun website gives instructions for installing it in Linux. See below. Should I do it?

> 
Linux download and installation instruction for the Java Runtime Environment (JRE)

This article applies to:

    * Platform(s):
      Red Hat Linux, SUSE Linux, JDS
    * Browser(s):
      Netscape 6.2x, Netscape 7, Mozilla 1.4+
    * JRE version(s):
      1.5.0

To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l

Make sure the installation file has executable permission

   6. Start the installation process.Type:
      ./jre-1_5_0-linux-i586.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.

type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0 directory. When the installation has completed, you will see the word Done.

---

### Post by Joeb454 on 2007-10-09
Given that your thread is marked as solved, I'm assuming that the instructions given from the website that you quoted above worked?

If so my idea was clearly wrong :p but glad you got it sorted :)

---

### Post by swarup on 2007-10-12
> **Joeb454 said:**
> Given that your thread is marked as solved, I'm assuming that the instructions given from the website that you quoted above worked?

If so my idea was clearly wrong :p but glad you got it sorted :)

At this point, I am not certain which strategy worked. Because in the end I had tried all of them including the above website instructions, and it still looked the same. But then I realized that there was something I myself wasn't properly executing in the website I was trying to work on that required JAVA. So once I executed that on the website, the page I needed immediately opened, and I felt like a fool. I don't know whether it would have worked even from the very get go without doing anything, if I had just opened it properly. So it may have been what you suggested, or it may have been the above website instructions, or it may have been that it didn't really require anything just needed me to open the web page properly. I'll never know. All I can tell you is, now it works fine. :)

---

