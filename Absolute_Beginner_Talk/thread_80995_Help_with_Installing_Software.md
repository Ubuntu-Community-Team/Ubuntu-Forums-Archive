---
title: "Help with Installing Software"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by SlackerHacker12 on 2005-10-23
Hello, 
I'm rather new to Ubuntu, and I seem to be having trouble with installing a program.  I wanted to install Blender3D, and I know (or I think I know) that I have to compile the .tar.bz2 file in order to use it, but I do not know how.  Would anyone be so kind as to give me advice on how I could go about doing this?

Any help is appreciated.  

Thank you. :)

---

### Post by Snakey on 2005-10-23
Extract the file to your home folder, go to the terminal (apps >system) ant type
./configure
make
make install

OR: you could install blender through synaptic or the install apps - program

---

### Post by herrpoon on 2005-10-23
Hi there!

The beauty of ubuntu is that you don't have to compile stuff yourself, this means you don't have to worry about dependencies and the like which for someone who isn't very experieneced, makes things a lot easier!

The best way to install new software is to go to system--administration--synaptic package manager and then just search for the software you want!  Once you've found what you're looking for, just click install and there you go!  Try taking a look at [www.ubuntuguide.org](www.ubuntuguide.org), an excellent starter point :D

---

### Post by SlackerHacker12 on 2005-10-23
I'll try that.  

Thank you!

---

### Post by Lisa_T on 2005-10-23
Every time I try to use ./configure in terminal, I get an error message saying there's no such file or directory. How can i fix that?

---

### Post by aysiu on 2005-10-23
How funny! My tutorial on installing software easily in Ubuntu (see the second link in my sig) is for Blender specifically.

---

### Post by Snakey on 2005-10-23
It depends on what you've downloaded, if its a deb, then install it with
sudo dpkg -i yourfile.deb
If it's a rpm, you'll need to have alien (sudo apt-get install alien)
and then convert the rpm to a deb with alien:
sudo alien yourfile.rpm

---

### Post by aysiu on 2005-10-23
Why would you install Blender from a .deb, .rpm, or .tar.gz when it's in the repositories? Please, just read the second link in my sig--it has screenshots and walks you through installing it step by step... the **easy** way.

---

### Post by David Marrs on 2005-10-23
Possibly an even easier option is to select "add applications" from the applications menu and install blender from there.

---

### Post by SlackerHacker12 on 2005-10-23
I'm sorry, but I did not mention that the computer that I'm installing these programs on does not have internet access.  My bad.

So, if you could tell me how I can install the program without using the internet, it would be appreciated.

---

### Post by blastus on 2005-10-23
I just wrote a discourse about that here; [url=http://www.ubuntuforums.org/showthread.php?t=80974] 	
Updating packages/ ubuntu without internet[/url] :)

---

