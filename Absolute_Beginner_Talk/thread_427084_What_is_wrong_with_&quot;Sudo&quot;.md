---
title: "What is wrong with &quot;Sudo?&quot;"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-04-29
I'm pretty new to Linux and I've been busy making ubuntu my own :). I've come across a bunch of websites helping me set-up Beryl, Kaffiene, and the like and often used Terminal and the command "sudo" (With MANY MANY MANY trials and errors). I was reading around in the forums and some users were saying that you shouldn't run around using that command very often. Why is that? Am I at a risk now because I followed instructions from forums and what not. I've added items to the source.list and many keys and I just want to make sure my computer is safe. Thanks!!

---

### Post by DrPppr242 on 2007-04-29
I'm prettey new to this to but sudo does whatever commands follow as root or the super user so if you use sudo all the time you can mess up your machine pretty fast if you don't know what you're doing it also will set permissions to root, for instance if you unpack a .tar.gz file with sudo tar xzvf instead of just tar xzvf only root will have access and it can be a pain to delete move or use the files

---

### Post by Najand on 2007-04-29
There is no problem using "sudo". The matter is that you should understand what you are doing. "sudo" can overwrite/ remove/ move some part of your system configuration or some important files related to your system. So you should be very careful. However if you don't use "sudo" you cannot install/set up new packages or customize your system or change the settings of your ubuntu. The only advice I can give you is that, before using a command starting with "sudo", try to know what does it do. I will help you to learn more about linux and also it can prevent troubles later.

---

### Post by isaacj87 on 2007-04-29
hmmm...i see but does it pose and security threats? such as compromised data or identity theiving?? Obviously I'm a former Windows user...

---

### Post by Malta paul on 2007-04-29
Hi,
You might like to check-out [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)      "File Permissions" :)

---

### Post by Najand on 2007-04-29
Well, most of spywares/visurs are built for windows. So they are not usually a seroius treath for linux. We have our firewall and security solutions for linux too. However this doesn't mean you can install any unknown package (especially from the internet). So if you are careful, be sure there wouldn't be any problem.

---

### Post by isaacj87 on 2007-04-29
I'm sorry if this has been covered, but is Ubuntu safe for sending sensitive data? For example, I have to finish a college transfer application online and it would require me putting data such as my SSN. Is Firefox/Ubuntu safe enough for that? I'm sorry I'm not very security savvy.

---

### Post by Sef on 2007-05-02
> I'm sorry if this has been covered, but is Ubuntu safe for sending sensitive data? For example, I have to finish a college transfer application online and it would require me putting data such as my SSN. Is Firefox/Ubuntu safe enough for that? I'm sorry I'm not very security savvy.

Yes, Firefox/Ubuntu is safer than sending it via I.E/Windows.   The transfer itself is very safe.   The problem is how the security is set up where it is stored on the computers.  Sending it by mail won't resolve that problem as the data on the form would be inputted on a computer.

---

