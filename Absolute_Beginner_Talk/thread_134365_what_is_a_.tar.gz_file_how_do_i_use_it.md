---
title: "what is a .tar.gz file? how do i use it?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by candide on 2006-02-21
extremely beginner question:

I have downloaded some apps i want to install.  They are on my desktop in ubuntu. They are in .tar.gz form. what do i need to do to install these applications?

:-k

---

### Post by senning on 2006-02-21
Hi Candide,
tar files are a compression format, like zip files.  They generally contain the sourcecode for programs.  Unless you feel comfortable trying to compile a program, you should probably try to find the program on Synaptic (in GNOME, System->Administration->Synaptic Package Manager) or Adept first.  If you REALLY REALLY want to compile these programs for some reason, let me know and I'll try to help out.

---

### Post by Sandlst on 2006-02-21
look at this [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")
Stolen from aysiu's sig hehe......scroll down to the part about 'installing from source'

I would go with senning on this though...only do this if the package is not avaliable in synaptic.

---

### Post by shade11 on 2006-02-21
tar.gz and .tgz are compressed formats for Linux. I think that it is better to stick with synaptic for now, or automatix. If you cant find the program in synaptic then try to open the file. Sometimes it is a source code. Sometimes it isn't. You can tell if it has a file called configure in it. If the file is in syanptic and you need to install from source or from the tar.gz just ask.

---

### Post by Zeroangel on 2006-02-21
Right click on the file and select 'extract here'. It will 'unzip' the files for you. 

However, I firstly would enable my universe and multiverse repositories if I were you, and see if these applications you need are available via that.

Failing that, we will need to do a few things:

For files that are already compiled in the .deb format it is a simple matter of using dpkg on them (sudo dpkg -i packagename) to install them

If we want to compile a program from source code in Ubuntu it's a little more difficult because Ubuntu is not designed 'out of the box' to do that. You will need to install a package called build-essential (which you can get from the Synaptic Package Manager, or 'sudo apt-get install build-essential')

---

### Post by K-9 on 2006-02-21
just out of curiousity - because i see a lot of commands posted on these forums yet sometimes cannot tell where spaces are used and not:

For files that are already compiled in the .deb format it is a simple matter of using dpkg on them (sudo dpkg -i packagename) to install them



(sudo dpkg -i packagename)****  there is a space between dpkg and -i yes?  becasue when people post stuff and it continues over to the next line or there are other text words included in the description it is a bit confusing... and as a total beginner, I was asking. Thanks - K-9

---

### Post by senning on 2006-02-21
K-9: Yes.  *sudo dpkg -i packagename*.  Though in a few months, when Dapper comes along, you should just be able to right click on [I].deb[/]s and have an entry for 'install'

---

### Post by speedsix on 2006-02-22
Can I ask a related question, say you want to get the latest version of a piece of software that *is* in synaptic by downloading the source .tar.gz. You will obviously want to remove the original older version from synaptic but then it will want to remove other apps that depend on this which you may want to keep. Can you get these to reference your new version and keep them?

If that makes sense.

Thanks

---

### Post by Zeroangel on 2006-02-22
I think you can do that by using the 'apt-get update' command.

---

### Post by dvarsam on 2006-02-22
[QUOTE=senning] ...in a few months, when Dapper comes along, you should just be able to right click on [I].deb[/]s and have an entry for 'install'[/QUOTE]

My God, I am getting so Excited about the "Dapper" Edition coming up....

Can you please tell us more:

How is it going to work?
What is New?

I'm getting so excited, PLEASE tell me more, \\:D/ 

where can I read stuff about it?:p 


Thanks

---

