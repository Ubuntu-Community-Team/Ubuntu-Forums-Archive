---
title: "Installing Real VNC HELP!"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by thallium205 on 2007-04-23
Hi, I am really new at using Ubuntu and Linux in general and I am having a lot of problems trying to instal RealVNC on my machine.  I use this command "sudo apt-get install" , then I dragged the installer file and added "/usr/local/bin" after it like the directions said and it says something along the lines that it could not write to the root file or something.  Sorry I cannot be more specific I am not near that machine right now.  I want to install RealVNC so I can figure out how to work this system while I am at work! 
Anyone who has installed RealVNC on their machine, can you PLEASE tell me the command you used?

Thanks!!

---

### Post by chalex on 2007-04-23
Why do you want RealVNC in particular?  Will any other VNC server do?

Are you talking about running a VNC server so that you can connect from other machines? Or vice versa?

"sudo apt-get install vncserver" or "sudo apt-get install vino" will install a vnc server so that you can connect from other machines.

There's a whole bunch of different VNC servers and clients included in the repository.  "apt-cache search vnc" will show you.  Or Search for "vnc" in Synaptic.

---

### Post by crav on 2007-04-24
Are all the different version cross-compatible? Meaing, if I install one of these, can I connect to RealVNC or vice versa?

---

### Post by Transrational on 2007-04-27
I'm having similar problems with Feisty and x11VNC. Downloading and installing seemed to work, but after that it's nowhere to be found. The executable's in /usr/bin, but I can't find a way to start and configure it. I've used Chicken of the VNC under OSX, so I'm familiar with what it should look like, but I can't find it. Or start it. (I need to be able to control the machine remotely, not have it control other machines.)

Any advice welcome.

---

