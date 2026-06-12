---
title: "trying to play chess in 3d but i get error, is as follows"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-12
our system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.

You are still able to play chess in 2D without these packages.

i have my Nvidia graphics drivers,, why wont it play, and,, just so anyone who reads this knows, i have just installed OpenGL python

i just can't find the other one.

os= ubuntu 7.04

---

### Post by wolfen69 on 2007-08-12
here are the deb packages. enjoy. [http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)

---

### Post by jake16424 on 2007-08-12
> **wolfen69 said:**
> here are the deb packages. enjoy. [http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)

thankyou :) ill try to install them,, if i have a problem, ill give a repost,, :D..

---

### Post by ridgeland on 2007-08-12
I got it to work.
I used
[http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)
to get python-gtkglext
and got OpenGL Python bindings from synaptics searching for OpenGL Python.

---

### Post by jake16424 on 2007-08-12
> **ridgeland said:**
> I got it to work.
I used
[http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)
to get python-gtkglext
and got OpenGL Python bindings from synaptics searching for OpenGL Python.

i keep trying to download it, i dont have super DSL but i click it, sends me to another window, and it says its done.. i try to unpack it, and it says error,, incomplete file.. O_o

---

### Post by ridgeland on 2007-08-13
I just tried to follow the steps on a second PC.
First verified that 3D got the same error message - it did.
Sourceforge is down so I used sneaker-net and copied it from one PC to the other. (didn't bother getting NFS setup for there).
The file is only 43 KB so even without DSL it could download to fast to see.  I always download to /Data/Downloads/Software/somewhere then use nautilus as root (set it up in my panel).  Then in nautilus-root I copy the download folder and paste it into /opt.  Then still in nautilus-root I open the folder, double click the deb and say [Install Package].  Oh yeah, the file I chose was the last one, it had feisty in the name. 
Then I went Synaptics and click to apply "python-opengl".  
Then checked Chess -> 3D - error message is gone, 3D board appears.
You did install as root?
To get nautilus as root from the terminal just $ sudo nautilus.

---

### Post by jake16424 on 2007-08-13
> **ridgeland said:**
> I just tried to follow the steps on a second PC.
First verified that 3D got the same error message - it did.
Sourceforge is down so I used sneaker-net and copied it from one PC to the other. (didn't bother getting NFS setup for there).
The file is only 43 KB so even without DSL it could download to fast to see.  I always download to /Data/Downloads/Software/somewhere then use nautilus as root (set it up in my panel).  Then in nautilus-root I copy the download folder and paste it into /opt.  Then still in nautilus-root I open the folder, double click the deb and say [Install Package].  Oh yeah, the file I chose was the last one, it had feisty in the name. 
Then I went Synaptics and click to apply "python-opengl".  
Then checked Chess -> 3D - error message is gone, 3D board appears.
You did install as root?
To get nautilus as root from the terminal just $ sudo nautilus.

no, but i tried both of the links given above and both did the same thing,, =(... ill try again this morning. 

PS: no clue what the file system is,, id rather not go poking around untill i have a better understanding ><

---

### Post by jake16424 on 2007-08-13
well i downloaded the packet, same thign happened, i used the first link, downloaded it. system error, package broken, needs to be fixed\replaced before it can continue, so i entered teh command given to download teh package again, then it finished, i tried to play chess and ended up with the same error messgae O_o

---

### Post by Hobo Joe on 2007-08-13
As far as i know there is no way to get it working.  But you could always download Brutal chess.

```

sudo aptitude install brutalchess

```

---

### Post by jake16424 on 2007-08-13
3d chess?

---

### Post by jake16424 on 2007-08-13
installed went smoothly untill i launched it,, then it went bezerko and froze O_O

---

### Post by Ek0nomik on 2007-08-13
Weird, I just got this working myself last night.  :)

**brutalchess** didn't work for me, it ended up freezing.

For the GNU Chess though, you follow this:

```
sudo apt-get install python2.4 python-imaging python2.4-opengl libgtkglext1

wget -c http://prdownloads.sourceforge.net/glchess/python-gtkglext1_1.1.0-2feisty_i386.deb

sudo dpkg -i python-gtkglext1_1.1.0-2feisty_i386.deb 
```

---

### Post by jake16424 on 2007-08-13
it installed, no problems, except for the fact now i cant find the game o.o

---

### Post by Ek0nomik on 2007-08-13
> **jake16424 said:**
> it installed, no problems, except for the fact now i cant find the game o.o

What did you install?

---

### Post by jake16424 on 2007-08-13
i don't know,, i used all of the commands that you gave me, and hit y then enter when needed,,, O_O

---

### Post by wolfen69 on 2007-08-13
try typing in terminal: glchess

---

### Post by Ek0nomik on 2007-08-13
> **jake16424 said:**
> i don't know,, i used all of the commands that you gave me, and hit y then enter when needed,,, O_O

The commands I gave you were to get the default Chess working that came with Ubuntu.  This is what allows you to have 3D Chess when you try to check that option.

---

### Post by jake16424 on 2007-08-13
> **Ek0nomik said:**
> The commands I gave you were to get the default Chess working that came with Ubuntu.  This is what allows you to have 3D Chess when you try to check that option.

is there an easy button for this? cause its still refusing to let me actiave the 3d.. ](*,)

---

### Post by Ek0nomik on 2007-08-13
> **jake16424 said:**
> is there an easy button for this? cause its still refusing to let me actiave the 3d.. ](*,)

```
sudo apt-get install python-opengl libgtkglext1
```

If it doesn't work after running that (make sure to close the game and reopen it), then I can only be led to believe you're video card drivers aren't supporting 3D...

---

### Post by jake16424 on 2007-08-13
well i have my drivers right from the Nvidia webpage, where i always go to upgrade them,, so there up to date,and are working, i can play the 3d screen saver, with all graphic settings on max in my settings menue, NO LAGG. and it looks amazing,, soo.. idk 

is this what i should have seen?

jake@jake-desktop:~$ sudo apt-get install python-opengl libgtkglext1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-opengl is already the newest version.
libgtkglext1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jake@jake-desktop:~$ 

it didnt work

---

### Post by Ek0nomik on 2007-08-13
> **jake16424 said:**
> well i have my drivers right from the Nvidia webpage, where i always go to upgrade them,, so there up to date,and are working, i can play the 3d screen saver, with all graphic settings on max in my settings menue, NO LAGG. and it looks amazing,, soo.. idk 

is this what i should have seen?

jake@jake-desktop:~$ sudo apt-get install python-opengl libgtkglext1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-opengl is already the newest version.
libgtkglext1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jake@jake-desktop:~$ 

it didnt work

Well now I guess I just don't know, because I just listed everything I did to get mine working, and I just did this last night.

Here are some links on the matter:

[http://ubuntuforums.org/showthread.php?t=410371](http://ubuntuforums.org/showthread.php?t=410371)
[http://ubuntuforums.org/showthread.php?p=3137685](http://ubuntuforums.org/showthread.php?p=3137685)
[http://my.opera.com/ninhthuan82/blog/playing-3d-chess-in-ubuntu-7-04-feisty](http://my.opera.com/ninhthuan82/blog/playing-3d-chess-in-ubuntu-7-04-feisty)

---

### Post by ridgeland on 2007-08-13
huh? Looks like you've got the two packages you need.
Chasing thinner leads now...
Maybe check /etc/X11/xorg.conf and verify that driver is Nvidia and not nv.

---

