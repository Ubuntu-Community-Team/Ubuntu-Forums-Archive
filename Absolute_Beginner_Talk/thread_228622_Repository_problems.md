---
title: "Repository problems"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Darrious on 2006-08-03
I was messing around with the file sources.list and I really don't know that much about repositories. I was trying to add another repository and I also deleted things that I didn't know what did. Now when I try to type ```
 apt-get install [FILE]
``` It says this ```
 E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
 
```
This is what the sources.list file says.
```
&#65279;
####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb http://archive.ubuntu.com/ubuntu dapper-backports main
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

# deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu dapper-backports universe
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

# deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse







```

---

### Post by risbac on 2006-08-03
There must be a weird character somewhere.
Rename your source.list into source.list.bak, create a new source.list file, then copy past each line one by one, and do an apt-get update after each modification. Maybe it will just work fine, otherwise you should be able to find the problem this way (or to be faster, do it by dichotomy, try each half, then refine by cutting into two again).

---

### Post by Darrious on 2006-08-03
Thanks. Though all I had to do was just rename the file to source.list.bak, then it worked.

---

### Post by Darrious on 2006-08-03
Now I can't install repositories. If I try the synaptic package manager then the window pops-up then closes and it asks me to click on the reload button. when I click on that it says its downloading package information then does nothing. How can I add repositories.

---

### Post by cstudent on 2006-08-03
> **Darrious said:**
> Now I can't install repositories. If I try the synaptic package manager then the window pops-up then closes and it asks me to click on the reload button. when I click on that it says its downloading package information then does nothing. How can I add repositories.

If you literally renamed the file and didn't copy the original, then you don't have a file in /etc/apt called sources.list. Rename or copy your original back to sources.list. Your original error is telling you there is a character it can't read in line one. Line one looks like a blank line to me. Try removing the blank line. I also see a problem with with this line under the Final Release Repositories section.

```

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main

```

This line creates duplicated repositories. Remove the words universe restricted and main. Then try again.

---

### Post by Darrious on 2006-08-03
> **cstudent said:**
> If you literally renamed the file and didn't copy the original, then you don't have a file in /etc/apt called sources.list. Rename or copy your original back to sources.list. Your original error is telling you there is a character it can't read in line one. Line one looks like a blank line to me. Try removing the blank line. I also see a problem with with this line under the Final Release Repositories section.

```

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main

```

This line creates duplicated repositories. Remove the words universe restricted and main. Then try again.

I tried averything said above and it's still saying ```
E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```

Could someone copy this file and put it in there /etc/apt/ directory, and try to find out what the problem is.

```
&#65279;####################################
### Official Ubuntu Repositories ###
####################################


# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse 
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb http://archive.ubuntu.com/ubuntu dapper-backports main
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

# deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu dapper-backports universe
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

# deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse
```

---

### Post by cstudent on 2006-08-03
I cut and pasted your list into a new sources.list. I don't get the error message, but the repositories don't seem to be responding at the moment. I'll try again shortly.



Worked OK for me. No error and apt-get update went fine with no errors.

---

### Post by cstudent on 2006-08-03
Maybe trying this copy will work for you. Of course, remove the .txt extension. I had to add that to upload the attachment.

---

### Post by Darrious on 2006-08-03
YES. That worked thanks. I don't see much of a difference in the files. Thanks for that. Now I have 63 new updates though. Hey, how do you select all the packages in synaptic. I have sooooooooo many packages.

---

### Post by Darrious on 2006-08-03
How would I install this. I'm very new to ubuntu.

[http://www.kiberpipa.org/~gandalf/ubuntu/README]("http://www.kiberpipa.org/~gandalf/ubuntu/README")

---

### Post by cstudent on 2006-08-03
You would start with step two based on your sources.list. You already have the extra repositories enabled.

I'll tell you how from the terminal:
Start with backing up:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak.good

```

Then you'll edit your sources list and add the needed repositories.
```

sudo gedit /etc/apt/sources.list

```

Then copy and paste the following at the end of the file.
```

## Cinelerra Repositories ##
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./

```

You may want to use one of the other repo lines in the step 3 for dapper instructions. I don't know what your processor is. If you have an amd or pentium4 use the line for your processor.

Save the file and close it.

Finally you run apt-get update.
```

sudo apt-get update

```

Then install the package
```

sudo apt-get install cinelerra

```


That should do it.

---

### Post by Darrious on 2006-08-03
That did it. I just want to say that I'm sticking with Ubuntu. I've tryed 6 different Linux operating systems. I was going to stick with Suse, but it was  much slower. I tryed the Ubuntu live cd before, but I tryed it again (after I tryed 3 others) and I really liked it. At first wasn't going to install it just because it was debian based. Then I decided I liked it cause it was fast. Now I like it because everything is much easier to install, and the support for this is GREAT!

---

### Post by cstudent on 2006-08-03
Glad I could help you. Welcome to Ubuntu!



cstudent

---

### Post by Darrious on 2006-08-03
I have all the repositories installed, but when I type ```
sudo apt-get install cinerella
``` It gives me this ```
The following packages have unmet dependencies:
  cinelerra: Depends: fftw3 but it is not installable
             Depends: libmjpegtools0c2a (>= 1:1.8.0-0.0ubuntu1) but it is not installable
             Depends: libmpeg3hv (>= 1:2.0.0) but it is not going to be installed
             Depends: libquicktimehv (>= 1:2.0.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.0.0-1svn20060611.1) but it is not going to be installed
             Depends: libmpeg3hv (= 1:2.0.0-1svn20060611.1) but it is not going to be installed
E: Broken packages

```
I tryed "apt-get install" on all of the packages listed here and they will come out with that one file Depends on another. 
I have the repositories that should install the files, but it doesn't sem to be working.Could someone else try to install cinerella and see if you can get it to work. BTw, thanks for all your help.

---

### Post by cstudent on 2006-08-03
I'm not willing to try and install the software on my box. The program is not finding the dependencies it needs to install properly. They are either not available in any repository or may be conflicting with other packages. I did find a couple of things on the web. One being what I think is the homepage for the program, although they refer to the program as cinelerra. They suggest installing the program and all dependencies from source. I also found a reference on UDSF, but it says it is for Breezy, so I don't know if the program can be installed.

[http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)

[http://doc.gwos.org/index.php/Cinerella](http://doc.gwos.org/index.php/Cinerella)

You may want to start another thread asking for help specific to Cinerella. There may be someone who uses the program that knows exactly what to do, but they may not read this thread because of the the title.


Good luck to you,
cstudent

---

### Post by Darrious on 2006-08-07
Thanks, I'll do that. The repositories did not work, but I finally fixed the prroblem, thanks to you, and learned more about repositories.

---

