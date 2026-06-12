---
title: "General Newb Questions"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by clueo8 on 2005-09-20
I have installed Kubuntu with KDE.  I'm having trouble with some common tasks.

1. When in a shell, i can run tar to extract files to a folder but "./configure" never works, nor does "make" or "install" and whatever else should work to install certain software.

2. How can i have root rights to change a protected system file with a file editor in KDE? I'm trying to edit a config file in a x11 directory to change my max screen resolution.  Is this the right way how to do that?  by editing this file?  I try to use "sudo kate" in a konsole window but that never works to open the program up with the right permissions.

3. I'd also like to edit my etc/fstab file, so I guess if #2 was answered, I'd be ok.

4. I downloaded eDonkey2000 and I would like to put that edonkey2000 folder in like the opt/ directory or where ever the "program files" like folder is... Then, in order to run the program, I don't think it has to be compiles, but just run with the run-eDonkey.sh file.  I did a "./run-eDonkey" by accident and somehow got it working!  How would I create like a desktop link which will have ./ in front of it so a double click would open it up.

Thanks for all your help in advance!

---

### Post by katu on 2005-09-20
1. As far as I know Kubuntu comes without installed make or compilers. You should do:
```
sudo apt-get install make gcc g++ 
```
this will ask for your user password. It should then download the needed packages.
You may also need the packages: gcc-3.4 g++-3.4

4. you could also run this from anywhere by executing:
```
/opt/<Nameofyouredonkeydirectory>/run-eDonkey
```
to create a link on the desktop, right click on the desktop, choose create launcher.
The important thing is to use:  
/opt/<Nameofyouredonkeydirectory>/run-eDonkey
as the command. Type is application. Should work. (note, I am doing this on my ubuntu machine) As soon as I get home I'll look at my kubuntu box to confirm this, and look at the other two. cheers,
Katu

---

### Post by davmac on 2005-09-20
1. You can also "sudo apt-get install build-essential"
2 & 3. I remember hitting this problem with kubuntu when I tried it. I got round it by using "sudo vim /etc/fstab" etc... Perhaps you could also try "sudo su" followed by "kate /etc/fstab"?

Dave Mac

---

### Post by clueo8 on 2005-09-20
So will "sudo apt-get install build-essential" get all the ones I need?  or do I need to do what the 2nd post said?

Also, with the eDonkey program, there is an executable file and then the shell stript to run it.  When I double click the shell script or even the excutable, it does nothing.  Only when ./ is in front of the shell script.  Is there anything special that I need to put with the "link to application" that will be on my desktop?  Or will this string I run up top take care of something to make the program run.  I hate how everything in kde tries to open with konquerer!

---

### Post by davmac on 2005-09-20
Not sure about the eDonkey question, but build-essential should install most of the stuff you need for compiling. Can't guarantee it'll work because it depends on what you're compiling so YMMV.

Regards,

Dave Mac

---

### Post by katu on 2005-09-20
1. It should be okay to install the build-essential package.
2&3. The su; sudo Kate doesn't work either. Text based editors do seem to work though.  If you don't like vim, you could try:
sudo nano /etc/fstab 
nano is a lightweight editor.
4. I don't know what the eDonkey scirpt does exactly, but in principle it should work if you:
right click on the wallpaper ->  create new ->link to application. 
What is important is the application tab and sections command and work directory.
You can choose these from the graphical interface. The work directory is the one where your script is located. 
Hope this helps,
Katu

---

### Post by Hobbsee on 2005-09-20
[QUOTE=katu]1. It should be okay to install the build-essential package.
2&3. The su; sudo Kate doesn't work either. Text based editors do seem to work though.  If you don't like vim, you could try:
sudo nano /etc/fstab 
nano is a lightweight editor.
4. I don't know what the eDonkey scirpt does exactly, but in principle it should work if you:
right click on the wallpaper ->  create new ->link to application. 
What is important is the application tab and sections command and work directory.
You can choose these from the graphical interface. The work directory is the one where your script is located. 
Hope this helps,
Katu[/QUOTE]
 sudo kate doesnt generally work, you're right.

Have you tried "sudo kwrite" instead?  It's another text editor, similar to kate

---

### Post by clueo8 on 2005-09-20
kwrite did the trick!  I'm still trying to drag and drop a folder from my desktop, into the /opt directory!  Access Denied!  Its not easy to do alot of things with the KDE UI is it? its still mostly terminal work... am i right?

---

### Post by Xian on 2005-09-20
You can do it either from a terminal of via SU Konqueror.

KDE Start Menu > Run Command
Enter 'kdesu konqueror'.

---

### Post by clueo8 on 2005-09-21
I installed the compiler thing that was stated to install, and when i type ./configure to run, it doesnt... Does there have to be a file called 'configure' in the actual directory for this to work?  Maybe I dont have to compile these programs like this.

---

### Post by katu on 2005-09-22
> Does there have to be a file called 'configure' in the actual directory for this to work?

Yes. The ./ implies you want to run a file from the current directory. Some packages don't have a configure script. See if there is a README or INSTALL file in the directory.  They should have instructions as to what to do.

---

