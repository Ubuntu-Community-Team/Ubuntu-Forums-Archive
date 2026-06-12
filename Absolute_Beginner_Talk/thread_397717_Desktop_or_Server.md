---
title: "Desktop or Server?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-03-31
I am putting Ubuntu on a 1TB File Server that I have and I am wondering if I should run the desktop or server version.  I have used the desktop ver some in the past, though I don't remember much about the commands and such.

I run this box as a headless server, and I used to use RDP to connect to it when it was running XP.  Now I am thinking that I might just use Webmin to admin the box and run the Server version only.

What are the advantages of doing it with Webmin on the Server version, rather than running the Desktop version and using VNC or something?

---

### Post by nixclusive on 2007-03-31
Running the desktop version will simply mean running more un-necassory code. You can try doing it with webmin and if you feel like you can install the ubuntu-desktop metapackage.

---

### Post by Bachstelze on 2007-03-31
Webmin is considered insecure and is not supported in Ubuntu. Please don't use it and use SSH instead.

---

### Post by houstonbofh on 2007-03-31
The "Server" version is Ubuntu with no GUI.  I like a GUI on my servers, as I use X remotely.  Some don't.  That is your call.  However, the actual "Ubuntu Server" CD also has a simple LAMP install.  If you think you may need that, install the Server CD with LAMP, and from the CLI run 'sudo apt-get install ubuntu-desktop' and you have it all.  (The you can go back and remove Open Office, and the like)

---

### Post by kc5hwb on 2007-03-31
I like the GUI and like to run X remotely as well.  What do you use to rum remotely?  VNC?

And what is LAMP, I saw this option, but wasn't sure what it was.

---

### Post by arron on 2007-03-31
If it is a headless server, you will thank yourself to run it with no x and learn the bash prompt. The prompt is more powerful than any gui once you learn it, and then you can easily work on it from anywhere via ssh.

I run a headless one, with no gui or x, all remote ssh login to a prompt.  Saves hd space and system resources.

---

### Post by arron on 2007-03-31
Oh yes...
L inux
A pache
M ySql
P hp or Pearl or Python.

---

### Post by kc5hwb on 2007-03-31
Bash Prompt is a new one to me, never heard that term before.

Won't SSH work other ways as well?  I thought that I had read somewhere that you could SSH into a Desktop ver of U, so I assumed that you could also do it with the Server ver.

Sorry for the dumb questions, its just been a while since I have done any of this.

---

### Post by houstonbofh on 2007-04-01
'bash' is a command shell.  But actually, Edgy uses 'dash' which is slightly different.  (Only hurts with Enemy Territory: True Combat : Elite where dash crashes the install)  These are all just cli environments.  They are powerful, and utterly non-intuitive.

SSH is a encryption tunnel to a cli.  However, it can also tunnel file transfer, and X windows.  'ssh myserver.home.net -X -l username' will allow me to run windowing apps, like nautilus, from remote.

VNC is a remote desktop application.  It is built into the Ubuntu desktop.  It is the whole desktop.  It is slower, but good for remote user instruction.

As to X on a server...  There are several versions.  Ubuntu is Gnome.  Heaviest, it also has the Ubuntu approved upgrade method built in.  KDE is lighter.  And when Edgy came out, many of them had upgrade nightmares.  Xubuntu is lightest of all.  The performance difference to a modern server with moder hardware is minimal.  I am running full Ubuntu distributions on P4 650s with 256 meg of ram.  I say use the tool you need, and shun none of them.

---

### Post by kc5hwb on 2007-04-01
VNC I have used before, as well as RDP on Windows.

I think I want to try SSH with Putty or some other app to see how I like that.

Webmin is good because, at my work, they turn off RDP and VNC ports, so my options are limited.  Webmin on port 8080, I could do.

---

### Post by kc5hwb on 2007-04-01
ok, I got the server OS installed, the desktop installed, and everything seems to be working fine.

The desktop that installed doesn't have the Synaptic Pkg Mgr.  So I am not sure where to go to install SSH Server and/or Webmin.

I don't plan to run this server on the Open Internet, just on my LAN, so security isn't an issue.

I need to find out how to format, installed SAMBA, and share 2 SATA drives that I have in this machine.  I have formatted drives before, but not SATA drives.  And I have installed SAMBA before, but not with this GUI since it seems a bit different from the regular Desktop GUI.

---

### Post by houstonbofh on 2007-04-01
What gui did you choose?  That would help us help you.  And 'apt' is what Syn'apt'ic is a front end for.  Read up on apt, and apt-get to load everything.  Sorry, but without Synaptic it is cli time.

---

### Post by kc5hwb on 2007-04-01
Actually, after a reboot, several things showed up, including Synaptic.  So we are good there.  I was also able to get SAMBA installed and working.  Right now I am messing with VNC.

My next hurtle that I don't know how to tackle is the 2-SATA drives.  They are showing up under /dev/sda1 and /dev/sdb1 because Ubuntu sees them as SCSI (I am told).  But I can't figure out how to mount them.  The option for "disks" under System-> isn't showing in this install, so I can't go here and mount the disks, and when I go to Places->Computer, these disks do not show in this view at all.

---

### Post by houstonbofh on 2007-04-02
sudo apt-get instal gparted

You have to partition and format before you mount.

---

### Post by kc5hwb on 2007-04-02
Thanks, partitioning and formatting I have done before.

---

### Post by kc5hwb on 2007-04-02
I got Gparted, found the disks, partitioned them and formatted to ext3.  But they still aren't showing in my Places->Computer view and I still don't have the System->Administration->Disks menu either.  How do I find these disks so that I can mount them and share them with Samba?

---

