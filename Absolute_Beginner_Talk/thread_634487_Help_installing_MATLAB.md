---
title: "Help installing MATLAB"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Eezyville on 2007-12-07
I've looked around for days and I cannot figure out how to install matlab in my linux laptop. Please tell me what I need to install to get it to work. Here's my specs:

HP dv9000z, Ubuntu Feisty Fawn
AMD Turion64 2.2 GHz
2 Gigs of ram
Nvidia GeForce Go 7600

I tried to install MATLAB R2007a from the DVD but I didn't have permissions so I copied everything to my home folder and changed permissions. I typed in: 

[PHP]sudo ./install_unix.sh[/PHP]

but I got,

[PHP] An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /home/chris/matlab/unix/update/install/main.sh: 168: /home/chris/matlab/unix/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .
[/PHP]

So then I typed in 

[PHP]./install_unix.sh -t[/PHP]

and a few lines later I got

[PHP]/home/chris/matlab/unix/update/install/main.sh: 582: /home/chris/matlab/unix/update/bin/glnx86/xsetup: Permission denied
[/PHP]

I've read online that I need to install X-window so i did through Synaptic Package Manager but still got the same errors. Plz help. :cry:

---

### Post by taurus on 2007-12-07
Try changing the permissions first before running the installer again.

```
chmod -R 755 /home/chris/matlab
```

---

### Post by spiderbatdad on 2007-12-07
this might be a case where being root would be beneficial during the install. That is, creating a root account and becoming SU then install. I'm wondering, too, if you have install instructions for this program? Do you need to autogen or some other step missing?

---

### Post by Eezyville on 2007-12-07
I have changed the permissions of the directory where matlab is before I posted the problem so that cannot be the issue. The instructions that came from mathworks is not helpful at all. I'll try to install as root. Thanks for the responses.

---

### Post by Eezyville on 2007-12-07
I got the same error in root. Am I missing something?

---

### Post by spiderbatdad on 2007-12-07
I'm not familiar with the type of install you are trying, sorry. I did notice you must have glibc-2.3.6 or later. Have you installed this dependency?

---

### Post by Whiffle on 2007-12-07
try doing

sudo sh install_unix.sh

directly off the cd...

---

### Post by spiderbatdad on 2007-12-07
found important instructions here:
[http://www.mathworks.com/access/helpdesk/help/base/install/install.html](http://www.mathworks.com/access/helpdesk/help/base/install/install.html)



If you are installing from a DVD, execute the following command to run the MathWorks Installer.

/dvd/install &

If you are installing from downloaded files, extract the installer in the $TEMP directory. For example, on Linux systems run the following command.

tar -xf boot.ftp 

Once you have expanded all the installer files in the $TEMP directory, execute the appropriate command to run the MathWorks installer on your platform.

./install

The installer displays the following welcome dialog box.

and so on....

---

### Post by Eezyville on 2007-12-07
> **Whiffle said:**
> try doing

sudo sh install_unix.sh

directly off the cd...

I tried it directly from the dvd and got the same error. I even switched over to root and it gave me the,
[PHP]-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/unix/update/install/main.sh: 168: /media/cdrom0/unix/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .
[/PHP]
error as root.

> **spiderbatdad said:**
> found important instructions here:
[http://www.mathworks.com/access/helpdesk/help/base/install/install.html](http://www.mathworks.com/access/helpdesk/help/base/install/install.html)



If you are installing from a DVD, execute the following command to run the MathWorks Installer.

/dvd/install &

If you are installing from downloaded files, extract the installer in the $TEMP directory. For example, on Linux systems run the following command.

tar -xf boot.ftp 

Once you have expanded all the installer files in the $TEMP directory, execute the appropriate command to run the MathWorks installer on your platform.

./install

The installer displays the following welcome dialog box.

and so on....
Those are the same instructions that came with the student version and they don't address this issue. I'll look more at the site and try to contact mathworks.

Thanks for the help.

EDIT: I've requested help from mathworks and I'm waiting on a reply.

---

### Post by ai2068 on 2008-01-03
I have exactly the same problem:(.  If you find a solution, could you post it here?

---

### Post by sunheng on 2008-01-13
I got the same problem. It came from X library. I am working on Fedora 8. Somehow starting from Fedora 7, libXp is not shipped anymore (probably replaced by libXpm). But Matlab is looking for it. To fix, download rpm libXp at 
[http://rpmfind.net//linux/RPM/fedora/devel/i386/libXp-1.0.0-8.i386.html](http://rpmfind.net//linux/RPM/fedora/devel/i386/libXp-1.0.0-8.i386.html)
The installation will proceed (At least in my case)

I guess this is also the issue for other recent Linux installation. You can always  try
locate libXp.so
which is what matlab installation is looking for. If you could not find one, it is very likely that is the issue. Package libXp will solve it.

Heng

---

### Post by Victormd on 2008-01-13
Just a thought, not installation related, have any of you tried Octave? It's an open-source alternative to Matlab with the same functions and built-in instructions. I've used both and must say that it is just as powerfull! BTW, it's in the repositories...

---

### Post by dopira on 2008-01-18
I was having the same problems as you and I managed to fix it.

I believe the problem is permissions, as someone had previously mentioned.

Try copying the dvd into your home directory. Then:

cd YOUR_MATLAB_DIR/update/bin/glnx86
sudo chmod 777 *   
cd YOUR_MATLAB_DIR
sudo sh install

Make sure you have the license file in the directory you install to. It has to be named license.dat 

Also, some people reported that running "sudo xhost +" is helpful before you install. 

If you are still having problems, I also recommend Octave. Be sure to check out octave-forge for additional packages.

---

### Post by NS2-10 on 2008-04-07
I read the following on MathWorks webpage:

> On Linux systems, DVD drives typically mount automatically; however, the drives mount with read-only permission. You might have to change the DVD drive configuration from read-only to execute—see Problems with Your DVD Drive

> mount -t iso9660 /dev/dvd /dvd

However this returns:

> 
mount: mount point /dvd does not exist

Huh? What should I do?

---

### Post by Whiffle on 2008-04-07
In order for it to mount something, it has to have somewhere to mount it.  Its telling you that /dvd doesn't exist.  You might be looking for /mnt/dvd though.

---

### Post by NS2-10 on 2008-04-07
Didn't work either...

> mount: mount point /mnt/dvd does not exist

The regular mount command yields no success either, ie:
> 
mount /media/cdrom0/

---

### Post by Whiffle on 2008-04-07
Try doing

sudo mkdir /mnt/dvd


first

---

### Post by twistadias on 2008-04-09
Hi 
I have installed matlab r2008a but it wont start up
The manual at [http://www.mathworks.com/access/helpdesk/help/base/install/install.html](http://www.mathworks.com/access/helpdesk/help/base/install/install.html) says that I have to start the license manager with this code 

```
su username -c "lmgrd -c license_file -l /var/tmp/LM_TMW.log"
```

I replaced username with my account name but I get an error

```
bash: lmgrd: command not found
```

How can I fix this??

I tried starting the license manager at boot. the maunal wants me to edit some files in matlabroot/etc
but there isn't an etc folder

---

### Post by twistadias on 2008-04-10
It seems that I have to install matlab in /usr/local/matlabR2008a for it to work properly

But the installer isn't  letting me create a directory as im not logged in as a superuser?? How do I do this??

---

### Post by twistadias on 2008-04-11
bump...

---

### Post by perlluver on 2008-04-11
You have to type in sudo, to become a superuser.  So it would be sudo mkdir /usr/lib/matlab2008 or whatever it may be.

---

### Post by twistadias on 2008-04-11
thank you so much

---

