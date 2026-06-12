---
title: "How To: Exit  X-Server"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-11-30
Hi im installing my NVIDIA graphics driver which requires me to exit the x server for the installation process. Could anyone tell me how to do this and in turn how to get back x-server  after the installation?????

---

### Post by an.echte.trilingue on 2006-11-30
If you hit CTRL+ALT+F1 you will be in a virtual terminal.  You can get back to your X environment with CTRL+ALT+F7.  Note that this procedure does not leaves X running, and so when you get back to your X environment after installing your driver you will have to restart it with CTRL+ALT+BACKSPACE.

However, your question makes me want to ask, what howto are you following to install the NVidia driver?  "Exiting the Xserver" does not sound like the Ubuntu way of installing the NVidia driver...

---

### Post by Bachstelze on 2006-11-30
He is linstalling from the package provided by nvidia, which works just as well.

@nite owl : do Crtl+Alt+F1 to switch to a virtual console, log in, terminate the Xserver because it is *still* running :

```
sudo /etc/init.d/gdm stop
```

then start the installer

```
sudo sh /path/to/package.run
```

when the install is complete, you can either

```
sudo reboot
```

or restart your xserver

```
sudo gdm
```

---

### Post by nite owl on 2006-11-30
planning on exiting x-server then runnin 'sh NVIDIA etc...' then starting x again and editing my config file. That ok?? or am i horribly wrong??lol

---

### Post by Bachstelze on 2006-11-30
That's ok, and no need to modify your xorg.conf, the installer will do it for you if you want.

---

### Post by maxcarson on 2008-06-17
i tried ctrl+alt+ f1, my screen went black and jettery. ctrl+alt+f7 im
back to where i started? i am having the same problem with the nvidia driver. when i boot i get the "black screen of death". ctrl+alt+f7 allows
me to get the welcome screen. i am a newbie. two days old.

---

### Post by b_ron on 2008-06-27
Thanks HymnToLife.  I had the same problem as nite owl.  The other suggestions did not work but yours did.  Thanks, again.

---

### Post by parakeets11 on 2008-07-01
I am also trying to install a NVidia Graphics Driver. But when i Crtl-Alt-f1 and enter the codes and start the installer, it says that I need a 1bic or lbic header to compile the kernel. What is this and where can i get it?

---

### Post by glorkinfall on 2008-07-04
I follow HymnToLife's instructions, and after typing 'sudo sh /path/to/package.run' I get a 'Can't open /path/to/package.run' message...](*,)

(I hope this isn't a hijack...)

---

### Post by Galveru on 2008-07-15
path/to/package.run is an example.  What he meant was the directory and filename of the .run file.
So another example could be
ubuntu@Ubuntu~$:cd Desktop
ubuntu@Ubuntu~/Desktop$:sh NVIDIA-Linux-x86-71.86.04-pkg1.run

I do believe they need to be run by a root user, so try
sudo sh NVIDIA-Driver-Name-Here.run (when in the same directory as the package)
Or directly from your home/default directory:
sudo sh /path/to/NVIDIA-Driver-Here.run
You will then be prompted for your password.

I get an error that I do not have libc header files installed, are there any people who can spoon feed me links that would help me install those?

---

