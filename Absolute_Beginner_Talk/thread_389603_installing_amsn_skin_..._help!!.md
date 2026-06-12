---
title: "installing amsn skin ... help!!"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by deafchickadee on 2007-03-20
Okay I want to install a skin for amsn.....   i can successfully extract it with no problems via Terminal, no problems.

```

cd ~/Desktop
unzip -x AQUA-0.95.zip
```

My problem is to install the extraction won't go into the appropiate folder: 

/usr/share/amsn/skins.

Neither of the following extraction destinations would work.....  

```
mkdir ~/.amsn/Skins/Aqua
cp -R /Desktop/Aqua/* ~/.amsn/Skins/Aqua
```

```
sudo cp ~/.amsn/skins/SKINFOLDER /usr/share/amsn/skins
```

I know I have it wrong, but I can't remember/figure it out.

---

### Post by cowlip on 2007-03-20
cp -R /Desktop/Aqua/*

That looks wrong, did you try  "cp -R ~/Desktop/Aqua/*" ?

Just so you know in the future, you can run Nautilus with root priveleges by adding "gksudo nautilus" to anywhere in your Gnome or KDE/whatever menu--just right click on it and choose "Edit menu".  It tends to get more unstable and crashy like this but it can be easier than the command line.

---

### Post by deafchickadee on 2007-03-20
I don't want to save it onto my desktop,

I want to save it in here /usr/share/amsn/skins 

it comes up with this response,

```
ella@ella-laptop:~/Desktop$ sudo cp ~/usr/share/amsn/skins
Password:
cp: missing destination file operand after `/home/ella/usr/share/amsn/skins'
Try `cp --help' for more information.
```

---

### Post by deafchickadee on 2007-03-20
extraction/install instructions from [here]("http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Installing+Plugins+and+Skins")

> aMSN can be installed to "/usr/share/amsn" if it was installed using a package or it can be to "/home/YOUR_USER_NAME/msn" if extracted from an archive.

To install a plugin, just download it, and extract the files from the .zip file (.zip, .tar.gz or similar). Then copy the extracted plugin folder to one of the following locations :
"/usr/share/amsn/plugins"
"/home/YOUR_USER_NAME/.amsn/plugins"

The plugin should appear in the plugins selector dialog. You don't need to restart aMSN.

To install a skin just download it, and extract the files for the .zip file (.zip, .tar.gz, or similar). Then copy the extracted skin folder to one of the following locations:
"/usr/share/amsn/skins"
"/home/YOUR_USER_NAME/.amsn/skins"

The skin should appear in the skins selector dialog. 

---

### Post by cowlip on 2007-03-21
Alright, assuming all the files are extracted into the directory ~/Desktop/Aqua, have you tried this? (Copy and paste)

cp -R ~/Desktop/Aqua ~/.amsn/Skins/

OR

sudo cp -R ~/Desktop/Aqua /usr/share/amsn/skins/

I'm sure there's a way to extract directly into that folder as well with the unzip command but I'm not on Ubuntu right now so can't check the man file.  Another trick is that you can create any missing directories doing "cp -Rd".

I thin kthe reason the last error came up is because cp relies on syntax like this: cp $FROMPATH $TOPATH .  You need both directories for cp to know what to do wth it.  

Have you had any better luck using "gksudo nautilus" to do this?

---

### Post by deafchickadee on 2007-03-21
```
ella@ella-laptop:~/Desktop$ sudo cp -R ~/Desktop/Aqua /usr/share/amsn/skins/
cp: cannot stat `/home/ella/Desktop/Aqua': No such file or directory
ella@ella-laptop:~/Desktop$ sudo cp -Rd ~/Desktop/Aqua /usr/share/amsn/skins/
cp: cannot stat `/home/ella/Desktop/Aqua': No such file or directory
ella@ella-laptop:~/Desktop$ 
ella@ella-laptop:~/Desktop$ cp -R ~/Desktop/Aqua ~/.amsn/Skins/
cp: target `/home/ella/.amsn/Skins/' is not a directory: No such file or directory
```

This is what is showing..  no file or directory :( 

How can i do the gksudo nautilus way? can tell me how to do this? I know its shakier doing this way which is why I've done everything via the terminal..    

:KS

---

### Post by cowlip on 2007-03-21
To do that, hit ALT + F2 and type in "gksudo nautilus" and then type in your password.

From the error above, it looks like cp needs to create the skins directory first, so just add the "d" to thr -r, so it's "cp -Rd"

THe other thing seem to be that /home/ella/Desktop/Aqua doesn't exist.  That's really weird, what happens when you do this:

ls /home/ella/Desktop/Aqua

---

### Post by deafchickadee on 2007-03-21
> 
To do that, hit ALT + F2 and type in "gksudo nautilus" and then type in your password.

..  and?..  I need my hand held!! ](*,) 

do i drag and drop? I can't find the folder on the desk top. Nothing there...Does it need t be extracted first onto the desk top?
> 
From the error above, it looks like cp needs to create the skins directory first, so just add the "d" to thr -r, so it's "cp -Rd"

I did, came back as this............... 

```
lla@ella-laptop:~/Desktop$ sudo cp -Rd ~/Desktop/Aqua /usr/share/amsn/skins/
cp: cannot stat `/home/ella/Desktop/Aqua': No such file or directory
```

> THe other thing seem to be that /home/ella/Desktop/Aqua doesn't exist. That's really weird, what happens when you do this:

ls /home/ella/Desktop/Aqua

same result as the previous... "no such file and dictectory" and what not

](*,)

---

### Post by cowlip on 2007-03-21
OK that means that the files don't seem to have extracted there.  So what I would do is use FileRoller to open the zip file, maybe by right clicking and choosing "Extract", and extract them to your desktop.  See if a new directory appears on your desktop and note the name of it.  Double click to see if there are the skin files in that folder.

Now if you want to use the command line, try "ls ~/Desktop/<INSERT DIRECTORY NAME HERE>".  Does it come up with a directory listing?


If so, try: 
cp -rd ~/Desktop/<INSERT DIRECTORY NAME HERE> ~/.amsn/skins



For gksudo nautilus you could either use Fileroller (double click on the zip file) to extract them to the /usr/share/amsn/skins directory , or you could copy them from your Desktop there.  Try to use the file tree sidebar on the left to navigate, or the address bar (kind of like a command line) that appears when you click to the left of the directory breadcrumb bar.  You don't have to use gksudo however just to copy inside your home folder, so enable hidden files in Nautilus (look at the menu  bar:  View-> Show Hidden Files or use the keyboard shortcut CTRL + H) and copy and paste them to the desired location.


[[I'm really sorry, I hope I'm not frustrating you ;) I hope someone actually using Ubuntu right now (I'm not) can pitch in too ]]

---

### Post by deafchickadee on 2007-03-21
nah nah, thats fine, i really appreciate your help heaps!!!

Part of a learning process.. i've only used this for 24 hours and i've enjoyed it so much. I'm learning so fast.

I used to write scripts for mIRC years ago, so ubuntu in a way is similar commands and all. It's pretty simple to pick up once you've grasped the basics. I've almost customised my laptop to perfection..  all i need to do now is configure the wireless (i figure that;s the hardest part), and a couple other things, then im pretty much set to use ubuntu all the time. I've used open office for a year, so im used to it.

:)

---

### Post by cowlip on 2007-03-21
There's a really good, user friendly guide to the Linux command line here: [http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

It helped me out so much when I first started on Linux, so I hope you get some use out of it.  I hope you get the wireless sorted too, sounds like you'll probably need ndiswrapper or something but I'm sure you'll get lots of help there (...although Feisty Fawn has support of many more encryptions and wireless cards now due to a new wireless stack from Devicescape)

---

