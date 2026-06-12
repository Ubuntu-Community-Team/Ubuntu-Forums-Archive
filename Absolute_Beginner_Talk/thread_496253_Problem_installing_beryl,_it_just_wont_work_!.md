---
title: "Problem installing beryl, it just wont work !"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Leo11 on 2007-07-08
I'm using the guide from [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA) 
and I got to the place where it says
 
For the installation of the nVidia drivers to continue, X.org must be shut down. Note that after executing the following command, it is not possible to return to a graphical interface until X.org is restarted.

One way to shutdown the X.org server is by stopping GDM. To do so, execute

sudo /etc/init.d/gdm stop

Now, actually running the installer is possible. Run

sudo sh ./<nvidia_installation_pkg_filename>

so i shut it down and replaced "nvidia_installation_pkg_filename"   with NVIDIA-Linux-x86-1.0-9755-pkg1.run

But when I enter sudo sh ./<NVIDIA-Linux-x86-1.0-9755-pkg1.run>   into it all I get is the error message
-bash: syntax error near unexpected token 'newline'


Can someone please explain why it won't work??
Thanx

---

### Post by tgm4883 on 2007-07-09
Do you really need that driver or would the restricted one from the repos work?

Also, dont install beryl, its discontinued.  Install compiz fusion.

---

