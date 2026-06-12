---
title: "Could not mount a shared folder"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by dtzxdtzx on 2007-03-01
Hi, All,

I have posted this question in wireless and networking section, since I did not get any response, I reposted here and hope someone coulde help me.

Since I heard that ubuntu is better than suse because it requires less hardware resource. I installed it in vmware server and want to try it.

However, I have encountered a problem to mount the host shared folder. My host is Window XP and the shared folder is C drive. In suse 10.0, I typed
mount -t cifs -o username="domain/username" -o uid="1000" //192.168.187.1/hostC ~frank/hostC

after typed in password, it works. I can read and write in hostC directory. 
The same command in ubuntu in su user mode, I got
mount: block device //192.168.187.1/hostC is write-protected, mounting read-only
mount: cannot mount block device //192.168.187.1/hostC read-only.

Note that ubuntu even did not ask password.

I have the full control of the shared hostC.

Does anyone know why it does not work in ubuntu?

Thanks

Frank

---

### Post by benfindlay on 2007-03-01
Ok, first things first. Ubuntu comes only with samba client installed. You need to set the server up yourself. Best way to do that is to follow this guide: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

As the link above shows, once samba is up and running, you need to set your desired user's password, then activate it so that he/she can access your shares. If SuSE worke anything like Debian, its pre-done for you!

However, it only takes about 2 minutes to get your shares working with ubuntu if you follow the guide above!

Hope this helps!

---

### Post by dtzxdtzx on 2007-03-01
Thanks for your help.

However, I do not know why I need to run samba server and the command 
sudo apt-get install samba

will generate a error message said that samba package is not available.

My problem is that I am running ubuntu as guest os in vmware server. The host is winxp. I have shared the winxp C drive. 

In fedora 5, I can mount the C drive. However, in ubuntu I could not.

After googling, it seems that ubuntu 6.10 is a good linux distribution. However, if I could not resolve this problem, I have to switch back to fedora.


Frank

---

