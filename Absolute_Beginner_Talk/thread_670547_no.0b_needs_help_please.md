---
title: "no.0b needs help please"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by niko123 on 2008-01-17
I THINK I MUST BE THE STUPIDEST PERSON...OR THE SLOWEST....OR BOTH!!!!

But i just recently bought a laptop....didt really bother to keep it there with vista so i figured.."hey why dont i learn linux"...so fars its awsome...iam enjoying everything that ubunto is offereing at the moment

did my research....went to the samba website and downloaded a file then transfered it to my flashdrive to my laptop with ubunto...then left the file on the desktop and...

ran the command "sudo apt-get install samba" and recived this... 

Reading package lists...Done
Building dependency tree
Reading state information...Done
Package samba is not available, but is referred to by another package. this may mean that the package is missing, has been ovsoleted, or is only available from another source
However the following packages replace it:
   smbclient samba-common
E: package samba has no installation candidate

now what i want to know...is...is samba installed...or am i missing somthing....( what, and how ) and...what does that whole thing mean...i know..im a noob..sorry....but PLEASEEEE help me!

oh not to mention i havent setup a working network yet....

---

### Post by DeusEx on 2008-01-17
"sudo apt-get install samba" attempts to download and install the package samba from the repositories, e.g. the internet. 
This means it doesn't use the file you just downloaded.

the easiest way to install software is using synaptic package manager!

---

### Post by Sinkingships7 on 2008-01-17
or, even simpler, Applications -> Add/Remove Programs

---

### Post by The Cog on 2008-01-17
As DeusEx said, apt-get downloads from the repositories on the internet. If it says no nstall candidate found, you may need to do 
**sudo apt-get update**
to get the latest repository index, then try
**sudo apt-get install samba**
again.

Also look at System->Administration->Synaptic which gives you a GUI front-end to apt-get.

---

### Post by oldos2er on 2008-01-17
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 Also check System, Administration, Software Sources, and see that all repositories are enabled.

---

