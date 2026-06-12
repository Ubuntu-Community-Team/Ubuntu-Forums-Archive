---
title: "installing a local webserver"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by walterwill on 2007-07-13
I turned my p3 laptop into a linux operating system to create a webserver and selected ubuntu and xampp for it. However, the unpacking did not work. Is it because xampp doesn't support ubuntu (it works with red hat, suse, mandrake and debian) or is the manual accompaning the installation cd giving me wrong command lines or syntax errors?) 

host@host-laptop:~$ su
Password: 
root@host-laptop:/home/host# mkdir /opt
root@host-laptop:/home/host# foo@bar:~ sudo cp xampp-linux-1.6.2.tar.gz /opt
bash: foo@bar:~: command not found

How can i solve this problem? is there a way to use the gui instead of typing lines as i'm not reallz good at that.

---

### Post by phr0ze on 2007-07-13
Why are your typing foo@bar and you don't need sudo if you already used the unrecommended su command.

This should be what you type.
cp xampp-linux-1.6.2.tar.gz /opt

However, this isn't doing much to install it. It just copies the package.

---

### Post by tunginobi on 2007-07-13
For the last command, just type:

sudo cp xampp-linux-1.6.2.tar.gz /opt

The stuff you typed in front before that is just a sample prompt which is displayed on the terminal. It differs between installations, and you're not meant to type it.

---

### Post by walterwill on 2007-07-13
Thx for the replies, but none of the lines seem to work:

host@host-laptop:~$ su
Password: 
root@host-laptop:/home/host# mkdir /opt
mkdir: cannot create directory `/opt': File exists
root@host-laptop:/home/host# cp xampp-linux-1.6.2.tar.gz /opt
cp: cannot stat `xampp-linux-1.6.2.tar.gz': No such file or directory
root@host-laptop:/home/host# sudo cp xampp-linux-1.6.2.tar.gz /opt
cp: cannot stat `xampp-linux-1.6.2.tar.gz': No such file or directory


first i have to copy the file to opt and then unpack it in there, maybe i'm moving too fast?

---

### Post by hyper_ch on 2007-07-13
Either have a look here:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) (Section 1.22) or here [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) or if you you want a more advanced setup: [http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3)

---

### Post by walterwill on 2007-07-13
Thanks but i'm the worst manual reader. I prefer ad hoc solutions. Now after some solely brainstorming I found out the xampp file sat in the wrong directory, so I pasted it where it belonged and started over again, This is what I got:

host@host-laptop:~$ su
Password: 
root@host-laptop:/home/host# sudo cp xampp-linux-1.6.2.tar.gz /opt
root@host-laptop:/home/host# cd /opt
root@host-laptop:/opt# sudo chmod -R a+rw /opt/lampp/htdocs
root@host-laptop:/opt# /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.2...
XAMPP: XAMPP-Apache is already running.
XAMPP: Starting MySQL...
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
root@host-laptop:/opt# 

Then I went to [http://localhost](http://localhost) and there it was, proudly showing the Xampp logo. So that step has been taken and now off to php. I thank everyone who paid attention to my struggle. If I experience some more, I'll keep you informed.

---

