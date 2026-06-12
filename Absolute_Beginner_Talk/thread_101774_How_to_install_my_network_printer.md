---
title: "How to install my network printer"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Leon on 2005-12-10
Hi all,
First of all, I'm new to Linux - ubunto...:) 
I have a Xerox 6100 network printer and  connected this printer trough Cups / IPP
This printer is a Postscript printer and therefore I use a generic PS driver and a PPD for the 6100.
It seems that the print file is send to this printer bus no test page is printed out.
I tried to install the Xerox driver, witch is available, but I don't no how to install this driver. I used the Phaser 6100Drv_i386 file and, according to the help file, I need to run setup.sh. How do I do this? I tried to use sudo setup.sh and ./setup.sh. Both fails.

You're help is more than welcome!

---

### Post by janrinok on 2005-12-11
Ok, a few questions.

How do you know that files are sent to the printer?  Do you see the data light flashing or is there some other indication?  Is it just the test page that does not print or is it all files?

What kind of network have you got?  Is there more than one computer on the network and, if yes, can they talk to each other? (Have you used 'ping'?)

It might be that we first have to make sure that your network is functioning and then we can start on the printer but, either way, it shouldn't be too difficult.  (I bet I am going to regret saying that.....!)   Jan

---

### Post by janrinok on 2005-12-11
To use setup.sh, you must first make sure that it is executable.  Do you prefer working through a GUI or the command line?  If GUI, find the setup.sh file, right click, and select Properties. Under Permissions, make sure that the file has Execute selected.  The command line is just as easy.  Change to the directory in which you have the setup.sh file (e.g. cd /this/is/it/setup.sh).  Type the following command:

chmod +x setup.sh

which will set the file to be executable.  Of course, you cannot change the attributes of the file on the CD, so you will have to copy it (and all the other relevant files) somewhere onto the hard drive e.g. ~/6100.  Change the attributes of the copy on the hard drive.  The commands that you have already tried should then work, but you will have to use them as root (i.e. using the sudo command) to install new drivers.  But as you have already tried that I know that you are happy using sudo so I will not go through a step by step guide.  

By the way, are you using a parallel connector or is it a true network (i.e. ethernet) connector) to the printer?

---

### Post by Leon on 2005-12-11
Hi,
Thanks for You're help!
The printer is a network printer with embedded ethernet card. Prints fine from Windows trough LPR and supports port 9100 and ipp on port 631
I checked the permissions, all oke.
When I run setup.sh I see the following:
----------------------------------------------------
jan@ubuntu:~/6100Drv_i386$ sudo ./setup.sh
/home/jan/.setup11294: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
jan@ubuntu:~/6100Drv_i386$
-----------------------------------------------------
I do'nt no how to search for this file. Can I find it somewhere and where to drop it?
Thanks again,
Jan

---

### Post by janrinok on 2005-12-11
Leon
Your installation does not yet have the correct library installed, but this is easily solved.  You can use Synaptic to install the appropriate library.  First of all, open Synaptic (System-Administration-Synaptic from the ver y top menu).  Once it has opened, search for 'libgtk' - mine lists both libgtk1.2 and libgtk2.0.  Select libgtk1.2 and libgtk1.2-common.  It will probably select the second file automatically when you install the first, it might even select several more files.  No problem, just accept them all.  Once you have marked the files for installation, press 'Apply' and this rest should be automagic.
If your Synaptic does not find the appropriate file then you probably haven't selected the appropriate repositories.  Not sure how much you know about Synaptic, but it requires various sources for files including the original CD and various online locations.  Basically, in the Synaptics menus, select Settings-Repositories and make sure that everything that is available there is selected and then 'Reload', 'Search' and 'Apply'.
We know that the hardware (printer, network card and cable) all work because you have used them under Windows.  What we do not know is whether they are correctly setup under Linux.  If you still experience problems after installing the libgtk file, please include the output from running 'ifconfig' on the command line.  You have told me the port number (9100, and IPP on port 631) but not the printer's IP address.  This might be provided automagically during the installation of the driver but we need to know the IP address that we are trying to connect to, so that we can test the network connection as far as the printer under Linux.  I'll google for some answers while you try to install the library files. Cheers, Jan.

---

### Post by Leon on 2005-12-11
Thanks Jan,
The installation runs! Thanks. Unfortunally, a new problem occours :-(
To add a printer I need to login as root. This tool is not accepting my root password..
I did a reset from Users and groups without a result. Can you help me with this?
Thanks again,
Leon

---

### Post by janrinok on 2005-12-11
Leon, I'm not sure that I understand what you me when you describe the current problem.  If the 'tool' (I assume you mean the Xerox program but, if I am wrong, then you will have to correct me!) requires root permissions when you start it from the command line then prefix it with 'sudo' before you start it.  Any program that requires a root password should accept the sudo password.  If you are trying to start the 'tool' from a menu and it will not let you then that indicates that we need to change the way in which the menu item works.  Let me know which it is, please.  Also, let me know how your network is set up.  Is it just one computer and the printer, or have you got other computers/devices on the same network?  It will help me to solve network problems if I know how it is set up - if your printer simply works then there are no problems and you will be another happy Ubuntu user! Jan
p.s.  I'm going to be offline for a few hours. I have another life outside of Linux and sometimes I have to leave the computer for a while.  But hopefully you will be successful... J

---

### Post by n0fx on 2005-12-27
Leon,

I have the same phaser printer but I got the same place you did.  Did you figure how to bypass the authentication part?  It asks for the root password but it doesn't seem to accept my sudo password and I also tried running sudo linux-config in the terminal but it doesn't work either.

If anyone knows or set this printer up before, please post here on how to get it to work.

Thanks.

---

### Post by B3Nji on 2006-03-20
bump!!

I too am having the exact same problem with the password. 
I start the config program with "sudo linux-config" and get the option to add a new printer, when I click add it asks for my root password, it tells me that it is wrong. Surely other people have come across this and have a fix? 

Thanks for your help guys.
Ben

---

### Post by n0fx on 2006-03-22
[QUOTE=B3Nji]bump!!

I too am having the exact same problem with the password. 
I start the config program with "sudo linux-config" and get the option to add a new printer, when I click add it asks for my root password, it tells me that it is wrong. Surely other people have come across this and have a fix? 

Thanks for your help guys.
Ben[/QUOTE]

Ben,

Did you try contacting Xerox regarding the issue?  Maybe you'll get lucky and they'll provide you with a solution.  I tried to contact them on the web but I never got an answer back.

---

### Post by B3Nji on 2006-03-23
[QUOTE=n0fx]Ben,

Did you try contacting Xerox regarding the issue?  Maybe you'll get lucky and they'll provide you with a solution.  I tried to contact them on the web but I never got an answer back.[/QUOTE]

cheers for the info m8ty, 

but in my experience when you try to contact a company like xerox you get what you got. Buff all! 

I have found that a few peeps are having the same problem, but they dont seem to have a answer either! 

thanks for your help anyway

---

### Post by n0fx on 2006-03-23
Ben,

I wanted to let you know that I also just tried logging in as root in gnome and running the linux-config command in the terminal but it still asks for an administrator account.

---

### Post by n0fx on 2006-04-17
I finally got this damn printer working.  It was a long process of trial and error but what I found out is this is a damn Samsung CLP-500 printer.  This was just rebadged by Xerox.

Ok, in order to install this, I grabbed this driver:

[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=IN&CttFileID=306148&CDCttType=DR&ModelType=N&ModelName=CLP-500&VPath=DR/200504/20050425144910781_lpp-1.1.7-27-i386.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=IN&CttFileID=306148&CDCttType=DR&ModelType=N&ModelName=CLP-500&VPath=DR/200504/20050425144910781_lpp-1.1.7-27-i386.tar.gz)
filename: 20050425144910781_lpp-1.1.7-27-i386.tar.gz

Extract the contents and you'll get an /image folder.

Now, make sure your root user has a password by doing this in the shell:

sudo passwd root

You'll need to add cupsys user to the shadow group, so you'll need to do this:

sudo vigr

navigate inside the screen until you find something that says this:

shadow:x:42 

go to the end of this line and just enter any letters (ie abdc), now erase what you just typed and make sure it looks like this:

shadow:x:42:cupsys

Once you add that in, press escape on the keyboard and type in :w (to save it) and then type in :qa! to quit back into the shell.  Now, in the shell, navigate to the folder where you have your /image folder from the download you did earlier.  So, in my setup, it was in /home/n0fx/Desktop/image

cd /home/n0fx/Desktop/image

Now, run the setup by doing this: 

sudo sh setup.sh 

and do the expert install.  Afterwards, run the linux-config program (in the shell or the setup will invoke it after it's done) to add your printer.  Make sure to pick the Samsung CLP-500.  When the program asks for the administrator of the computer, enter root as the username and your password you setup earlier. 

I got mine to print via the network. Once it's all setup, delete the root password by going into the shell and typing:

sudo passwd -l root

and it should be disabled.  I haven't had a chance to test all the features but it prints the test page fine.  This should work fine if it's installed via USB or parallel probably. If you check under System -> Administrator -> printing, there should be a printer called lp and that should be fine.  All the jobs will be sent to that printer, which is the Phaser 6100.

Happy Installing! :D

---

