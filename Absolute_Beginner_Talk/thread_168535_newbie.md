---
title: "newbie"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by benfica on 2006-04-30
I have just installed ubuntu for the first time. Can someone out there tell me how to access the cmd prompt and set up my su password. I installed Ubuntu with VMWARE...

---

### Post by Nequeo on 2006-04-30
[QUOTE=benfica]I have just installed ubuntu for the first time. Can someone out there tell me how to access the cmd prompt and set up my su password. I installed Ubuntu with VMWARE...[/QUOTE]

The command prompt is under Applications--->Accessories

If you're a newbie, it's unlikely that you want to set a su password. Ubuntu locks the root account by default, and tries to force you into using 'sudo'. There's a good explanation of why here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The basic idea is that instead of opening a root terminal, or logging in as root, you just preface any command you need to run with root privages with 'sudo'. Or 'gksudo' if it's a graphical program. 

Cheers,

---

### Post by muep on 2006-04-30
You don't usually use the root account in Ubuntu. It is possible but not encouraged, so it is disabled as default.

Ubuntu uses sudo to get temporary root privileges.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for more information.

---

### Post by x5452 on 2006-04-30
I just read through this but I dont understand the 'why' to it at all.  If the su is disabled, but sudo gives you the same access, what is the point? Im not getting what the difference is, can someone clarify for me please?

---

### Post by Bloch on 2006-04-30
> I just read through this but I dont understand the 'why' to it at all. If the su is disabled, but sudo gives you the same access, what is the point? Im not getting what the difference is, can someone clarify for me please?

su logs you in as "root" (also known as "superuser"). When you are superuser at the terminal you can change and delete system files.

sudo temporarily gives you superuser powers. e.g.
su rm /usr/bin/zip.py
will remove the file /usr/bin/zip.py  (i.e. the file zip.py which is in the directory bin which is in the directory usr)
You will be asked for your root password when you use a sudo command.

Now if you can do everything using sudo you don't need su. You are right, there is no point :-)  Except to avoid typing sudo each time. To login as superuser all you have to do is:
sudo su
(and of course it will request your password)

---

### Post by nalmeth on 2006-05-01
in the terminal you can also just type
sudo -i
to hold priviledges for 15 minutes
Being taught with debian and gentoo, I was a little put off by sudo, but must say I have grown to like it.

---

