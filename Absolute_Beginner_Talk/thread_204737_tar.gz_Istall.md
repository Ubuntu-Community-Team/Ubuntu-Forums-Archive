---
title: "tar.gz Istall"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-27
real n00b to this...

i have downloaded a program and all i ahve is a tar.gz file.. how do i install that ...

i am used to the windowz .exe.. lol

any help grateful...

---

### Post by Mike_N on 2006-06-27
TAR is like ZIP, it's an archive... the ".gz" at the end shows that it's compressed... i think.

So... when you get one of these, like a ZIP, you have to extract it to the right destination...

Hope that helps, Mike

---

### Post by bukwirm on 2006-06-27
To uncompress, right click on the file, select 'extract here'; or in the command line enter 'tar -xvzf *filename*'.

Since it is a tar.gz file, you probably have source code which you need to compile. Make sure you have the nessacary libraries and packages (look at the readme file), then type (in the command line) './configure', 'make', then 'make install' (probably, but read the readme first).

---

### Post by aysiu on 2006-06-27
Read this before you install any .tar.gz files:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by shoot2kill on 2006-06-27
[QUOTE=Mike_N]TAR is like ZIP, it's an archive... the ".gz" at the end shows that it's compressed... i think.

So... when you get one of these, like a ZIP, you have to extract it to the right destination...

Hope that helps, Mike[/QUOTE]

YEAH THATS WHAT I THOUGHT, BUT INSIDE ARE LOTS OF DIFFERENT FILES AND FOLDERS, AND I THINK EACH INDIVIDUAL FILE NEEDS TO BE PUT IN THE FOLDER THAT IS ALREADY ON MY BOX.. THERE ARE LOADS OF FILES AND I DNT WANT TO DO THEM ALL INDIVIDUALLY... 

SCREENSHOT POSTED (NOTE: THE SIZE OF SCROLL, SHOWS HOW MANY FILES THERE IS)

---

### Post by Bloch on 2006-06-27
This is a great guide to installing software on ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

First you should check with synaptic to see what software you need. Software installed with synaptic works 99% of the time straight off, and will be updated automatically.

If the software in your .tar.gz file is not in synaptic, double click on it and unpack it. There should be a readme file. If it mentions ./configure and ./make commands then you are dealing with source code. Ubuntu does not come with the libraries needed for compiling. They have to be downloaded (using synpatic). 

This would be a good time to stop and ask yourself if you want to go down that road. It may take a lot of time and might not work - compiling software is not expected of linux users any longer, not since about 1996 :-)

On the other hand the .tar.gz file might unpack and contain an executable in it. Double click on it and choose either run or run in terminal - whichever works.

---

### Post by aysiu on 2006-06-27
It appears you're trying to install Cedega. If that's the case, this may help:
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)

---

### Post by shoot2kill on 2006-06-27
now im more confused...

when i extract the tar.gz, im left with 3 folders.. usr, etc, and opt..

the read me says

```
2. In a root shell change directory to where you extracted the files.
3. cp etc/* /etc/
4. cp opt/* /opt/
5. cp usr/* /usr/
```

but this does not seem to do anything... there is no .configure, or .make...

HELP please

---

### Post by shoot2kill on 2006-06-27
[QUOTE=aysiu]It appears you're trying to install Cedega. If that's the case, this may help:
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=22&Itemid=63)[/QUOTE]

that site gives instructions for installing a .deb

not a .tar.gz

?????????

---

### Post by xtacocorex on 2006-06-27
Say you extracted the archive to your desktop.

Open up a terminal and do the following:
```

cd /home/<username>/Desktop/<extracted folder>

OR

cd /home/<username>/path/to/extracted/archive/

sudo cp etc/* /etc/
sudo cp opt/* /opt/
sudo cp usr/* /usr/

```
Be sure to include your user name in place of <username> and the folder name in place of <foldername>. Also, Desktop is capitalized, so keep watch for case sensitivity.

That should copy all to where it needs to go.

---

### Post by shoot2kill on 2006-06-27
[QUOTE=xtacocorex]Say you extracted the archive to your desktop.

Open up a terminal and do the following:
```

cd /home/<username>/Desktop/<extracted folder>

OR

cd /home/<username>/path/to/extracted/archive/

sudo cp etc/* /etc/
sudo cp opt/* /opt/
sudo cp usr/* /usr/

```
Be sure to include your user name in place of <username> and the folder name in place of <foldername>. Also, Desktop is capitalized, so keep watch for case sensitivity.

That should copy all to where it needs to go.[/QUOTE]

eerrrmmmm.... not sure if it worked, how can i tell

```
gav@gav-linux:~$ cd /home/gav/Desktop/test
gav@gav-linux:~/Desktop/test$ sudo cp etc/* /etc/
cp: omitting directory `etc/X11'
gav@gav-linux:~/Desktop/test$ sudo cp opt/* /opt/
cp: omitting directory `opt/kde3'
gav@gav-linux:~/Desktop/test$ sudo cp usr/* /usr/
cp: omitting directory `usr/bin'
cp: omitting directory `usr/lib'
cp: omitting directory `usr/share'
gav@gav-linux:~/Desktop/test$

```

---

### Post by xtacocorex on 2006-06-27
As a simple test in a terminal, go to:
```
cd /usr/lib/transgaming_cedega
```
and see what is listed. 

From your screenshot, it should be at least a couple directories like the following (there may be more, but this is what I've gathered from the screenie):
agp_test
bin
ClientCookie
default_cofiguration_profiles

If those exist, then you should be alright.

---

### Post by shoot2kill on 2006-06-27
[QUOTE=xtacocorex]As a simple test in a terminal, go to:
```
cd /usr/lib/transgaming_cedega
```
and see what is listed. 

From your screenshot, it should be at least a couple directories like the following (there may be more, but this is what I've gathered from the screenie):
agp_test
bin
ClientCookie
default_cofiguration_profiles

If those exist, then you should be alright.[/QUOTE]


nope.. :( :( :(
```
gav@gav-linux:~/Desktop/test$ cd /usr/lib/transgaming_cedega
bash: cd: /usr/lib/transgaming_cedega: No such file or directory
gav@gav-linux:~/Desktop/test$

```

---

### Post by xtacocorex on 2006-06-27
Hmm, that should have worked.

Can you attach the README?

---

### Post by shoot2kill on 2006-06-27
[QUOTE=xtacocorex]Hmm, that should have worked.

Can you attach the README?[/QUOTE]

it called INSTALL , not README

---

### Post by Arisna on 2006-06-27
[QUOTE=shoot2kill]
```
gav@gav-linux:~$ cd /home/gav/Desktop/test
gav@gav-linux:~/Desktop/test$ sudo cp etc/* /etc/
cp: omitting directory `etc/X11'
gav@gav-linux:~/Desktop/test$ sudo cp opt/* /opt/
cp: omitting directory `opt/kde3'
gav@gav-linux:~/Desktop/test$ sudo cp usr/* /usr/
cp: omitting directory `usr/bin'
cp: omitting directory `usr/lib'
cp: omitting directory `usr/share'
gav@gav-linux:~/Desktop/test$

```[/QUOTE]

Directories aren't being copied over.  I believe you need to use "cp -r" rather than "cp".

---

### Post by xtacocorex on 2006-06-27
I still think that should have worked, but it didn't. 

```

cd /home/gav/Desktop/test
sudo cp ./etc/* /etc/
sudo cp ./opt/* /opt/
sudo cp ./usr/* /usr/

```

By adding the ./, it will tell the cp command to use the stuff in the current directory. I'm not sure if it didn't work because sudo wasn't letting cp find what it needed to copy.

If this doesn't work, then I don't know what is going wrong.

---

### Post by shoot2kill on 2006-06-27
[QUOTE=Arisna]Directories aren't being copied over.  I believe you need to use "cp -r" rather than "cp".[/QUOTE]

:) :) :) :) :) :) :) :) 

that worked.. thankyou very much...

however, i still not sure how to open the app...

????????? it is not in prog list

---

### Post by xtacocorex on 2006-06-27
Totally didn't think of the -r flag. Sucks having to work on a Windows machine at work and not being able to test stuff out before I answer.

You should just be able to type cedega at the command prompt to open it up.

The rest of INSTALL.txt should be able to walk you through the rest of the setup.

---

### Post by vidak on 2006-06-27
[QUOTE=shoot2kill]real n00b to this...

i have downloaded a program and all i ahve is a tar.gz file.. how do i install that ...

i am used to the windowz .exe.. lol

any help grateful...[/QUOTE]

the tar.gz file is a packaged file, usually called tarball. This can be handled eg. from console using
tar -xzf foo.tar.gz

where tar is the program you will run, x, z, f stand for eXtract gZipped File, and foo.tar.gz is the file you downloaded.
This will possibly create a directory with the program's source. Go into it, then read the README and INSTALL files.
Now you have to configure and compile the program. Say
./configure
then
make
these steps may take a while. Check out the result of configure, there may be some errors (missing depencies, which mean you have to install some packages needed by this program)
then use
sudo checkinstall
to install the program.

But check the reposiories if this program can be installed without compiling. What is the program you want to install?

Tell me if you need more help.

---

### Post by shoot2kill on 2006-06-27
[QUOTE=xtacocorex]Totally didn't think of the -r flag. Sucks having to work on a Windows machine at work and not being able to test stuff out before I answer.

You should just be able to type cedega at the command prompt to open it up.

The rest of INSTALL.txt should be able to walk you through the rest of the setup.[/QUOTE]

thankyou very much for your help. works great...

:):):)

---

### Post by xtacocorex on 2006-06-27
Glad to help.

---

### Post by njzillest on 2006-06-27
to install .deb dpkg -i then the location


it should look like this 

dpkg -i /home/user/Desktop

---

