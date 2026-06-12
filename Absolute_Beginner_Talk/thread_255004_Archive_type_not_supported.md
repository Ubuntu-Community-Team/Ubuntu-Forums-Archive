---
title: "Archive type not supported???"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by thenewdeal38 on 2006-09-10
I keep getting this whenever I download any software can anyone please help me!****

---

### Post by meng on 2006-09-10
Yes. Please don't double post. Please be patient.
Please explain exactly what you are trying to do. What file are you downloading, from where, and using what - wget, firefox, Synaptic package manager. This is not clear in your note.

---

### Post by thenewdeal38 on 2006-09-10
Well when i download for example lime wire for linux i open the folder and a screen that says archive type is not supported, what does that mean? Im using firefox.

---

### Post by jordanmthomas on 2006-09-10
I went to the limewire site, and it has you download the software as an rpm.  Ubuntu packages have the name deb.  All is not lost, you can still use it...
```

cd ~/Desktop
sudo apt-get install alien
sudo alien *.rpm
sudo dpkg -i *.deb

```

This will change to your Desktop directory (I'm assuming this is where you saved it)
Install alien, which converts rpms to debs
Convert the rpm
Install the deb

You're good to go

---

### Post by thenewdeal38 on 2006-09-10
In english please, what does that mean i mean when i download what should i ask fire fox to open the file with?

---

### Post by jordanmthomas on 2006-09-10
You should tell it to save to the Desktop first.
Then open a terminal and do the commands I listed.

---

### Post by thenewdeal38 on 2006-09-10
I dont understand ive only used windows would it be to much for a step by step guide, by the way the window asks me to either open with then i have the option of archive manager (default) , if i scroll down i get other with sends me to this window with home desktop,file system,cd, floppy and bin  or if i dont scroll down it also saves to disk. Thanks your saving my life, seriosly i appreciate your help!:p

---

### Post by jordanmthomas on 2006-09-10
Sooo...you have it figured out?  I'm not sure if you are still asking for help.

---

### Post by thenewdeal38 on 2006-09-10
I dont even know where to begin i need step by step help im still stuck on the choose helper application window.

---

### Post by meng on 2006-09-10
jordanm already gave you a step-by-step guide. I guess you didn't realize since you so rudely asked again for "in english" and then "would it be to much"!

To recap:
1. Open Terminal. This is under Applications > Accessories > Terminal
2. Type the commands that jordanm posted, one after the other in the Terminal.

This should install the software. What you are trying to do (i.e. install non-Ubuntu configured binary programs) is not a simple, straightforward process and can also create minor problems with running software. It is not generally recommended for users with your level of expertise. That is why installing software from Ubuntu repositories is recommended.

---

### Post by jordanmthomas on 2006-09-10
You need to click 'Save to Disk'

---

### Post by jimmygoon on 2006-09-10
> **thenewdeal38 said:**
> I dont even know where to begin i need step by step help im still stuck on the choose helper application window.

n00b: start with the basics. read. follow instructions.

1. save it to desktop
2. open terminal
3. type in the commands that were listed above

There... "steps"... that was what was written above.... I just typed it out... READ! Its the only way you will learn linux. Also, frostwire is better than limewire and 100x easier to install ;)

---

### Post by jordanmthomas on 2006-09-10
jimmygoon, I think he is having trouble saving it to his Desktop.

---

### Post by thenewdeal38 on 2006-09-10
yes sorry but thanks yeagh how do i save it to my desktop ps when i type all that in the command it asks for my password but when i try typing my password in the terminal it wont let me, thanks and im not trying to be rude im just uber noob.

---

### Post by meng on 2006-09-10
Desktop is the default download location for Firefox. So unless you changed it, your file is located in ~/Desktop.
Your password will not be echoed to the screen when you type it. This is for security reasons, so if I was looking at your screen I couldn't see your password. Just type the password and press enter.

---

### Post by jordanmthomas on 2006-09-10
When you click the download link, the window comes up, right?
This window has  a button that says "Save to disk"
Click this button.
Wait for it to finish downloading.
Go to Applications --> Accessories --> Terminal at the top of your screen
issue the commands I gave earlier.


As for sudo not taking your password, it is accepting it.  It doesn't show anything as a security measue so people can't walk by and be like, "hey, you only have 4 letters in your password"

**edit**
beaten...

---

### Post by meng on 2006-09-11
Is it my imagination or is poor etiquette on the rise in these forums?

---

### Post by jordanmthomas on 2006-09-11
I don't know.  I've only been here about a week.

---

### Post by meng on 2006-09-11
You've been pretty active in that week, judging by your post count. Anyhow, I'm guessing the OP has given up.

---

### Post by nudnik on 2006-09-11
As a Bovine American I proudly request a copy of Mubuntu. I trust it is hoove friendly, human keyboards can be a bother.

:mrgreen:

---

### Post by thenewdeal38 on 2006-09-11
Thanks alot i really appreciated the help, cheers!!!

---

### Post by thenewdeal38 on 2006-09-11
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)'
in the drive '/cdrom/' and press enter
 Whaaaaaat!!! A friend of mine downloaded ubuntu online for me so i dont have any cd's what should I do???

---

### Post by jordanmthomas on 2006-09-11
Did you ever get it working?

---

### Post by thenewdeal38 on 2006-09-11
no

---

### Post by Najand on 2006-09-11
> Media change: please insert the disc labeled
'Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)'
in the drive '/cdrom/' and press enter
Hmm, if you have Internet access and can download the iso image then download it and then mount it using the following command:
```

sudo mount -t iso9660 -o loop <File Name>.iso /media/cdrom

```

It will behave as you have the original CD mounted in your computer, though you don't need to burn it on a media and waste a cd-rom.

---

