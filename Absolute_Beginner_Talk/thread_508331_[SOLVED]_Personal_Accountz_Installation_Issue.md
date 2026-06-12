---
title: "[SOLVED] Personal Accountz Installation Issue"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-24
Earlier in the year I purchased a program called “Personal Accountz”, the reasons being that it can be run on Windows, Mac or Linux.

I’ll post cogent extracts showing what the problem is. First of all, a post by the Manager Quentin on the Accountz Forum:

**Quentin**:

[color=blue]If you install Personal Accountz into your home directory, or you have administrator rights on the Mac, you should have no problem as long as you ensure the permissions for the installer file has been set to Owner Execute. 

This varies according to the version of Linux you are using. In Ubuntu 6.06, right click on the application and select Properties. Choose the Permissions tab and set the Owner option to Execute. This is much the same for other flavours of Linux.[/color]

Additionally:

[color=blue]If you have a problem installing Personal Accountz on Ubuntu, please let us know which version of Ubuntu you are using, and which processor (eg. 32 or 64 bit). Write as much detail as you can and describe exactly what is happening during installation and what errors occur. 

We have tested this on Ubuntu on a 32bit platform and it installs without any problems. Here is what to do: 
1. Insert the CD into your drive 
2. Open the Linux folder and open the 32 or 64 bit folder depending on your processor 
3. Drag the relevant binary file from the above folder onto your Desktop 
4. Right click on the binary and select Properties 
5. Click on the Permissions tab 
6. Ensure the Owner permissions Execute box is ticked then close the dialogue 
7. Double-click the binary to run it and choose Run from Terminal 
8. The installer should start.[/color]

**Login the Log said:**
[color=blue]It runs OK on both Feitsy Fawn and its predecessor Edgy Eft.[/color]

**andavane said:**
[color=blue]Quentin, 
I have installed Ubuntu 7.04 "Feisty Fawn", and followed the steps you outlined. However when I double click, 'something' happens... a screen comes up very quickly and then vanishes again. Then things are back to where they were. I also downloaded the patch, with the same effect. 
I should state that I am a complete Ubuntu Greenhorn. 

i know that you begin with very minimal things to do, and then as the situation demands, you install various components from "Add/remove..." in the Application folder, so I would not be surprised if I had missed something. 

Regards 

John
_________________
omRamanaaya[/color]

**Quentin added:**
[color=blue]Just a reminder that not setting Owner Execute will result in the terminal window flashing on then off and nothing happening. Please confirm that you have: 

1) Copied paz_install.bin from the CD to your Desktop 
2) Right-clicked on it, selected the Permissions tab, ensured it is showing the 'User' name, and then set the Executable option.[/color]

**and andavane responded:**
[color=blue]Yes Quentin. 
In "Permissions" My name is displayed as owner (andavane). 
Access is set to "read and write" 
Group and others are on "read only" 
The execute box is ticked. 
When I double click, the terminal window flashes up again and then disappears. 
I note that in the "open with" tab, "text editor" is the only option. It doesn't look right to me. 
In the same box there is an "add" button and when I click that, I get a list of applications which can be used to add. There is also an option to add a custom command. I don't know what any of these things does. 
No time yet to phrase the essence of the question and problem on the Ubuntu forum, but will go there to scout for the word "accountz". 
Kind regards 
John
_________________
omRamanaaya[/color]

**and Quentin’s latest post says:**
[color=blue]It is probably the version of Java you have installed. Problem is I am not sure how to resolve that. My Ubuntu worked fine using the default settings. 

I know someone else who installed another version of Java on your version of Ubuntu and had the same result as you. They then uninstalled that version and although it still had problems, at least the console stayed open and let them know what the problem was. I am now waiting for our Java expert to come back from his hols to get a definitive answer. It will be in 3 weeks. I hope you don't mind waiting.[/color]

* and this, Gentlemen, is the point at which we are stuck ...*

Regards, John

---

### Post by zanglang on 2007-07-24
Can you try this? It will essentially require you to use the commandline... but well, hopefully we'll get some more indications on what went wrong.

The file is on your desktop, right?
Open up a terminal and enter the following:
> cd Desktop
chmod +x <complete name of file, without brackets>
./<file name again. Note the dot-slash>

Paste any errors you might've got here.

---

### Post by kt66se on 2007-07-24
The following worked for me......

1. First make sure you have run all the Ubuntu updates and also installed any java software as found in the Install/Remove software menu

2. Copy the appropiate paz_install.bin file to your home folder. (32/64bit)

3. Open a terminal and follow the next steps, you can use copy and paste from the code below into your terminal (I am assuming you have copied the paz_install.bin to yor home folder, if not use ```
ls
``` to navigate to the correct directory)

Main code to follow.......

```
sudo chmod +x paz_install.bin
```

Hit enter after the .bin

We use sudo to give us the right permissions to carry out the chmod command. chmod changes the permissions of the paz_install.bin file to the user, even if you think your file is set correctly, carry out the above code. (Your prompt should be back at the user line)

2. Type the following

```
./paz_install.bin 
```

This should open the jave installation script. Follow the prompts and install to the defaults.
Annoyingly "lots" of links and shortcust will be placed in various folder and on the desktop, you can delete these if you wish. I also found that sometimes the Personl Accountz launcher would not launch when double clicking. This I put down to the fact that Unix/Linux does not like spaces, so if you experience this, rename the Personel Accountz launcher to anything without a space, i.e PA, Personel_Accountz, Accountz etc.
You can do this by right clicking on the launcher icon and select "rename".

Hope this helps?


Kind regards

Adam

---

### Post by Andavane on 2007-07-24
Hello Zanglang
Well it went wrong right at the beginning, it wouldn't  even let me type "cd desktop", viz:

> andavane@andavane-ibm:~$ andavane@andavane-ibm:~$ cd desktop
bash: andavane@andavane-ibm:~$: command not found
andavane@andavane-ibm:~$ 

I take it that cd = change directory, right?

Regards

John

---

### Post by zanglang on 2007-07-24
Hi there. Yes, you're right, but I think you've accidentally pasted in "andavane@andavane-ibm:~$" into your command as well. Also, you'll need to capitalize 'Desktop', because it's case-sensitive. ;) You should see something like this:
```
andavane@andavane-ibm:~$ cd Desktop
andavane@andavane-ibm:Desktop$
```
This means you've successfully changed to the Desktop folder.

---

### Post by Andavane on 2007-07-24
PS:
> 
1. First make sure you have run all the Ubuntu updates and also installed any java software as found in the Install/Remove software menu

I couild not see "Java" anywhere in the add/remove applications.
Regards
John

---

### Post by zanglang on 2007-07-24
You might have to enable the 'multiverse' repository to get the Java runtime. Go to System > Administration > Software Sources, tick 'Software restricted by copyright or legal issues (multiverse)' (I'd recommend you tick all of them), click close, and choose 'Reload'.

---

### Post by Andavane on 2007-07-24
Hello Adam and Zanglang
> The following worked for me......

1. First make sure you have run all the Ubuntu updates and also installed any java software as found in the Install/Remove software menu

2. Copy the appropiate paz_install.bin file to your home folder. (32/64bit)

3. Open a terminal and follow the next steps, you can use copy and paste from the code below into your terminal (I am assuming you have copied the paz_install.bin to yor home folder, if not use
Code:

ls

to navigate to the correct directory)

Main code to follow.......

Code:

sudo chmod +x paz_install.bin

Hit enter after the .bin

We use sudo to give us the right permissions to carry out the chmod command. chmod changes the permissions of the paz_install.bin file to the user, even if you think your file is set correctly, carry out the above code. (Your prompt should be back at the user line)

2. Type the following

Code:

./paz_install.bin

This should open the jave installation script. Follow the prompts and install to the defaults.
Annoyingly "lots" of links and shortcust will be placed in various folder and on the desktop, you can delete these if you wish. I also found that sometimes the Personl Accountz launcher would not launch when double clicking. This I put down to the fact that Unix/Linux does not like spaces, so if you experience this, rename the Personel Accountz launcher to anything without a space, i.e PA, Personel_Accountz, Accountz etc.
You can do this by right clicking on the launcher icon and select "rename".

Hope this helps?


Kind regards

Adam

Something seems to be working, but I got this message:

> andavane@andavane-ibm:~/Desktop$ chmod + paz_install
chmod: cannot access `paz_install': No such file or directory
andavane@andavane-ibm:~/Desktop$ chmod + paz_install.bin ./paz_install.bin
andavane@andavane-ibm:~/Desktop$ sudo chmod +x paz_install.bin
Password:
andavane@andavane-ibm:~/Desktop$ ./paz_install.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
andavane@andavane-ibm:~/Desktop$

Unfortunately the paz_install.bin file, being on the desktop, is cluttering the desktop a bit. I'd like to get this program neatly tucked away into its own little box somewhere.

Being a post-war child, I came to computers late (in my late forties!) and do find some of this quite hard to follow. It is interesting, but I am a slow learner ;) What on earth is a "VM" ?

Can you guys make anything of all this?

Kind regards

John

---

### Post by zanglang on 2007-07-24
Don't worry, everyone starts off as a newbie. ;)

OK, You're missing Java, which is required by the installer to run, and that's why the installer failed to start. VM means "virtual machine", which in laymen's terms is the software that handles running code from a program in a way that'll work on multiple platforms (Windows, your phone, or Ubuntu), without the program explicitly knowing the actual details of the platform.

Alrighty. Now you need to install Java. Enable the 'multiverse' repository following my steps above, go to Add/Remove, search for Java 6 Web Start, tick that, and click 'OK'. Wait for it to install. Once it's done, now try and double-click the installer file and see if it works. If it doesn't, go back to the command line and do this again:
> andavane@andavane-ibm:~/Desktop$ **./paz_install.bin**

---

### Post by Andavane on 2007-07-24
> **zanglang said:**
> You might have to enable the 'multiverse' repository to get the Java runtime. Go to System > Administration > Software Sources, tick 'Software restricted by copyright or legal issues (multiverse)' (I'd recommend you tick all of them), click close, and choose 'Reload'.
Thank you Zanglang.

Under Software Sources, Ubuntu Software, all the boxes (inc software restricted (multiverse)) are already ticked.

Now the second tab (third part software) has an "Add CD-ROM" option, so I am thinking that it might be an idea to add the "Accountz" CD in here, and install the program that way. As I am so very green at all this, I thought I'd confer before proceeding...!

Regards

John

PS: yes "cd Desktop" changed the directory OK

---

### Post by kt66se on 2007-07-24
Hi John,

Looked at this a bit late but it seems like you are nearly there! :)

I am not using Ubuntu at the mo, (I test lot's of different distros), but maybe you should search for java under the package manager - synaptic instead of "Add/Remove". Use the search feature to search java, tick the java box, click on apply, then run ./paz once synaptic has finished. Don't add the CD into the source as you suggest.

You are having a lot of bad luck, it is not normally this hard to run applications on Linux, especially Ubuntu. How did you come to install Ubuntu, was it download or from a Mag DVD? 

If you get no joy, post me that you will call, I'll re-install Ubuntu on my laptop then go through the install with you.

---

### Post by Andavane on 2007-07-25
> **kt66se said:**
> Hi John,

Looked at this a bit late but it seems like you are nearly there! :)

I am not using Ubuntu at the mo, (I test lot's of different distros), but maybe you should search for java under the package manager - synaptic instead of "Add/Remove". Use the search feature to search java, tick the java box, click on apply, then run ./paz once synaptic has finished. Don't add the CD into the source as you suggest.

You are having a lot of bad luck, it is not normally this hard to run applications on Linux, especially Ubuntu. How did you come to install Ubuntu, was it download or from a Mag DVD? 

If you get no joy, post me that you will call, I'll re-install Ubuntu on my laptop then go through the install with you.

Hello there kt66se
I installed it from the distro which came the July Issue of "Linux Magazine", which I was trying.
Thank you very much for your help (and on the Accountz Forum too!). Indeed, I am "nearly there" I feel.
Actually I don't mind the problems along the way because it has been my experience in life that it is during times such as these  that a lot may be "going in". I believe that we are here to learn    :-k

Will keep things posted, and then we can post the results on Quentin's forum; We may be among the first users to have the program on Ubuntu, but I'm sure that we are not the last  :cool:

PS: Thanks for your kind offer: No need to go to the trouble of installing it again on your machine

Kind regards

John
~   ~   ~   ~   ~  ~  ~  ~   ~  ~  ~   ~  ~  ~  ~  ~  ~  ~  ~  ~  

PC: IBM Think-Centre A-50 : 40 Gb

Hard Drive 0) Windows XP-Pro (NTFS), partitioned (my data folder on a FAT32 partition)
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb (ext3)

[color=Green]My Ubuntu Strategy:
[i]Carry on doing in Ubuntu exactly what you were doing in Windows XP.
Holler when you get stuck!
Give Pranams to UbuntuFolks..[/i].[/color]

---

### Post by sigint on 2007-07-26
I also had the "... no VM ..." error.

After so much messing about with synaptic package manager, I don't remember what I loaded to make it work but this is what I currently have:-

(Do a search for "Java" and then list all those loaded by clicking the left-most  header)

bsh
gcj-4.1-base
gdb
gij-4.1
java-common
libgcj7-0
libgcj7-jar
libgcj-common
libgnome-speech3
libgtksourceview-common
libjsqldb-java
libjaxp1.3-java
libjline-java
libservlet2.3-java
libxalan2-java
libexerces2-java
libxt-java
openoffice.org
openoffice.org-base
openoffice.org-java-common
sun-java6-bin
sun-java6-jre

---

### Post by Andavane on 2007-07-26
Dear members:
I have spoken with Adam on the phone and  it turns out that I did not have the correct Linux files on the CD.
The company is posting me the latest CD today which should be with me shortly.
Regards
John

---

### Post by Andavane on 2007-07-26
Dear Friends,
A member kindly offered to help me over the telephone.
When I called last night, transcribed that I did not have the correct files on my CD.
This explains a lot!  :eek:
They are sending me a new CD in the post, so this hopefully resolves the issue.
If everything installs smoothly I shall, for the sake of completeness, round off this thread with a post explaining exactly what it is you are supposed to do.
Regards
John

---

### Post by kt66se on 2007-08-06
Hi John,

As promised, please find below a quick summary of the things we went through.

**Useful Terminal commands**

Changing a file permission so you can run it as a normal user

```
sudo chmod 777 filename (hit enter)
password
```

To execute a file to run from the terminal after permission has been changed

```
./filename (hit enter)
```

To list files in a directory

```
ls
```

To view a file

```
more filename
```

(Use space bar to see more of the file and when you want to exit, hit the “q” keyboard button)

Change directory to the “name” folder

```
cd /home/name
```

List of processes running on your PC

```
ps -aux
```

List of active processes running on your PC

```
top
```

to exit “top” type “q”on the keyboard

to shut down your PC

```
sudo halt
```

To reboot

```
sudo reboot
```

For other resources, try any of the Ubuntu books at Amazon, the dummies books will give you a good start in using basic command line options.

Cheers

Adam

[www.g17.co.uk](www.g17.co.uk)

---

### Post by kt66se on 2007-08-06
Oh, just in case you have trouble running any of the PA updates try the following



(You will have downloaded the file to a folder - navigate to that folder using the terminal, once there follow the commands below)

```
sudo chmod 777 the_paz_upgrade_filename (hit enter and enter your password when prompted, then enter again)
```

Next

```
./the_paz_upgrade_filename (hit enter)
```

Follow the on-screen prompts

Job done - you may have to re-enter your CD Key again!

---

