---
title: "i need a basic guide on using terminal and programming for ubuntu can anybody help"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by EnGorDiaz on 2007-07-03
im sick of asking questions i need a basic guide but my last question is 

im trying to install a package called avira its a TAR.GZ i need to know how install it. i extracted it 

i then used the terminal and typed cd, to the bin folder.  there is an install inside the main folder called install when i activate it it says there needs to be a root. can anyone help 

me install avira antivir.TAR.GZ 

and also can someone help me with the guide, i have searched on google but i need to be more specific.

---

### Post by KIAaze on 2007-07-03
Guides on using the terminal:
[http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html")
[http://www.psychocats.net/ubuntu/terminal]("http://www.psychocats.net/ubuntu/terminal")
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

Is there an INSTALL or README file?
If so open them with a text editor for installation info.

Is there an install.sh file?
Then running:
```
sudo install.sh
```
should be enough.

Is there a configure file in the extracted files?
If so, the install method is probably:
```
./configure
make
sudo make install
```

For programming guides, what language do wish to use?
It shouldn't be hard to find guides for programming on google.

---

### Post by EnGorDiaz on 2007-07-03
thanks :)

---

### Post by starcraft.man on 2007-07-03
[How to install software]("http://www.psychocats.net/ubuntu/installingsoftware")
- scroll down to source section for information on installing from the tar (I assume its source).

[Terminal for Beginners]("http://www.linuxcommand.org/")
- Read learning the shell and then other sections.

[Only wiki I know on programming.]("http://laroza.pbwiki.com/")-

Those should cover it. If theres any questions post. If your 

I never installed avira, can't help specifically.

Edit: Darn it, I guess I'm slow tonight...

---

### Post by carloslosgrande on 2007-07-03
Hi EnGorDiaz, you can check the following very useful sites;

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by EnGorDiaz on 2007-07-03
hmmm is this how you do it 


james@james-desktop:~$ cd  /home/james/Desktop/antivir-workstation-pers-2.1.10-15 
james@james-desktop:~/Desktop/antivir-workstation-pers-2.1.10-15$ ./configure
bash: ./configure: No such file or directory
james@james-desktop:~/Desktop/antivir-workstation-pers-2.1.10-15$ make
make: *** No targets specified and no makefile found.  Stop.
james@james-desktop:~/Desktop/antivir-workstation-pers-2.1.10-15$ make install
make: Nothing to be done for `install'.

---

### Post by starcraft.man on 2007-07-03
> **EnGorDiaz said:**
> hmmm is this how you do it 


james@james-desktop:~$ cd  /home/james/Desktop/antivir-workstation-pers-2.1.10-15 
james@james-desktop:~/Desktop/antivir-workstation-pers-2.1.10-15$ ./configure
bash: ./configure: No such file or directory
james@james-desktop:~/Desktop/antivir-workstation-pers-2.1.10-15$ make
make: *** No targets specified and no makefile found.  Stop.
james@james-desktop:~/Desktop/antivir-workstation-pers-2.1.10-15$ make install
make: Nothing to be done for `install'.

Nope sorry, I'm not very good at compiling, one of my weak points. Need more info anyway, can you link to where you got the tar so we can look at it ourselves?

Can I ask why you are installing an Antivirus solution? The only reason to do so IMO, is if you need to scan email attachments for Windows Viruses before forwarding. KlamAV is best for that its in the repos.
[URL="http://www.psychocats.net/ubuntu/security"]
Here is why you don't need an AV.[/URL]

---

### Post by KIAaze on 2007-07-03
> bash: ./configure: No such file or directory
That means the configure script doesn't exist. So it's useless to run the make and make install commands.

Could you post the output of this command please:
```
ls ~/Desktop/antivir-workstation-pers-2.1.10-15
```

edit:
Oh and if you don't want exactly Avira antivirus, there's another antivirus for Ubuntu, which is very easy to install: ClamAV

Just type:
> sudo apt-get install clamav

This can also be done through "applications->add/remove programs" or "system->administration->synaptic package manager" in the menus. Just search for the clamav package.

---

### Post by silent1643 on 2007-07-03
i found this one useful myself
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by starcraft.man on 2007-07-03
> **KIAaze said:**
> That means the configure script doesn't exist. So it's useless to run the make and make install commands.

Could you post the output of this command please:
```
ls ~/Desktop/antivir-workstation-pers-2.1.10-15
```

edit:
Oh and if you don't want exactly Avira antivirus, there's another antivirus for Ubuntu, which is very easy to install: ClamAV

Just type:


This can also be done through "applications->add/remove programs" or "system->administration->synaptic package manager" in the menus. Just search for the clamav package.

Don't forget about the GUI front end, most people don't like the commands only (thats all you get with clam right?)

```
sudo aptitude install klamav
```

That will install the front end after :).

---

### Post by Raineer on 2007-07-03
the link in my sig has a growing terminal guide, I just finished the section on extracting tars and installing from scripts today.

---

### Post by KIAaze on 2007-07-03
> Don't forget about the GUI front end, most people don't like the commands only (thats all you get with clam right?)

Yep, I was just searching for it but didn't remember its name and it wasn't listed when searching for clamav on packages.ubuntu.com.

In the end, I found more than what I was looking for:
[http://wiki.clamav.net/Main/ClamGUI]("http://wiki.clamav.net/Main/ClamGUI")
As always, there's a lot of choice in the Free world. :)

---

### Post by starcraft.man on 2007-07-03
> **KIAaze said:**
> Yep, I was just searching for it but didn't remember its name and it wasn't listed when searching for clamav on packages.ubuntu.com.

In the end, I found more than what I was looking for:
[http://wiki.clamav.net/Main/ClamGUI]("http://wiki.clamav.net/Main/ClamGUI")
As always, there's a lot of choice in the Free world. :)

Indeed :)

---

