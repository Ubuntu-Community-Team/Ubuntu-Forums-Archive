---
title: "Need help installing Adobe Reader"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by kaidenet on 2007-11-15
I have downloaded an adobe Reader 8.1.1 reader installer file in a .tar.gz format. I have extracted it onto my desktop and when I opened up the installer file using the terminal, it asks me the following:

This installation requires 117MB of free disk space. 

Enter installation directory for Adobe Reader 8.1.1 [/opt] 




I tried to type /opt/adobe and pressed enter, I get the message:

Directory "/opt/adobe" does not exist.

Do you want to create it now? [y]

I typed y and enter

I get the message:

mkdir: cannot create directory '/opt/adobe' : Permission Denied
ERROR: Cannot make directory "/opt/adobe".

How do I install my Adobe Reader?

---

### Post by metroplex on 2007-11-15
You need super user (root) privileges to create files and directories in /. Use "sudo" to temporarily get root access.
Look at the manuals for "sudo" or "su" to learn more about what they do.

man sudo
or
man su

---

### Post by hyper_ch on 2007-11-15
Acro 8 is in the medibuntu repos:  [http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by Inxsible on 2007-11-15
Use this link to add the medibuntu repos to your sources

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Mze on 2007-11-15
Or use this method off the Ubuntu Guide [Adobe Reader Gutsy amd64/i386]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Adobe_Reader_Gutsy_amd64.2Fi386")

I'm assuming you're using Gutsy (Ubuntu 7.10)

---

### Post by por100pre1 on 2007-11-15
> **kaidenet said:**
> I have downloaded an adobe Reader 8.1.1 reader installer file in a .tar.gz format. I have extracted it onto my desktop and when I opened up the installer file using the terminal, it asks me the following:

This installation requires 117MB of free disk space. 

Enter installation directory for Adobe Reader 8.1.1 [/opt] 




I tried to type /opt/adobe and pressed enter, I get the message:

Directory "/opt/adobe" does not exist.

Do you want to create it now? [y]

I typed y and enter

I get the message:

mkdir: cannot create directory '/opt/adobe' : Permission Denied
ERROR: Cannot make directory "/opt/adobe".

How do I install my Adobe Reader?

Add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and then do this in terminal:

```
sudo apt-get install acroread
```

---

### Post by rsambuca on 2007-11-15
You can also just download the .deb file instead, which installs it for you with a simple mouse click.  [You can get it here]("http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.1/enu/AdobeReader_enu-8.1.1-1.i386.deb").

---

### Post by stchman on 2007-11-15
> **hyper_ch said:**
> Acro 8 is in the medibuntu repos:  [http://www.medibuntu.org](http://www.medibuntu.org)

I run Feisty and all I get from Medibuntu in Acrobat 7.  To get Acrobat 8 do you need to have Gutsy?

---

### Post by kaidenet on 2007-11-16
> **rsambuca said:**
> You can also just download the .deb file instead, which installs it for you with a simple mouse click.  [You can get it here]("http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.1/enu/AdobeReader_enu-8.1.1-1.i386.deb").

I tried to open the .deb installer file. When the file was fully downloaded, the installer loaded up and immediately gave me this message:

**Software index is broken**

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

What should I do now?

---

### Post by SunnyRabbiera on 2007-11-16
you can try to install automatix.
or you can get it off of mediabuntu too [here]("http://www.medibuntu.org/packages.php")

by the way you do know that ubuntu does have its own PDF reader right?
its called envince, its under "graphics" listed as "doccument viewer"

---

### Post by rsambuca on 2007-11-16
You need to enter a terminal and enter```
sudo apt-get install -f
```

---

### Post by SunnyRabbiera on 2007-11-16
honestly the terminal can be avoided for this...

---

### Post by rsambuca on 2007-11-16
> **SunnyRabbiera said:**
> honestly the terminal can be avoided for this...

No it can't.  If you actually read the Op's last post, it indicates the Software index is broken.  > Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
In fact, if this isn't corrected, the Op will be unable to install any software, let alone acroread.

---

### Post by kaidenet on 2007-11-16
> **SunnyRabbiera said:**
> you can try to install automatix.
or you can get it off of mediabuntu too [here]("http://www.medibuntu.org/packages.php")

by the way you do know that ubuntu does have its own PDF reader right?
its called envince, its under "graphics" listed as "doccument viewer"

I tried to install it, but I cannot find automatix in the website listed.

---

### Post by AlexenderReez on 2007-11-16
> **stchman said:**
> I run Feisty and all I get from Medibuntu in Acrobat 7.  To get Acrobat 8 do you need to have Gutsy?
no..you don't need....take feisty repo medibuntu list....

for gutsy -->


ok...i will explain....open terminal.... it is under application --> accessories -->terminal

enter 

> sudo apt-get install -f 
enter password and hit enter again....

that is to correct your system...

in terminal..enter....

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

> sudo apt-get install acroread 

---

