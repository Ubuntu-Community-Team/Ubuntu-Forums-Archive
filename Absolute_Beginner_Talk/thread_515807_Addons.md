---
title: "Addons"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Dennis Shipman on 2007-08-02
I have had limit technical glitches with this operating system. However, I need these add ons for my browser to operate optimally. They are not in Synaptic, or Automatix2. So, how does one go about getting and installing them?


[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

### Post by Raineer on 2007-08-02
Do you need *all* of those plugins?  A quick glance through the list and I saw several that have equivalents in synatpic or Linux versions.

Can you post a more specific list of what you need to add? I'm sure we can help.

edit: Right on that page you linked a good deal of those have "Linux" links to support info.  When I clicked them it took me right to install files, did you try those?

---

### Post by wolfen69 on 2007-08-02
all of those are available as regular downloads in ubuntu. you do not need to install them directly into firefox. they will work in your browser.

---

### Post by Seisen on 2007-08-02
Actually the Windows Media Player, Shockwave Player and Quicktime plugins in Ubuntu won't work. That might be what is causing the problem.

---

### Post by Nythain on 2007-08-02
windows media player and shockwave you might be s o l with... i know shockwave you are, but i think theres ways around windows media player.

for the others...
sudo apt-get install flashplugin-nonfree mozilla-mplayer sun-java6-jre sun-java6-plugin java-common w32codecs acroread acroread-plugins
that should take care of making sure you can play windows codecs, java, acrobat, and media inside of firefox

make sure you have all teh appropriate repos (universe, multiverse, medibuntu)

---

### Post by Dennis Shipman on 2007-08-04
The browser is constantly prompting for plugins/addons on web pages with heavy flash/java content. When you say be specific, I was. I need all of those plugins/addons for my browser to work correctly. If Synaptic or linux has a version that will work, where can I obtain it? And more importantly, what are the codes/commands needed to install them?

> **Raineer said:**
> Do you need *all* of those plugins?  A quick glance through the list and I saw several that have equivalents in synatpic or Linux versions.

Can you post a more specific list of what you need to add? I'm sure we can help.

edit: Right on that page you linked a good deal of those have "Linux" links to support info.  When I clicked them it took me right to install files, did you try those?

---

### Post by Dennis Shipman on 2007-08-04
Unless I am misunderstanding your response, it is not accurate. The browser constantly prompts for add ons/plug ins, which are *not* installed in the browser, and I need to know how to do it. 

> **wolfen69 said:**
> all of those are available as regular downloads in ubuntu. you do not need to install them directly into firefox. they will work in your browser.

---

### Post by Dennis Shipman on 2007-08-04
I know the symptom, I need to find the cure. . .

> **Seisen said:**
> Actually the Windows Media Player, Shockwave Player and Quicktime plugins in Ubuntu won't work. That might be what is causing the problem.

---

### Post by Dennis Shipman on 2007-08-04
I already tried this several times without success. The browser still prompts for "shockwave flashplayer" and often Java, which I cannot install because for some reason when I follow the instructions provided by Sun Systems, and enter SU followed by the Root password, I get an authentication error, and cannot get pass this step.


> **Nythain said:**
> windows media player and shockwave you might be s o l with... i know shockwave you are, but i think theres ways around windows media player.

for the others...
sudo apt-get install flashplugin-nonfree mozilla-mplayer sun-java6-jre sun-java6-plugin java-common w32codecs acroread acroread-plugins
that should take care of making sure you can play windows codecs, java, acrobat, and media inside of firefox

make sure you have all teh appropriate repos (universe, multiverse, medibuntu)

---

### Post by Steveway on 2007-08-04
There is NO Shockwave for Linux, so you need to keep on living without your little browsergames.
And Afaik, Java is in the repositorys so you can install it through Synaptic, you should learn how to use Synaptic first that'll help.
And a tip for free, Ubuntu doesn't use su we use a system called Superuser do, in short sudo.
And, what is that? a quadruple or fivetuplepost? Learn to edit your posts!

---

### Post by Dennis Shipman on 2007-08-04
Those were the instructions provided by SUN Systems. As a novice user, I just folllowed them. I did install Java through Syntaptic but often I still get an error message when navigating to pages that requires java plug ins.


> **Steveway said:**
> There is NO Shockwave for Linux, so you need to keep on living without your little browsergames.
And Afaik, Java is in the repositorys so you can install it through Synaptic, you should learn how to use Synaptic first that'll help.
And a tip for free, Ubuntu doesn't use su we use a system called Superuser do, in short sudo.
And, what is that? a quadruple or fivetuplepost? Learn to edit your posts!

---

### Post by NilsE on 2007-08-04
Install RealPlayer like this

1) In Synaptic make sure shared libraries: libstdc++.5 (or newer) is installed.

2) Download RealPlayer from [http://www.real.com/linux](http://www.real.com/linux) to your home folder by clicking on the gold "Download RealPlayer" button.

3) In a none root terminal enter the following commands (none root so it is installed under the user not root).

You can copy and paste each line.
```
cd /home/xxxxx  

NOTE: Where xxxxx is you home  folder

```
```
chmod +x RealPlayer10GOLD.bin

NOTE: Applies permissions

```
```
sudo ./RealPlayer10GOLD.bin

NOTE: As it does the install you can take all the defaults.

```
This will install RealPlayer and the Mozilla plugin.

Then from synaptic install all the Gstreamer 10 plugins.  Just the ones that say plugin and no need to install the doc and dbg files.

Also install w32codecs which is in restricted drivers.

This is a good guide for the Gstreamer and w32codecs [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by Dennis Shipman on 2007-08-04
> **Dennis Shipman said:**
> Those were the instructions provided by SUN Systems. As a novice user, I just folllowed them. I did install Java through Syntaptic but often I still get an error message when navigating to pages that requires java plug ins.

I. To install the Linux self-extracting x64 file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0_02-linux-amd64.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l



Change permission on the installation file

   6. Start the installation process. Type:
      ./jre-1_5_0_02-linux-amd64.bin
      Note: If the file is in the current directory, prepend it with "./"

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0_02 directory. When the installation has completed, you will see the word Done.



Installation completes

   8. The JRE is installed in jre1.5.0_(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java directory. Verify that the jre1.5.0_02 sub-directory is listed under the current directory. Type:
      ls



Verify the installation

   9. Delete the bin installation file if you want to save disk space.
  10. Exit the root shell.

I need to modify the commands so this installation will work with Ubuntu 7.04 64 Bit AMD. Does anyone know how?

---

### Post by Dennis Shipman on 2007-08-04
I tried this many times, and cannot locate the file I downloaded to the home folder. 

> **NilsE said:**
> Install RealPlayer like this

1) In Synaptic make sure shared libraries: libstdc++.5 (or newer) is installed.

2) Download RealPlayer from [http://www.real.com/linux](http://www.real.com/linux) to your home folder by clicking on the gold "Download RealPlayer" button.

3) In a none root terminal enter the following commands (none root so it is installed under the user not root).

You can copy and paste each line.
```
cd /home/xxxxx  

NOTE: Where xxxxx is you home  folder

```
```
chmod +x RealPlayer10GOLD.bin

NOTE: Applies permissions

```
```
sudo ./RealPlayer10GOLD.bin

NOTE: As it does the install you can take all the defaults.

```
This will install RealPlayer and the Mozilla plugin.

Then from synaptic install all the Gstreamer 10 plugins.  Just the ones that say plugin and no need to install the doc and dbg files.

Also install w32codecs which is in restricted drivers.

This is a good guide for the Gstreamer and w32codecs [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by shearn89 on 2007-08-04
just type "cd" (in a terminal), and it will automatically take you to your home folder - however, unless you've changed it, the file will be in your "Desktop" folder, so:
```
cd ~/Desktop
```

If you still can't find it, type (again in a terminal)
```
locate RealPlayer10
```
and it should give you the location.

---

### Post by philinux on 2007-08-04
All i did when i got the missing plugin message was to click install - end of story. It just installed the plug in.

---

### Post by Dennis Shipman on 2007-08-04
What is this?:confused: I need a little assistance not sarcasm. Please give me a break, I'm new to Ubuntu, and these forums. And if the fix worked that easily trust me, I would not be subjecting myself to rude comments like this. Please hold your reply. There are other Ubuntu members who aren't here for this sort of mischief but to help our community. 

> **philinux said:**
> All i did when i got the missing plugin message was to click install - end of story. It just installed the plug in.

---

### Post by philinux on 2007-08-04
Sorry no sarcasm intended I don't know why but the plugins were no probs honest. I'm a newbie too. Only been using Linix Feisty for about 3 weeks.
To check what you have installed you need to type about:plugins in the address bar.

---

### Post by Dennis Shipman on 2007-08-04
file:///home/dennis/Desktop/RealPlayer10GOLD.bin is where WebDownLoader says it saved the file. But using Locate Realplayer10 just returned me back to dennis@dennis-laptop:~$ 


> **shearn89 said:**
> just type "cd" (in a terminal), and it will automatically take you to your home folder - however, unless you've changed it, the file will be in your "Desktop" folder, so:
```
cd ~/Desktop
```

If you still can't find it, type (again in a terminal)
```
locate RealPlayer10
```
and it should give you the location.

---

### Post by diatribe on 2007-08-04
commands:

cd ~/Desktop
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

---

### Post by philinux on 2007-08-04
Denis I installed realplayer10 and it's there under application - sound & video but if I try 
locate replayer10 I get same result as you

---

### Post by Dennis Shipman on 2007-08-04
To be frank, I have to sit down and study this operating system because it is far more complicated than Windows, which is for home users. So, my frustration stems from responses where people know a little but not enough to seriously address installation conflicts, software incompatibility and related issues, which are the major shortfalls of this OS. Simply saying you had no problem does not address anything, moreover, which is why I thought you were being sarcastic. 


> **philinux said:**
> Sorry no sarcasm intended I don't know why but the plugins were no probs honest. I'm a newbie too. Only been using Linix Feisty for about 3 weeks.
To check what you have installed you need to type about:plugins in the address bar.

---

### Post by Dennis Shipman on 2007-08-04
It is asking for "enter the prefix for symbolic links [/usr]:"

---

### Post by philinux on 2007-08-04
Thanks denis, when it came to real player I installed it from Synaptic package manager. This type of install was just like windoze setup.exe in operation. no commands to type. I dont know if you can just use it now though after your install method.

---

### Post by shearn89 on 2007-08-04
> To be frank, I have to sit down and study this operating system because it is far more complicated than Windows, which is for home users. So, my frustration stems from responses where people know a little but not enough to seriously address installation conflicts, software incompatibility and related issues, which are the major shortfalls of this OS. Simply saying you had no problem does not address anything, moreover, which is why I thought you were being sarcastic.

Ubuntu is also for home users, but compare how long you've been using windows to how long you've been using Ubuntu, and maybe it will put it into perspective. Plus everything is designed for windows and internet explorer, not linux and firefox...

Also, the people on this forum are (mostly) trying to help you, and very few are actually developers of the OS - we're simply other users, who have a little more knowledge and experience at using it, and are trying to aid others; if we "don't know enough to seriously address installation conflicts" we apologise - we can always just ignore your problem if you want.

Anyway, the reason my "locate" command didn't work, is because i forgot to put an asterisk at the end of RealPlayer10.

EDIT: after a quick look [here]("http://monkeyblog.org/ubuntu/installing/#installer"), apparently you don't need to put the "./" at the beginning of the path to the file, just make it executable (if it isn't), and put in the full path. In your case, this would be:
```

cd ~/Desktop
chmod a+x RealPlayer10Gold.bin
RealPlayer10Gold.bin

```
make sure you get the case right, as linux is case-sensitive in the terminal.

---

### Post by Dennis Shipman on 2007-08-04
Oh boy:( Why assume that I believe people aren't here to help:confused: If you'd read my reply to the poster's thread you took the liberty of responding to, you'd see it was a simple misunderstanding, and we've both moved on to more productive endeavors like tweaking our nifty new OS. 

If you're serious about helping, though, I have 3 problems that still have not been addressed: Namely, since downloading and installing Realplayer10, I've gotten an unwanted, "locked" icon on my desktop that I cannot delete, move, or otherwise do anything with because though its clearly somewhere in my home file, I have no "permissions," to unlock the folder (if I could even locate it because looking in the terminal for it didn't produce any results) What to do?

Second, I still cannot install plug ins for Mozilla Firefox, which actually work like a flash player compatible with 64 bit architecture, or at least 32 bit workaround. Here's the message I got when I tried:

~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


Third, Java does have a complete Runtime Environment download on its website specifically designed for 64 bit systems but it will not download and install using the instructions provided.


QUOTE=shearn89;3133446]Ubuntu is also for home users, but compare how long you've been using windows to how long you've been using Ubuntu, and maybe it will put it into perspective. Plus everything is designed for windows and internet explorer, not linux and firefox...

Also, the people on this forum are (mostly) trying to help you, and very few are actually developers of the OS - we're simply other users, who have a little more knowledge and experience at using it, and are trying to aid others; if we "don't know enough to seriously address installation conflicts" we apologise - we can always just ignore your problem if you want.

Anyway, the reason my "locate" command didn't work, is because i forgot to put an asterisk at the end of RealPlayer10.

EDIT: after a quick look [here]("http://monkeyblog.org/ubuntu/installing/#installer"), apparently you don't need to put the "./" at the beginning of the path to the file, just make it executable (if it isn't), and put in the full path. In your case, this would be:
```

cd ~/Desktop
chmod a+x RealPlayer10Gold.bin
RealPlayer10Gold.bin

```
make sure you get the case right, as linux is case-sensitive in the terminal.[/QUOTE]

---

### Post by shearn89 on 2007-08-05
Sorry about the (minor) rant - i didn't mean to be rude. As to your problems:

> **Dennis Shipman said:**
> I have 3 problems that still have not been addressed: Namely, since downloading and installing Realplayer10, I've gotten an unwanted, "locked" icon on my desktop that I cannot delete, move, or otherwise do anything with because though its clearly somewhere in my home file, I have no "permissions," to unlock the folder (if I could even locate it because looking in the terminal for it didn't produce any results) What to do?


I think this can be solved by opening a terminal and doing:
```

cd ~/Desktop
ls
#<this should list the files in the directory, one of which should be the launcher that you can't delete>
sudo rm <name of launcher>

```
It will ask for a password after the "sudo" command, which is just your normal user password.


> 
Second, I still cannot install plug ins for Mozilla Firefox, which actually work like a flash player compatible with 64 bit architecture, or at least 32 bit workaround. Here's the message I got when I tried:

```

~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```


This could be becuase some of the Repositories (lists of software available to download) aren't enabled. Open Synaptic (System -> Administration -> Synaptic Package Manager), go to Settings -> Repositories, and check all the boxes. That should solve the problem -  if it doesn't, post back here, and i'll see what i can do.

> 
Third, Java does have a complete Runtime Environment download on its website specifically designed for 64 bit systems but it will not download and install using the instructions provided.


Not sure about this - i did a quick google to try and find the page, but it looks a bit complicated. If you post a link to the page you're using, i'll have a look myself.

shearn89

---

### Post by Dennis Shipman on 2007-08-06
1. Trying the commands as indicated returned the following error message, which is the same one I told you I'd gotten when I attempted to remove the "locked" icon from my desktop.

dennis@dennis-laptop:~$ cd ~/Desktop
dennis@dennis-laptop:~/Desktop$ ls #realplayer
RealPlayer
dennis@dennis-laptop:~/Desktop$ sudo rm realplayer
Password:
rm: cannot remove `realplayer': No such file or directory
dennis@dennis-laptop:~/Desktop$ 


2. All available respositories and some have been added and enabled. I can provide a list if necessary.

3. I. To install the Linux self-extracting x64 file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0_02-linux-amd64.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l



Change permission on the installation file

   6. Start the installation process. Type:
      ./jre-1_5_0_02-linux-amd64.bin
      Note: If the file is in the current directory, prepend it with "./"

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0_02 directory. When the installation has completed, you will see the word Done.



Installation completes

   8. The JRE is installed in jre1.5.0_(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java directory. Verify that the jre1.5.0_02 sub-directory is listed under the current directory. Type:
      ls



Verify the installation

   9. Delete the bin installation file if you want to save disk space.
  10. Exit the root shell.




NEED MORE HELP?
If you require further assistance, please make sure you check through our Help and FAQ sections thoroughly. We probably have a page that answers your question.

You may find information on the following topics in the Help section:
Installation Instructions
Configuration
Error Messages
Applet Application




This page meets my need.
  	disagree 							agree
Comments:


> **shearn89 said:**
> Sorry about the (minor) rant - i didn't mean to be rude. As to your problems:



I think this can be solved by opening a terminal and doing:
```

cd ~/Desktop
ls
#<this should list the files in the directory, one of which should be the launcher that you can't delete>
sudo rm <name of launcher>

```
It will ask for a password after the "sudo" command, which is just your normal user password.




This could be becuase some of the Repositories (lists of software available to download) aren't enabled. Open Synaptic (System -> Administration -> Synaptic Package Manager), go to Settings -> Repositories, and check all the boxes. That should solve the problem -  if it doesn't, post back here, and i'll see what i can do.



Not sure about this - i did a quick google to try and find the page, but it looks a bit complicated. If you post a link to the page you're using, i'll have a look myself.

shearn89

---

### Post by shearn89 on 2007-08-06
In linux, a "#" indicates a comment in coding, what you should have typed into the terminal to remove the launcher was:
```

cd ~/Desktop
ls
sudo rm <name of launcher as shown by the "ls" command>

```
Where "cd" Changes Directory to your desktop folder, "ls" lists all items in that directory (ie. on the desktop), and "sudo rm ***" removes the *** file as an administrator.


As to the instructions, they should meet your need, with a little tweaking:

1. Locate the file you downloaded, and write down somewhere on paper where it is. This may be in your "Desktop" folder, on in your "home" directory somewhere.

2. Create the installation folder - in a terminal type:
```

sudo mkdir /usr/java

```
(assuming you wish to install to /usr/java)

3. Move the downloaded file to the folder just created:
```

sudo mv <path to downloaded file> /usr/java/

```
Where path to file will be something like ~/Desktop/jre-1_5_0_02-linux-amd64.bin (if in the desktop folder) or ~/jre-1_5_0_02-linux-amd64.bin (if in home directory). "~" is a shortcut for your "home" folder (/home/username/)

4. Make the file executable:
```

cd /usr/java/
sudo chmod a+x jre-1_5_0_02-linux-amd64.bin

```

5. Run the installation:
```

./jre-1_5_0_02-linux-amd64.bin

```
This is equivalent to step 6 in their instructions, and you can follow theirs for the rest of it.

---

### Post by Dennis Shipman on 2007-08-06
The Realplayer folder is clearly in my home directory but terminal still returns an error message saying no such file or directory.


> **shearn89 said:**
> In linux, a "#" indicates a comment in coding, what you should have typed into the terminal to remove the launcher was:
```

cd ~/Desktop
ls
sudo rm <name of launcher as shown by the "ls" command>

```
Where "cd" Changes Directory to your desktop folder, "ls" lists all items in that directory (ie. on the desktop), and "sudo rm ***" removes the *** file as an administrator.


As to the instructions, they should meet your need, with a little tweaking:

1. Locate the file you downloaded, and write down somewhere on paper where it is. This may be in your "Desktop" folder, on in your "home" directory somewhere.

2. Create the installation folder - in a terminal type:
```

sudo mkdir /usr/java

```
(assuming you wish to install to /usr/java)

3. Move the downloaded file to the folder just created:
```

sudo mv <path to downloaded file> /usr/java/

```
Where path to file will be something like ~/Desktop/jre-1_5_0_02-linux-amd64.bin (if in the desktop folder) or ~/jre-1_5_0_02-linux-amd64.bin (if in home directory). "~" is a shortcut for your "home" folder (/home/username/)

4. Make the file executable:
```

cd /usr/java/
sudo chmod a+x jre-1_5_0_02-linux-amd64.bin

```

5. Run the installation:
```

./jre-1_5_0_02-linux-amd64.bin

```
This is equivalent to step 6 in their instructions, and you can follow theirs for the rest of it.

---

### Post by shearn89 on 2007-08-06
try pressing "tab" after typing "real", and see if it auto-fills anything for you. If nothing happens, press tab twice, and it should list any available options. If that doesn't work, post a screenshot of your desktop, and i'll have a "real" look (haha...).

---

### Post by BlueNoteExpress on 2007-08-06
Also, keep in mind that Linux is case sensitive.

realplayer is not the same as RealPlayer.

---

### Post by tqk on 2007-08-06
> **Steveway said:**
> There is NO Shockwave for Linux, so you need to keep on living without your little browsergames.

Just for the record, I don't think that's how it's done in *buntuland.  That sort of attitude is perfectly appropriate for Usenet newsfroups [sic], but *buntu expects more.  Many *buntu users will have no clue what you're berating them for, or about.

We love them anyway.  :-)

---

