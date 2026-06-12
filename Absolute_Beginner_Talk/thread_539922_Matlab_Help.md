---
title: "Matlab Help"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Remy001 on 2007-08-31
I've had ubuntu for 2 weeks and still can't get matlab working. I had problems installing but finally figured that out.
but when I go to start the license manager I get

~/MATLAB/etc$  ./lmstart
 
Checking license file for local hostname and local hostid . . .
 
Taking down any existing license manager daemons . . .
 
    No license manager daemons running . . .
 
Starting license manager . . .
 
    Debug logfile = /var/tmp/lm_TMW.log
ln: creating symbolic link `/var/tmp/lm_TMW.vd1' to `/home/remy/MATLAB/etc/glnxa64/lm_matlab': File exists
    Note: License manager still has not started properly . . .
          You may still be waiting for redundant servers to
          communicate properly. Check the end of the logfile for any
          additional messages by using the command 'lmstart -e'.

then with lmstart -e I get

363 19:01:29 (lmgrd)   for your enterprise.
364 19:01:29 (lmgrd)
365 19:01:29 (lmgrd) -----------------------------------------------
366 19:01:29 (lmgrd)
367 19:01:29 (lmgrd)
368 19:01:29 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
369 19:01:29 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
370 19:01:29 (lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.9760, errno: 2
371 19:01:29 (lmgrd) Failed to open the TCP port number in the license.
372 19:01:29 (lmgrd) Can't remove statfile /usr/tmp/.flexlm/lmgrdl.9760: errno No such file or directory


I've change permisions of lmgrd and lmstart,
I've created the directory in matlab/ etc   /usr/tmp/./flexlm  both with sudo and without
I'm not a programer and not terribly comfortable with the terminal, getting better over the last 2 weeks though.

I need Matlab for research I am doing, Biophysics, and matlab was the last reason I was using windows over linux and I would hate to have to go back but I need matlab up and running
please Help

---

### Post by verbalshadow on 2007-09-01
I have not tried this instructions as i do not have MATLAB. Google provide these:
[http://www-math.cudenver.edu/ccm/sysdocs/how_to_install_Matlab_on_linux.html](http://www-math.cudenver.edu/ccm/sysdocs/how_to_install_Matlab_on_linux.html)
[http://shum.huji.ac.il/cc/matlR13linuxhomeinst.html#prod](http://shum.huji.ac.il/cc/matlR13linuxhomeinst.html#prod)

hope they help

---

### Post by Remy001 on 2007-09-01
Thanks for the help, but nothing seems to work

I copied and pasted the license email I got I deleted and tried to reinstall Matlab 2007a I have the code for windows so I guess I'll just have to reinstall windows which I am not happy about
I may dual boot but that seems like a pain

anybody has any advice or possible solutions please let me know

---

### Post by Adramelech on 2007-09-01
Maybe running the license manager as root? i think the installation manual says so

---

### Post by Remy001 on 2007-09-02
When I've tried to run license manager with sudo I get a message that

Starting license manager . . .
 
    Debug logfile = /var/tmp/lm_TMW.log
 
    Error: You are superuser.
 
           For security reasons superuser is not allowed to start
           the license manager.
 
           Either startup the license manager as a regular user or
           stay as superuser and use the -u option and an alternative
           username. For help use the -h option.
 
    Note: License manager still has not started properly . . .
          You may still be waiting for redundant servers to
          communicate properly. Check the end of the logfile for any
          additional messages by using the command 'lmstart -e'.


I've learned alot about linux the last 2 weeks and suspect some of my 'fixes' probably made things worse so I'm going to try and reinstall fresh ubuntu, (probably from all my years with windows I'm used to having to reinstall)
Thanks to everyone who has been trying to help

---

### Post by goorq on 2008-02-23
Hi,
 I have the same problem you describe here. Do you finally succed to solve the problem ?

---

### Post by firestormx37 on 2008-02-23
I had this problem some time ago and managed to solve it.  I don't remember exactly what I did though, so I will have to look around and see if I can figure out what I did.  I believe that the answer is somewhere on the forums, if you want to try looking too.

---

### Post by firestormx37 on 2008-02-23
Ok, the one thing that I remember being a problem is that the license file was missing some important lines.  I think I was able to reinstall and regenerate the license and then it worked.  But check your license.dat file which should be in the where_installed/matlab/etc directory.  Check that the file has two lines like the following near the top of the file:

SERVER <pc_name> ANY 27000   <--this just needs a name to refer to your computer
DAEMON MLM /usr/local/matlab/etc/lm_matlab     <--this directory should match where matlab is installed

I also seem to recall a problem getting Matlab to run that was related to java.  If you are trying to run matlab but just get a white screen, take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=357870](http://ubuntuforums.org/showthread.php?t=357870)

Hope this helps.

---

