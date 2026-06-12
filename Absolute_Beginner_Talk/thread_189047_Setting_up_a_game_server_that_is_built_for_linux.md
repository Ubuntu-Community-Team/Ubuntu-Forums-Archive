---
title: "Setting up a game server that is built for linux"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by joe_elscorpion on 2006-06-04
> 1.Restore the goserver package by using command "gunzip goserver.tar.gz", 

  then "tar xvf goserver.tar". It will automatically create a goserver 

  directory with all of the files in it. 

  Under the goserver directory, there are 5 sub-directories: bin,lib,globalops,

  monitor and installation.

2.Under bin/linux_release/, you will find the server executable(goserver.elf) 

  and server profile(server.prf). 

3.Under lib/linux_release/, there are three dynamic libraries we used. 

4.Under globalops/ you will find all of the resource files necessary for 

  running goserver.elf. 

5.Under installation/, there is documentation guide for installation.

6.Under monitor/, there are the remote monitors running on both linux & windows

  platform. And under the windows, there are 2 sub-directories:console and mfcapp, 

  in either of which, the console-version and MFC-based version is inclusive.

7.Move the executable file(goserver.elf) and server profile file(server.prf) 

  from bin/linux_release/*.* to the goserver directory (with goserver as your 

  current directory, type "mv bin/linux_release/*.* .").

8.Move the dynamic libraries (*.so under the lib/linux_release/) to the system

  path /usr/local/lib/(with goserver as your current directory, 

  type "mv lib/linux_release/*.so /usr/local/lib"). And then check the 

  .bashrc shell file in your default home directory, 

  if there is already an assignment path defined like 

  "export LD_LIBRARY_PATH=/usr/local/lib",it is OK. If no such defined path, 

  add "export LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib" in your .bashrc 

  file.(If you do not know your default home directory, type cd ~, you should

  be switched to your home directory.)

9.If you want to bind the LINUX server to a specific IP, add a line in the 

  server.prf with "-bindip=a.b.c.d" or directly bind the IP as an argument, 

  see below if not defining the bind IP in the server.prf file.

10.If you want to assign the different port number for the IPC with monitor, 

  add a line in the server.prf with "-monport=port_number" or directly assign 

  the monitor port as an argument, see below if not defining the monPort 

  in the server.prf file.

Im stuck on step 8 of this, I moved the .so files, but the next part, > And then check the 

  .bashrc shell file in your default home directory, 

  if there is already an assignment path defined like 

  "export LD_LIBRARY_PATH=/usr/local/lib",it is OK. If no such defined path, 

  add "export LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib" in your .bashrc 

  file.(If you do not know your default home directory, type cd ~, you should

  be switched to your home directory.) 
im having trouble understanding, could someone please clarify.
Thanks,
Joe

---

### Post by harishg on 2006-06-04
[QUOTE=joe_elscorpion]Im stuck on step 8 of this, I moved the .so files, but the next part,  
im having trouble understanding, could someone please clarify.
Thanks,
Joe[/QUOTE]


In a terminal type the give command and it would work. export adds the command to the .bashrc file.It is better to do it this way than opening the .bashrc file.

---

