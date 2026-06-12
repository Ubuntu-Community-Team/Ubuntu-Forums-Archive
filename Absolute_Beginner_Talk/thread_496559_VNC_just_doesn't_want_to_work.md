---
title: "VNC just doesn't want to work"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-07-09
Hi there,

I can't VNC to my Kubuntu box from Windows. Windows just can't connect. SSH works fine. And the Kubuntu Box can't vnc to a Windows box.

All I want is to be able to VNC to the Kubuntu box as it is a file server and has no screen.

The windows box produces an error saying that the VNC server could not connect.

On what port does vnc run on by default?

I have followed some how to's but it seems that they have only made things worse.

Thanks for any help,

Rudolf

---

### Post by Waappu on 2007-07-09
Hi

In Ubuntu I have noticed I must set password for VNC server before I can connet from Windows machine.
And some user must be loggend in before VNC works

---

### Post by information_entropy on 2007-07-09
If you just want to use a box as a file sever, you might want to investigate sshfs.

A very good how to can be found here:

[http://ubuntuforums.org/showthread.php?t=275856&highlight=howto+sshfs]("http://ubuntuforums.org/showthread.php?t=275856&highlight=howto+sshfs")

---

### Post by bernied on 2007-07-09
Have you started a vnc server on the server box? How have you done this? There are many ways to set this up, using inetd and such, but the easiest is to just run vncserver in a terminal (through ssh for example) - when you do this, it should give you some indication that it has started.

As far as I remember, vnc defaults to port 5901 upwards, though 5900 is sometimes used. You can change this in the command line when you start vncserver, or through a config file.

Generally you will need a functioning X-server on the headless box (not strictly true, but it seems to be the easiest way), this is not so easy to achieve when you don't have a monitor on it. Are you sure you have a functioning desktop environment on the box?

You can do something like 'ps -ef | grep vnc' on the server box to see that the vnc server is running

netstat might be a useful command to run on the server to see what's open ('man netstat' for details on options)

nmap is a good tool for looking for open ports on other machines (though I don't know if there's an nmap for windows) - you would need to install this

A strict firewall on a windows (or any) machine will prevent outbound traffic - are you sure the message is getting out of the windows box?

If you want to vnc from kubuntu to windows, you need to run a vnc server on the windows box. Again watch out for firewalls.

I hope some of this helps.

---

