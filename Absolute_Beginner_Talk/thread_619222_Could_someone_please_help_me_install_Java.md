---
title: "Could someone please help me install Java?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by RobHK on 2007-11-21
Could someone please help me install Java? I went to play a game o a we site and was told I needed to install Java. I was redirected to the Java web site and downloaded the file. I gave permission to run the file as executable.

These are the instructions on the Java site:

# At the terminal: Type:
su
# Enter the root password.

Now I am not aware of any root password and my login password isn't accepted, So I can't get any further.

---

### Post by Stemp on 2007-11-21
To install java, check : [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by RobHK on 2007-11-21
> **Stemp said:**
> To install java, check : [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Merci. Je n'avais pas reconnu le nom du fichier. 

Pour l'instant, côté anglais, rien à excuser mais la prochaine fois répondez-moi en français :)

---

### Post by Inxsible on 2007-11-21
First enable the universe and multiverse repositories. Then in a terminal type in```
sudo aptitude install sun-java6-jre
```When it asks you for the password, just type in the password that you created during installation. It will not show any * when you type the password in, but it is still accepting it. Just type in your entire password and hit "Enter"

---

### Post by samadk50 on 2007-11-21
Well this is what I did !!!!!  I'm a novice to Linux and it took me two or three attempts 
to get Java JRE and Adobe Flash player also to work sort of OKAY !!!!!! Crystal Solitaire still won't run if that's a test. I have had other Websites with Java Applets run alright though.
***** HANG ON and read carefully and re-read and maybe correct a few 'fat finger' goofs I have possibly made !!!!!

     *******   Install JRE on Linux   *******
*****  Substitute YOUR 'USER NAME' for SAM(My User Name)   *******

Download to /home/sam/

****  BRING UP TERMINAL WINDOW   ****
SUDO -l    This sets the Terminal for 'ROOT' usage. Most folders and files are
           OWNED by what is refered to as ROOT not owned by you. I also try to 
           add the SUDO command to each command in these steps.(Pre-Fix)

sudo CD /usr/java   THIS WILL PROMPT FOR ADMIN PASSWORD(Your Login Password).
                    You're Admin if your the 1st user created at Ubuntu Install Time.

sudo /home/sam/jre-6u3-linux-i586.bin

sudo chmod a+x /home/sam/jre-6u3-linux-i586.bin

The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_02 directory. When the installation has completed, you will see the word Done.

*****  MAKE Symbolic Link    ******


 Mozilla 1.4 and later

   1. Go to the plugins sub-directory under the Mozilla installation directory
      cd <Mozilla installation directory>/plugins
   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Mozilla is installed in this directory:
            /usr/lib/mozilla-1.4/
          * and if the JRE is installed at this directory:
            /usr/java/jre1.5.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/mozilla-1.4/plugins
      *******  cd /usr/lib/mozilla-firefox/plugins   ****
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so
             .
      ***** sudo ln -s /usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so
      ***** 

   3. Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well.
   4. Go to Edit > Preferences. Under Advanced category > Select Enable Java

---

### Post by Inxsible on 2007-11-21
samadk50, why go thru all that, when jre6 as well as the firefox plugin are available in the repos ?

---

### Post by kleo skywalker on 2007-11-21
Make sure repositories are enabled, go to Synaptic, search for > sun-java6-jre and install it. This will install other related packages as well.

---

### Post by RanDinCarolina on 2007-11-21
I got the flash plug-in in 7.10 by going to the pandora site and Firefox asked if I wanted to install it. JAVA in the repos and flash via the pandora site!!!

---

### Post by kleo skywalker on 2007-11-21
> **RanDinCarolina said:**
> I got the flash plug-in in 7.10 by going to the pandora site and Firefox asked if I wanted to install it. JAVA in the repos and flash via the pandora site!!!

This way, flash is not installed system-wide - only the user installing gets it, the other users don't. For system-wide changes, go to Synaptic, search for > flashplugin-nonfree and install it.

---

### Post by stchman on 2007-11-21
> **RobHK said:**
> Could someone please help me install Java? I went to play a game o a we site and was told I needed to install Java. I was redirected to the Java web site and downloaded the file. I gave permission to run the file as executable.

These are the instructions on the Java site:

# At the terminal: Type:
su
# Enter the root password.

Now I am not aware of any root password and my login password isn't accepted, So I can't get any further.

This will install the Java 1.5 on your system.

```
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
```

When you enter the line into your terminal then you will be prompted with a password.  Type your login password.  When you install Ubuntu you are granted administration rights for that user.

---

### Post by Inxsible on 2007-11-21
stchman, why are you asking the OP to install Java 1.5, when the latest version is 1.6 ?

Also, the OP doesn't need the jdk, I don't think he is programming in Java. He just needs the JRE to run the programs

---

### Post by stchman on 2007-11-21
> **Inxsible said:**
> stchman, why are you asking the OP to install Java 1.5, when the latest version is 1.6 ?

Also, the OP doesn't need the jdk, I don't think he is programming in Java. He just needs the JRE to run the programs

I have had problems in the past with using the 1.6 JRE with Firefox and such.  It is a blanket statement I use when installing Java.

If the OP wishes to install the 1.6 then he/she can use this statement:

```
sudo apt-get -y install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-fonts sun-java6-plugin  
```

I forgot the -y after the apt-get statement in my original post.

---

