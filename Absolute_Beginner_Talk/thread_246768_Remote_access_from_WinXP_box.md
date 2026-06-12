---
title: "Remote access from WinXP box?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by vincedia on 2006-08-29
I have found a lot of technical articles on remote access to my 6.06 Ubuntu box. I even found a nice basic how-to on an older version of Ubuntu.

Well I am new to Linux, and I can't find anything on how to set up a remote graphical access session to Ubuntu 6.06. I'm pretty much clueless on SSH and if it is even possible to get a graphical connection using that. I do not know how to use a terminal except to paste some commands I've copied from this forum so far. Hence the need for the graphical part. So a basic overview of SSH might also help.

I'm just looking to be able to transfer some files between my XP PC and Linus Ubuntu box. The XP pc being at work and the Linux box at home. I would alo like to be able to complete tasks from my work PC on my home PC. (certian downloads seem to take hours and require multiple inputs of SU password.

Thanks in advance!
Vince

---

### Post by mejy on 2006-08-29
> **vincedia said:**
> I have found a lot of technical articles on remote access to my 6.06 Ubuntu box. I even found a nice basic how-to on an older version of Ubuntu.

Well I am new to Linux, and I can't find anything on how to set up a remote graphical access session to Ubuntu 6.06. I'm pretty much clueless on SSH and if it is even possible to get a graphical connection using that. I do not know how to use a terminal except to paste some commands I've copied from this forum so far. Hence the need for the graphical part. So a basic overview of SSH might also help.

I'm just looking to be able to transfer some files between my XP PC and Linus Ubuntu box. The XP pc being at work and the Linux box at home. I would alo like to be able to complete tasks from my work PC on my home PC. (certian downloads seem to take hours and require multiple inputs of SU password.

Thanks in advance!
Vince

SSH is essentially a way to login to a remot compurter, and then execute commands on that computer.  It's like your using the terminal on the other computer, but you can do it remotely.  For example, I can login to one linux box from another and use cp to copy files around on that computer, or use 'top' to see what processes are running.

If you want to login using a GUI, you can use the remote desktop feature built into Windows XP Pro and most other professional/server versions, and then use the Terminal Server Client included in Ubuntu to access the XP box.  If it's not enabled by default, use the menu editor to enable it in the internet section.

To access the Ubuntu computer from a Windows desktop, enable remote desktop sharing from System->Preferences->Remote Desktop, and use a VNC Viewer on the XP Machine.  You'll have to google to find a good free VNC viewer for XP, since I've never had to use one myself.

Your biggest problem to sort the rest out will be configuring the firewalls at either end andsorting out IP address issues.  For most stuff at the work end, you may well need to get your system admin to set some of the stuff up (unless you have the privelages to do it yourself).

Hope this helps.

---

### Post by vincedia on 2006-08-29
That does help, thank you!

It is my office, and I use almost the exact same equipment from the office that I do from home. Setting up the ports and IP addys should be no problem.

So just enabeling the remote desktop and adding VNC to the win box is all that I need to do? I didn't think it would be that simple.

Thank you, I will be trying that tonight :)

Vince

---

### Post by atomkarinca on 2006-08-29
as far as i know file transfer is not possible via only vnc. you should install vnc file server for that. or [winscp]("http://winscp.net") would do the trick. it's basically an ftp-like program that lets you transfer files. you don't have to struggle with vnc.

---

### Post by msak007 on 2006-08-29
If you're looking for a good VNC client, I would suggest [UltraVnc]("http://ultravnc.sourceforge.net/") - has a ton of features (including file transfer) and though it can only be installed on Windows, it can connect to *nix machines (which is what you're trying to do). RealVNC also has file transfer, but they make you pay for the versions that include it. As far as being able to connect to your computer remotely, set up an account at [DynDNS.org]("http://www.dyndns.com/") (it's free if you choose a dynamic IP) and then install an app such as **ddclient** (it's in the repos) to update your IP on their host automatically everytime your IP changes.

---

### Post by snakyjake on 2006-08-30
Take a look at tightvncserver for your Linux box.  It will allow you to login into your Linux box without first having to be logged into the box.  I don't have good configuration instructions available, and would be great if someone could share them.

Then on your Windows box, use VNC Viewer or TightVNC.  FreeNX is a better solution (faster, secure, a bit better on client configuration).

Jake

---

### Post by zhenya on 2006-09-03
I'll second the reccommendation for FreeNX.  It's ultimately easier to configure than VNC over SSH, and much faster.  It also supports file sharing between the host and the client.  

For strict file access on your ubuntu machine, try winscp.  This gives you a windows-explorer like interface to copy files between two machines.  You will need to forward port 22 (ssh) on your home router to your ubuntu machine's ip address (which should be fixed, not dynamic.)  If you do not have a static ip address from your ISP you should also register with dyndns.org or similar so you don't lose access when your ip changes.

---

