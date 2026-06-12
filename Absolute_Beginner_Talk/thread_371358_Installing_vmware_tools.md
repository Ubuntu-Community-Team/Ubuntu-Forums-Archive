---
title: "Installing vmware tools"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-02-26
hey guys, im new to the linux and Ubuntu scene. I just installed it for the first time yesterday on a virtual machine (which was also the first day of installing and using a virtual machine). anyway, i may become somewhat of another linux convert as i really like it so far. i have taken a short class on linux before but i hardly remember a thing. so im going to experience the whole thing myself on my home computer finally.

anyways, im having a problem installing vmware tools in Ubuntu. i ran the installation in the terminal and it seemed to install fine but after that i need to configure it which isnt working quite as well. it goes through all of its stuff and eventually says something about not having a something suitable for the kernal and would i like it to make a suitable one for me. so i proceed and it works away and then it says there was an error extracting something 7.org i think. i dont quite remember. but then it just aborts. so thats my only complaint so far. any suggestions?

---

### Post by Maestro23 on 2007-02-26
This guide might help: [https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

---

### Post by uknowho008 on 2007-02-26
awesome thanks. i dont know how i missed it. we'll see how it goes.

---

### Post by Maestro23 on 2007-02-26
> **uknowho008 said:**
> awesome thanks. i dont know how i missed it. we'll see how it goes.

No prob man.  Good luck.

---

### Post by uknowho008 on 2007-02-26
after patching the config file it says there is a syntax error near elseif on line 4491

i would try and figure it out myself but i dont know how to get to line 4491 and im certainly not counting. haha. so whats up with that?

---

### Post by Maestro23 on 2007-02-26
> **uknowho008 said:**
> after patching the config file it says there is a syntax error near elseif on line 4491

i would try and figure it out myself but i dont know how to get to line 4491 and im certainly not counting. haha. so whats up with that?

Don't know man.  Never used Vmware myself, just saw your post and was trying to help you out.:) 

What is the file and in what directory is it located?

---

### Post by uknowho008 on 2007-02-26
it is a configuration file for wmware tools. i downloaded the the patch file from the website and patched the  configuration file which is suposed to get past the x.org 7.0 error i ran into before. but when i run the patched config file it says there is a syntax error. ugh..

the config file is located in user/bin/

its in that link that you gave me under "Workaround: Installing vmware tools"

thanks for all the help

---

### Post by uknowho008 on 2007-02-27
is anybody running ubuntu 6.10 and gotten vmware tools to work? there seems to be an error in the patch.

---

### Post by uknowho008 on 2007-02-27
this forum is pretty active. is there anybody that can help? i want to get vmware tools working so i can transfer files from win xp to the virtual machine and work with it. but im stumped.

---

### Post by Anicka on 2007-02-27
[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)

Try this link. I didn't need any work-around when I installed in VMware, so maybe it's only with 5.2 (I have 5.5.3). I did something like:

sudo alien --scripts /cdrom/VMwareTools*.rpm
sudo dpkg -i vmwaretools*.deb
sudo vmware-config-tools.pl

Good luck!

---

### Post by uknowho008 on 2007-02-27
how about today? does anybody know how to fix this? my version of ubuntu is 6.10 and this is why im having so much trouble. can anybody help?

---

### Post by uknowho008 on 2007-02-27
oh you have 5.5.3? where can i get the newer version? ill do a search right now.

---

