---
title: "I need help installing Java"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-01
First off, I dont know which one to download on this page [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

And second, I don't know how to install it. 

Also, they are all .bin's and my comp will not open them for some reason, I tried installing Stuffit for Linux but there was no luck there. Please help, thanks.

-- Narcoleptic_Insomniac

---

### Post by Anonii on 2006-09-01
There you go:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Good Luck :]

---

### Post by Narcoleptic_Insomniac on 2006-09-01
Ok, my computer wont let me look at my sources list. When I type /etc/apt/sources.list to see my sources list it says access denied. I just gave the computer my password to make a backup. Help?

---

### Post by bulldog on 2006-09-01
If you want anything more 

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

and install automatix to install a whole bunch of apps for you.

About your sources list,try gksudo gedit /etc/apt/sources.list
and it will work.

---

### Post by Anonii on 2006-09-01
> **Narcoleptic_Insomniac said:**
> Ok, my computer wont let me look at my sources list. When I type /etc/apt/sources.list to see my sources list it says access denied. I just gave the computer my password to make a backup. Help?
Use: 

sudo gedit /etc/apt/sources.list

on the terminal.

sudo to get root access
and gedit to get the text editing program :)

Also read this, please:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Narcoleptic_Insomniac on 2006-09-01
Jee guys, thanks for tryin to help but you just lead my another thing that ends in .bin and my comp still refuses to open it.

---

### Post by Anonii on 2006-09-01
You probably mean this:
    *

12 - To install java :

    *

      sudo bash

      chmod 777 ./jre-1_5_0_06-linux-i586.bin

      (this file name will depend on the java version you download)

      ./jre-1_5_0_06-linux-i586.bin

      (it will ask you some questions)

      mkdir /usr/local/java32

      cp -r -p ./jre1.5.0_06/* /usr/local/java32

      cd /usr/local/firefox32/plugins/

      ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./



Please try reading this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
a little better. Its really detailed.

---

### Post by Narcoleptic_Insomniac on 2006-09-01
> **Anonii said:**
> You probably mean this:
    *

12 - To install java :

    *

      sudo bash

      chmod 777 ./jre-1_5_0_06-linux-i586.bin

      (this file name will depend on the java version you download)

      ./jre-1_5_0_06-linux-i586.bin

      (it will ask you some questions)

      mkdir /usr/local/java32

      cp -r -p ./jre1.5.0_06/* /usr/local/java32

      cd /usr/local/firefox32/plugins/

      ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./



Please try reading this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
a little better. Its really detailed.

Well do you think you could just give me a link to download that version of Java because I'm a beginner and don't know where to start.

---

### Post by Anonii on 2006-09-01
Use the following command on the terminal:
[B]
sudo apt-get install sun-java5-bin
[/B]
And report back if the program you want works, or not.

---

### Post by Narcoleptic_Insomniac on 2006-09-01
Didnt work. Still cant use java. All I want to do is look at this thing on the internet and I have all this trouble.

---

### Post by bulldog on 2006-09-01
Try automatix and it will work.

---

### Post by Anonii on 2006-09-01
Then please, spend 5minutes and read this article. I'm not a Java expert so I cant help you further.

Read this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by unisol on 2006-09-01
Download

Go to [http://java.com](http://java.com) 
Click on Get Java Software button 
There are two types of installation packages. Linux RPM package or Linux self extracting binary file. Download the package that best suits your needs.

Note: Linux RPM (Redhat Package Manager) uses RPM to install the JRE. In order to use this method, you need to have RPM available on your system. Otherwise use the other option. 




Click the appropriate Download button to download the package that best suits your needs. You can download the file to any of the directories on your system. 
After download verify: For Linux self extracting binary file 
Name of the file is jre-1_5_0_02-linux-i586.bin 
Size is approximately 15.8 MB 
For Linux RPM packages 
Name of the file is jre-1_5_0_02-linux-i586-rpm.bin 
Size is approximately 15.26 MB 



Install 


Linux self extracting binary file 
Linux RPM package
Note: The instructions below are for installing JRE 5.0. If you're installing another version, make sure you change the version number appropriately when you type the commands at the terminal.


To install the Linux (self-extracting) file 

Follow these instructions:

At the terminal: Type:
su 
Enter the root password. 
Change to the directory in which you want to install. Type:
cd <directory path name>
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/

Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions. 
Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0-linux-i586.bin 
Verify that you have permission to execute the file. Type:
ls -l 




Start the installation process.Type:
./jre-1_5_0-linux-i586.bin

This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.





The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0 directory. When the installation has completed, you will see the word Done.





The JRE is installed in jre1.5.(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.5.0 directory. Verify that the jre1.5.0 sub-directory is listed under the current directory. Type:
ls 





The installation is now complete. Skip to the Enable and Configure section. 

To install the Linux RPM (self-extracting) file 

Follow these instructions:

At the terminal: Type:
su 
Enter the root password. 
Change to the directory in which you want to install. Type:
cd 
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java

Note about root access: To install the JRE in a system-wide location such as/usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions. 
Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0-linux-i586-rpm.bin

Start the installation process. Type:
./jre-1_5_0-linux-i586-rpm.bin

This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.





The installation file creates jre-1_5_0-linux-i586.rpm file in the current directory. 




Run the RPM command at the terminal to install the packages. Type:
rpm -iv jre-1_5_0-linux-i586.rpm 
The JRE is installed in jre1.5.(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.5.0 directory. Verify that the jre1.5.0 sub-directory is listed under the current directory. Type:
ls 





The installation is now complete. Go to the Enable and Configure section. 


Enable and Configure


Mozilla 1.4 and later 
Mozilla 1.2, Netscape 6 and later 

Mozilla 1.4 and later 

Go to the plugins sub-directory under the Mozilla installation directory
cd <Mozilla installation directory>/plugins 
In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so 
Example:

If Mozilla is installed in this directory:
/usr/lib/mozilla-1.4/ 
and if the JRE is installed at this directory:
/usr/java/jre1.5.0 
Then type at the terminal to go to the browser plug-in directory:
cd /usr/lib/mozilla-1.4/plugins 
Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
ln -s /usr/java/jre1.5.0/plugin/i386/ns7
/libjavaplugin_oji.so . 
Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well. 
Go to Edit > Preferences. Under Advanced category > Select Enable Java 


Mozilla 1.2, Netscape 6 and later 

Go to the plugins sub-directory under the Netscape directory
cd <Mozilla1.2>/plugins 
Create a symbolic link to the ns7-gcc29/libjavaplugin_oji.so file:
ln -s <JRE>/plugin/i386/ns7-gcc29/libjavaplugin_oji.so 
Example:

If Netscape is installed at this directory:
/usr/lib/Mozilla1.2/ 
And if the JRE is installed at this directory:
/usr/java/jre1.5.0 
Then type at the terminal to go to the browser plug-in directory:
cd /usr/lib/Mozilla1.2/plugins 
Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
ln -s /usr/java/jre1.5.0/plugin/i386/ns7-gcc29
/libjavaplugin_oji.so . 
Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well. 
Go to Edit > Preferences. Under Advanced category > Select Enable Java 



Test Installation
To test that the JRE is installed, enabled and working properly on your computer, run this test applet from our web site:
Test your Java Runtime Environment

---

