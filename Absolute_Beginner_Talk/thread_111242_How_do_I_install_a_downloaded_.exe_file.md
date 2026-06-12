---
title: "How do I install a downloaded .exe file?"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by bigdog427 on 2006-01-01
Hello,

	Just trying out Ubuntu for the first time. The OS has been installed for an hour or so. Nice, I like it. Trying to get things setup & install a program that I have downloaded. Downloaded **folding@home** to the desktop. The file is _FAH504-Linux.exe_. I need to convert the program into a file that I can execute. According to the FAH website, I need to type _chmod +x FAH5-Linux.exe_ into the command line. I just can’t seem to find how to open the command line. I’m sure that I am just overlooking the interface, but I feel that I have looked everywhere. I don’t want to get frustrated this early. So, someone please tell me how to open the command line & what I should enter. Thanks for your help, I’m an old Windows user & just want to try something new. Please forgive my ignorance. 

           Darren

---

### Post by phido on 2006-01-01
Alt+F2 and then enter terminal or konsole and it shows up, in the menu its under system. U will need to type *sudo* befor the command for root priveligies.

---

### Post by Mustard on 2006-01-01
The command line, also known as the terminal, is found in your Applications>>Accessories menu, if you are on Breezy Badger.

The command you would enter, assuming the file was saved in your /home/user directory is

sudo chmod +x FAH5-Linux.exe

You'll be asked to enter a password.  Enter your user password.

Alternatively, if you are using gnome, you could browse to the folder the installer is in, right click on the file, select properties, go to the permissions tab, and tick the 'execute' box.

---

### Post by bigdog427 on 2006-01-01
[QUOTE=phido]Alt+F2 and then enter terminal or konsole and it shows up, in the menu its under system. U will need to type *sudo* befor the command for root priveligies.[/QUOTE]

Hello, I have already tried the terminal. I guess that I am not entering it correctly. Please let me know what the proper way to enter it is. Thanks

---

### Post by phido on 2006-01-01
oh sorry, its **T**erminal

---

### Post by bigdog427 on 2006-01-01
[QUOTE=Mustard]The command line, also known as the terminal, is found in your Applications>>Accessories menu, if you are on Breezy Badger.

The command you would enter, assuming the file was saved in your /home/user directory is

sudo chmod +x FAH5-Linux.exe

You'll be asked to enter a password.  Enter your user password.

Alternatively, if you are using gnome, you could browse to the folder the installer is in, right click on the file, select properties, go to the permissions tab, and tick the 'execute' box.[/QUOTE]

OK Terminal? I have tried 

sudo chmod +x FAH5-Linux.exe

and

sudo chmod +x FAH504-Linux.exe.

I get a “no such file or directory” error message. The file is saved in my home/user/desktop folder. I feel like such an idiot. Haven't looked into Gnome yet, but I will. Thanks

---

### Post by phido on 2006-01-01
*cd ~/Desktop  - for your desktop*
and then
* sudo chmod +x FAH504-Linux.exe*
should work :smile:

---

### Post by ardchoille on 2006-01-02
[QUOTE=bigdog427]Hello,

	Just trying out Ubuntu for the first time. The OS has been installed for an hour or so. Nice, I like it. Trying to get things setup & install a program that I have downloaded. Downloaded **folding@home** to the desktop. The file is _FAH504-Linux.exe_. I need to convert the program into a file that I can execute. According to the FAH website, I need to type _chmod +x FAH5-Linux.exe_ into the command line. I just can&#8217;t seem to find how to open the command line. I&#8217;m sure that I am just overlooking the interface, but I feel that I have looked everywhere. I don&#8217;t want to get frustrated this early. So, someone please tell me how to open the command line & what I should enter. Thanks for your help, I&#8217;m an old Windows user & just want to try something new. Please forgive my ignorance. 

           Darren[/QUOTE]
Where did you download FAH5-Linux.exe from? I would like to take a look at this file. The reason I think this is fishy is because a .exe will not run in Linux unless you use something like wine, and anyone who develops a Linux binary would never give it a ".exe" file extension. I'd like to run a few commands on that file to see exactly what kind of file it is. Do you have the URL you downloaded it from? Sounds to me like this is a Windows .exe file that someone mistakenly added the word "Linux" to the filename.

---

### Post by Mustard on 2006-01-02
[QUOTE=ardchoille]Where did you download FAH5-Linux.exe from? I would like to take a look at this file. The reason I think this is fishy is because a .exe will not run in Linux unless you use something like wine, and anyone who develops a Linux binary would never give it a ".exe" file extension. I'd like to run a few commands on that file to see exactly what kind of file it is. Do you have the URL you downloaded it from? Sounds to me like this is a Windows .exe file that someone mistakenly added the word "Linux" to the filename.[/QUOTE]

I checked that out myself, by googling up the link.  It really is a linux install file that ends in an .exe extension.  There is nothing theoretically wrong with this, as the .exe extension is irrelevant in linux.  The file will however be an executable when given executable privileges using the chmod command.  I found it a bit unusual that it was using the .exe extension, but I guess they have there reasons for doing so. :)

---

### Post by bigdog427 on 2006-01-02
[QUOTE=Mustard]I checked that out myself, by googling up the link.  It really is a linux install file that ends in an .exe extension.  There is nothing theoretically wrong with this, as the .exe extension is irrelevant in linux.  The file will however be an executable when given executable privileges using the chmod command.  I found it a bit unusual that it was using the .exe extension, but I guess they have there reasons for doing so. :)[/QUOTE]

Mustard,

	Thanks for all your help. I think I have installed the program. If it were a Windows PC, I would say that it looks like I unzipped the files to my desktop. I’m not sure what to do now, but I will take that up with the Folding community. I am used to being asked where I want to install the files. Ubuntu just did it. Where do I go to learn about the commands that you gave me? cd ~/Desktop opens the desktop directory. sudo does what? The chmod +x makes the file executable?  I’m sure there are many more. 

	I am just trying to breath some new life into an older PC. I am mainly going to use it as a Folding computer. Just playing around, but I am interested in learning more about Linux. Thanks for your help. Any other pointers you can give me will be greatly appreciated. 

	Thanks - Darren

---

### Post by Zimmer on 2006-01-02
Go for the Tuxfiles link and this one
[http://tille.xalasys.com/training/tldp/ch02s02.html](http://tille.xalasys.com/training/tldp/ch02s02.html)
for basic Linux command line command info.
Personally I like Ubuntu for the Synaptic package manager ease of use, compared with other distros . The less you have to use the command line the better, but it is good to have a choice.

---

### Post by bigdog427 on 2006-01-02
[QUOTE=Zimmer]Go for the Tuxfiles link and this one
[http://tille.xalasys.com/training/tldp/ch02s02.html](http://tille.xalasys.com/training/tldp/ch02s02.html)
for basic Linux command line command info.
Personally I like Ubuntu for the Synaptic package manager ease of use, compared with other distros . The less you have to use the command line the better, but it is good to have a choice.[/QUOTE]

Thanks Zimmer

I know just enough to be dangerous. It seems the more I learn, the less I know. But I have to start somewhere.

Thanks Again - Darren

---

### Post by TeeAhr1 on 2006-01-02
[QUOTE=bigdog427]I am used to being asked where I want to install the files. Ubuntu just did it.[/QUOTE]
That's a Firefox default, it annoyed me at first too.  You can change it like so: (in Firefox) Edit > Preferences, go to the "Downloads" tab, and select "Ask me where to save every file."

---

### Post by Iandefor on 2006-01-02
[quote=bigdog427]Thanks Zimmer

I know just enough to be dangerous. It seems the more I learn, the less I know. But I have to start somewhere.

Thanks Again - Darren[/quote] I suggest you look for the package in Synaptic. Before you do that, though, I'd enable the Universe and Multiverse repositories (if you haven't already done that). Here are a few links to help you get started:
[How to Use Synaptic]("https://wiki.ubuntu.com/SynapticHowto")
[How to Add Repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto") 
[What is A Repository?]("https://wiki.ubuntu.com/Repositories")

---

### Post by bigdog427 on 2006-01-02
[QUOTE=Iandefor]I suggest you look for the package in Synaptic. Before you do that, though, I'd enable the Universe and Multiverse repositories (if you haven't already done that). Here are a few links to help you get started:
[How to Use Synaptic]("https://wiki.ubuntu.com/SynapticHowto")
[How to Add Repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto") 
[What is A Repository?]("https://wiki.ubuntu.com/Repositories")[/QUOTE]

Hi, Thanks. I have looked through these items & feel that I have a basic grasp of them. The problem that I was having was that I was trying to install a downloaded file. I was trying to run folding@home. It seems that I have installed it, now I just need to figure out how to run it. Anyone have any experience running Folding? Thanks

---

### Post by Iandefor on 2006-01-02
[quote=bigdog427]Hi, Thanks. I have looked through these items & feel that I have a basic grasp of them. The problem that I was having was that I was trying to install a downloaded file.[/quote] I know you were trying to get help installing the downloaded file; my thought was, however, that since you were trying to install a package, you could just as easily search for it in Synaptic and there would be a good likelihood that it would be in the repositories.

---

### Post by bigdog427 on 2006-01-02
[QUOTE=Iandefor]I know you were trying to get help installing the downloaded file; my thought was, however, that since you were trying to install a package, you could just as easily search for it in Synaptic and there would be a good likelihood that it would be in the repositories.[/QUOTE]

Hello, Is it a package? If it is a package, where would I look for it in Synaptic? Thanks

---

### Post by Iandefor on 2006-01-02
[quote=bigdog427]Hello, Is it a package? If it is a package, where would I look for it in Synaptic? Thanks[/quote] Yes, it is. A package is a generic term for a program or a set of programs, or a library or header file. I've already searched Synaptic and there isn't a package for Folding@Home, but you have two options to find a package (for future reference). 

Option 1: If you want to be cryptic, you can use a terminal to run the following command:

```
sudo aptitude search [Keywords]
``` Where [Keywords] is replaced by the search terms. 

Option 2: Open up Synaptic, and click on the "find" button, and enter your search terms.

---

