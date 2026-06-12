---
title: "Cannot run Synaptic?!?!"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-04-26
Hi.
When i try to run Synaptic i get the following error message:
"The package virtualbox needs reinstalling, but I cannot find any archive for it." (translated from swedish)

---

### Post by igknighted on 2007-04-26
> **the_axiom said:**
> Hi.
When i try to run Synaptic i get the following error message:
"The package virtualbox needs reinstalling, but I cannot find any archive for it." (translated from swedish)

try "sudo apt-get -f install".  If that doesn't work, try "sudo dpkg --configure -a".  Failing both of these, run "sudo apt-get remove virtualbox && sudo apt-get install virtualbox", but be ware you might lose all your VM's.

---

### Post by earobinson on 2007-04-26
you should be able to click edit->fix broken packages and synaptic will fix the packages after you click apply

---

### Post by the_axiom on 2007-04-26
sudo apt-get -f install
sudo dpkg --configure -a
I did follow both of them, none of them worked.
I didnt want to try your other commands before I know what a WM is?

earobinson:
where do I click edit? Synaptic closes directly after the errormessage is closed...

---

### Post by az on 2007-04-26
Try
sudo dpkg -r virtualbox

If that does not work, try downloading the virtualbox deb again and re-install it.  It may be that the removal scripts were not installed when it's installation was interrupted...

---

### Post by igknighted on 2007-04-26
> **the_axiom said:**
> sudo apt-get -f install
sudo dpkg --configure -a
I did follow both of them, none of them worked.
I didnt want to try your other commands before I know what a WM is?

earobinson:
where do I click edit? Synaptic closes directly after the errormessage is closed...

A virtual machine (VM) is an OS you have running in virtualbox.

Use az's fix, as I was unaware virtualbox wasn't in the repo's.

---

### Post by the_axiom on 2007-04-26
ok i've tried all your commands now, none of them worked.
I'm new to **_Ubuntu_**, with other words I don't know how to download the deb file.

---

### Post by the_axiom on 2007-04-26
found it at last but I get an error (when I run VirtualBox_1.3.8_Ubuntu_feisty_i386.deb):
The package could be broken or you are not allowed to open the file. Check ther rights on the file. (translated from swedish)

---

### Post by the_axiom on 2007-04-26
c'mon guys there must be anything I could do?

---

### Post by the_axiom on 2007-04-26
how do I uninstall this crap manually?

---

### Post by the_axiom on 2007-04-26
Please tell me what to do? I need to install VLC to watch a movie with friends. C'mon anyone gotta know...

---

### Post by Seisen on 2007-04-26
Follow the steps in comment #9 and see if that fixes the problem.
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html")

---

### Post by Campingman on 2007-04-26
Have you seen these threads, looks like a tricky one
[http://ubuntuforums.org/showthread.php?t=413847&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=413847&highlight=virtualbox)
[http://ubuntuforums.org/showthread.php?t=421933&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=421933&highlight=virtualbox)

May have some additional info

---

### Post by the_axiom on 2007-04-27
> Edit /etc/init.d/virtualbox and change line 129 from &#8216;exit 1&#8242; to &#8216;exit 0&#8242;

Reinstall the virtualbox package by &#8216;dpkg -i &#8216;. An installation failure of this package is expected.

Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from &#8216;exit 1&#8242; to &#8216;exit 0&#8242;

Execute &#8216;dpkg --configure --pending&#8216;
i didnt find virtualbox in "/etc/init.d" (manually).
Please help me, ubuntu is much or less useless without beeing able to install anything.

---

### Post by the_axiom on 2007-04-27
is the only way to reinstall?

---

### Post by az on 2007-04-27
> **the_axiom said:**
> found it at last but I get an error (when I run VirtualBox_1.3.8_Ubuntu_feisty_i386.deb):
The package could be broken or you are not allowed to open the file. Check ther rights on the file. (translated from swedish)

What do you mean run it?

In a terminal, cd to the directory where that file is and run

sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb

Then remove it.

---

### Post by the_axiom on 2007-04-27
[IMG]http://i12.tinypic.com/42ljgg0.jpg[/IMG]
What am I supposed to do now?

---

### Post by az on 2007-04-27
If hitting enter does not work, try hitting TAB so that the OK becomes selected, then press enter.

---

### Post by the_axiom on 2007-04-27
I solved it all by typing
sudo dpkg --remove --force-remove-reinstreq virtualbox
in terminal.

---

### Post by mtwalther on 2007-04-27
get out of the X window manager, ctl alt f1, type in..
wget [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb)

after it installs
type

sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb within the directory you installed it

should solve your problem, it happend to me last night and I fixed it doing this, I think

---

